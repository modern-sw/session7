# Lab Instructions:


---
## Part 1:

### Installation

- [Docusaurus](https://docusaurus.io/docs/installation) consists of a set of npm packages.
The easiest way to install Docusaurus is to use the create-docusaurus command line tool that helps you scaffold a skeleton Docusaurus website. You can run this command anywhere in a new empty repository or within an existing repository, it will create a new directory containing the scaffolded files.

```sh
npx create-docusaurus@latest my-website classic
```

- When prompted, choose **JavaScript** (use arrow keys to select and press Enter).
   ```
   » - Use arrow-keys. Return to submit.
   >   JavaScript
       TypeScript
   ```
- Change into the project directory and Start the development server:
   ```sh
   cd my-website
   npm start   
   ```

By default, a browser window will open at [`http://localhost:3000`](http://localhost:3000). To stop the server use `ctr + C` (MAC `cmd + C`)



**Project structure**

Assuming you chose the classic template and named your site `my-website`, you will see the following files generated under a new directory `my-website/`:

```bash
my-website
├── blog
│   ├── 2019-05-28-hola.md
│   ├── 2019-05-29-hello-world.md
│   └── 2020-05-30-welcome.md
├── docs
│   ├── doc1.md
│   ├── doc2.md
│   ├── doc3.md
│   └── mdx.md
├── src
│   ├── css
│   │   └── custom.css
│   └── pages
│       ├── styles.module.css
│       └── index.js
├── static
│   └── img
├── docusaurus.config.js
├── package.json
├── README.md
├── sidebars.js
└── yarn.lock
```

**Explanation**

- `/blog/` - Contains the blog Markdown files. You can delete the directory if you've disabled the blog plugin, or you can change its name after setting the `path` option. 
- `/docs/` - Contains the Markdown files for the docs. Customize the order of the docs sidebar in `sidebars.js`. You can delete the directory if you've disabled the docs plugin, or you can change its name after setting the `path` option. 
- `/src/` - Non-documentation files like pages or custom React components. You don't have to strictly put your non-documentation files here, but putting them under a centralized directory makes it easier to specify in case you need to do some sort of linting/processing
  - `/src/pages` - Any JSX/TSX/MDX file within this directory will be converted into a website page.
- `/static/` - Static directory. Any contents inside here will be copied into the root of the final `build` directory
- `/docusaurus.config.js` - A config file containing the site configuration. This is the equivalent of `siteConfig.js` in Docusaurus v1
- `/package.json` - A Docusaurus website is a React app. You can install and use any npm packages you like in them
- `/sidebars.js` - Used by the documentation to specify the order of documents in the sidebar


---
## Part 2: Deploying to GitHub Pages using GitHub Actions


**Step 1: Create a GitHub Repository**

1. Go to [GitHub](https://github.com) and create a new repository for your project.
   - Click the "New" button in the top-right corner of the GitHub dashboard.
   - Name the repository (e.g., `mywebsite`).
   - Make sure the repository is set to **public** and **DO NOT** initialize with a README

**Step 2: Enable GitHub Pages Deployment from GitHub Actions**

1. In your GitHub repository, go to the **Settings** tab.
2. Scroll down to the **Pages** section in the left sidebar.
3. Under **Source**, select **GitHub Actions** to deploy your site via GitHub Actions.


**Step 3: Set Up GitHub Actions Workflow**

1. Inside your project, create the following folder structure:
   ```
   .github/
     └── workflows/
   ```

2. Inside the `workflows` folder, create a new file named `deploy.yml`.

3. Paste the following YAML configuration into the `deploy.yml` file:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main
    # Review gh actions docs if you want to further define triggers, paths, etc
    # https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#on

jobs:
  build:
    name: Build Docusaurus
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0
      - uses: actions/setup-node@v4
        with:
          node-version: 18
          cache: npm

      - name: Install dependencies
        run: npm install --frozen-lockfile
      - name: Build website
        run: npm run build

      - name: Upload Build Artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: build

  deploy:
    name: Deploy to GitHub Pages
    needs: build

    # Grant GITHUB_TOKEN the permissions required to make a Pages deployment
    permissions:
      pages: write # to deploy to Pages
      id-token: write # to verify the deployment originates from an appropriate source

    # Deploy to the github-pages environment
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}

    runs-on: ubuntu-latest
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```


**Step 4: Update `docusaurus.config.js`**

In your `docusaurus.config.js` file, configure the production URL and deployment settings for GitHub Pages. 

Make sure to set the following values:

```javascript
module.exports = {
  // Set the production URL of your site
  url: 'https://username.github.io',  // Replace 'username' with your GitHub username or organization name.

  // Set the /<baseUrl>/ pathname under which your site will be served
  // For GitHub Pages deployment, this is usually '/<projectName>/'
  baseUrl: '/mywebsite/',  // Replace 'mywebsite' with your repository name.

  // GitHub Pages deployment configuration
  organizationName: 'username',  // Replace with your GitHub username or organization.
  projectName: 'mywebsite',      // Replace with your repository name.
};
```

**Step 5: Initialize Your Project as a Git Repository and Push to GitHub**

1. Make the project directory a Git repository by running:

```bash
git init
```

2. Make sure that you have the `.gitignore` file. If it does not exist, create one and exclude the `node_modules` directory from version control:

```
node_modules/
``` 

3. Stage all the changes:

```bash
git add .
```

4. Commit the changes:

```bash
git commit -m  "Add message here"
```

5. Connect your local repository to the GitHub repository by following the steps provided by GitHub. There are three commands as shown in the screenshot below, in the green block diagram. You'll need to copy and paste the commands into your terminal, one at a time:


```bash
git remote add origin <GitHub Repository URL>
git branch -M main
git push -u origin main 
```

> Refresh the GitHub repository page to see your changes.


**Step 6: Check GitHub Actions**

1. After pushing to GitHub, navigate to the **Actions** tab in your GitHub repository.
2. GitHub Actions will automatically trigger the deployment workflow you set up in Step 2.
3. Your site will be built and deployed to GitHub Pages. You should see the progress of the deployment in the Actions tab.

**Step 7: Test Changes and Push Updates**

1. Make any changes or updates to your site (e.g., editing content, updating styles).
2. Once you've made the changes, push them to GitHub using the following commands:
   ```bash
   git add .  # Stages the changes
   git commit -m "Made changes to the site"  # Commits the changes
   git push origin main  # Pushes the updates to the 'main' branch
   ```

3. After pushing the changes, GitHub Actions will automatically rebuild and redeploy your site.
4. Visit your site (e.g., `https://username.github.io/mywebsite`) to confirm the changes are reflected.


**Note:**

Docusaurus is a modern static site generator, meaning the website needs to be built into a directory of static files before it can be hosted on a web server for viewing. In GitHub Actions, the workflow includes instructions 
- to install dependencies using `npm install`
- to generate the static site by running `npm run build` and 
- to deploy to GitHub Pages



---

## Links

- [Deploying to GitHub Pages](https://docusaurus.io/docs/deployment#deploying-to-github-pages)