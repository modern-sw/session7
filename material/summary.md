# Summary


---
## Part 1: Introduction Software documentation

#### Docusaurus

Across all static site generators, [Docusaurus](https://docusaurus.io/) has a unique focus on documentation sites and has many out-of-the-box features. used e.g by [Jest](https://docusaurus.io/showcase)

Other main static site generators : VitePress, MkDocs, Docsify


#### VitePress {#vitepress}

[VitePress](https://vitepress.dev/) has many similarities with Docusaurus - both focus heavily on content-centric websites and provides tailored documentation features out of the box. However, VitePress is powered by Vue, while Docusaurus is powered by React. If you want a Vue-based solution, VitePress would be a decent choice.

### MkDocs {#mkdocs}

[MkDocs](https://www.mkdocs.org/) is a popular Python static site generator with value propositions similar to Docusaurus.

It is a good option if you don't need a single-page application and don't plan to leverage React.

[Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) is a beautiful theme.

### Docsify {#docsify}

[Docsify](https://docsify.js.org/) makes it easy to create a documentation website, but is not a static-site generator and is not SEO friendly.

---

---
## Part 2: GitHub Actions?

**GitHub Actions** is a CI/CD and automation platform integrated directly into GitHub. It allows you to automate workflows for tasks like building, testing, deploying, and more. GitHub Actions enables developers to define custom workflows for their repositories using YAML configuration files, which specify what actions should occur and when.

### Key Features of GitHub Actions:
- **Automated Workflows**: Automate your development workflows by specifying tasks (such as testing or deployment) that should run in response to specific events (like pushing code or opening pull requests).
- **Event-Driven**: Actions are triggered by GitHub events such as pushes, pull requests, releases, etc.
- **Customizable**: You can define multiple jobs in a workflow and run them on different operating systems (Linux, macOS, Windows).
- **CI/CD Integration**: GitHub Actions can be integrated with Continuous Integration (CI) and Continuous Delivery (CD) pipelines.

### How GitHub Actions Relate to CI/CD

**CI (Continuous Integration)** and **CD (Continuous Deployment/Delivery)** are practices that aim to streamline and automate the software development and delivery process. GitHub Actions is often used to implement these practices in a GitHub repository.

- **CI (Continuous Integration)** refers to the practice of automatically testing and integrating code changes into the main branch of the codebase. This helps identify bugs early and ensures that new code does not break the existing system. In GitHub Actions, CI is commonly achieved by setting up workflows that:
  - Run tests whenever code is pushed or a pull request is opened.
  - Build the application to ensure the new code compiles correctly.
  - Run linters and code analysis tools to maintain code quality.

  Example CI tasks in GitHub Actions:
  - Run unit tests.
  - Run integration tests.
  - Lint code.

- **CD (Continuous Delivery/Deployment)** is the practice of automatically deploying your application once it has passed the CI checks. The main difference between **Continuous Delivery** and **Continuous Deployment** is that **Continuous Delivery** requires manual approval for deployment, while **Continuous Deployment** automatically pushes the updates to production once the code is ready.

  Example CD tasks in GitHub Actions:
  - Deploy code to staging after passing tests.
  - Deploy code to production once the tests pass, often automatically.
  - Deploy to services like AWS, Azure, or GitHub Pages.

### How GitHub Actions Supports CI/CD:

1. **CI Workflow**: 
   - On every code change (push or pull request), GitHub Actions can automatically run tests, linters, or any build tasks you've defined in the workflow. This ensures that the code is always in a deployable state and adheres to your quality standards.

2. **CD Workflow**: 
   - Once the code passes all tests and checks, GitHub Actions can trigger a deployment job to deploy the application to a server, cloud platform, or static site hosting service like GitHub Pages or AWS S3.

### Example GitHub Actions Workflow

Here’s an example of a CI/CD workflow for a Node.js project that runs tests and deploys the code to GitHub Pages.

```yaml
name: CI/CD Pipeline

on:
  push:
    branches:
      - main  # Trigger on pushes to the main branch

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '14'

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test

  deploy:
    needs: build  # Ensure the build job runs before deploy
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Deploy to GitHub Pages
        uses: JamesIves/github-pages-deploy-action@v4.1.0
        with:
          branch: gh-pages
          folder: build  # Folder to deploy
```

### How This Relates to CI/CD:
- **CI**: This workflow runs tests (`npm test`) when code is pushed to the `main` branch. It ensures that the code passes tests and is in a deployable state before moving to the next step.
- **CD**: After the build and test jobs are successful, the code is deployed to the `gh-pages` branch using the `github-pages-deploy-action` GitHub Action.

### Summary
GitHub Actions allows you to define custom workflows to automate tasks related to **Continuous Integration (CI)** and **Continuous Deployment (CD)** directly within GitHub. You can run tests, build applications, and deploy them automatically as part of your CI/CD pipeline, ensuring faster and more reliable development and deployment cycles.

---

## Yarn vs npm: A Comparison

Both **Yarn** and **npm** are package managers for JavaScript and Node.js projects. They are used to manage dependencies, install packages, and handle tasks related to the project's development environment. However, there are some differences in how they work, their performance, and additional features. Let’s compare the two:



### 1. **Performance**

- **Yarn**: Yarn was introduced as a faster alternative to npm. It achieves its speed by utilizing a **caching mechanism** that stores previously downloaded packages and uses them for future installations. Yarn also **parallels the installation process**, meaning multiple packages can be installed simultaneously, reducing the time taken for installations.
  
- **npm**: Historically, npm was slower than Yarn due to its sequential nature and lack of efficient caching in earlier versions. However, with the introduction of npm 5 and later versions, npm has improved considerably in terms of performance. npm now has a **lock file** and **caching** to improve the speed, but Yarn still tends to outperform npm in certain scenarios.

### 2. **Lock Files**

- **Yarn**: Yarn introduced the concept of the **`yarn.lock` file**. This lock file ensures that the same package versions are installed across all environments (team members, CI/CD pipelines, etc.). The `yarn.lock` file records the exact version of dependencies and their sub-dependencies.

- **npm**: npm introduced its own lock file, called **`package-lock.json`**, in npm version 5. The `package-lock.json` file is similar to Yarn's lock file in that it also ensures consistent dependency versions across different environments.

### 3. **Dependency Management**

- **Yarn**: Yarn installs dependencies by checking the **`yarn.lock`** file and resolves them accordingly. It also installs all dependencies in a **deterministic order**, which ensures that the same package versions are installed every time.

- **npm**: npm also uses **`package-lock.json`** for deterministic installs (from npm 5 onwards), meaning it ensures the same version of dependencies is installed across different environments. However, npm installs dependencies sequentially, whereas Yarn installs them in parallel, making Yarn faster in this regard.


### 4. **Offline Support**

- **Yarn**: One of Yarn’s strengths is **offline support**. If you’ve already installed a package once, Yarn caches it locally. This means you can install the same package or any of its dependencies later without an internet connection. This feature is useful when working in environments with limited connectivity.

- **npm**: npm does have caching mechanisms as well, but it doesn’t offer the same robust offline support that Yarn does. npm's caching is more about speeding up installations, while Yarn’s caching allows for full offline dependency installation.


### 5. **Workspaces**

- **Yarn**: Yarn has built-in support for **monorepos** through its **workspaces** feature. This allows you to manage multiple packages within a single repository. Workspaces make it easier to manage shared dependencies across different packages and maintain consistency.

- **npm**: Starting from **npm 7**, npm introduced native support for **workspaces** as well. Although npm's workspaces feature is newer than Yarn's, it is now quite competitive. However, Yarn’s workspaces are still considered more mature and battle-tested.

### 6. **Security**

- **Yarn**: Yarn uses **checksum verification** to ensure the integrity of packages during installation. When a package is downloaded, Yarn checks that the downloaded package matches its hash, which reduces the chances of installing tampered packages.

- **npm**: npm also has security measures in place. With npm 7+, the **`npm audit`** command can be used to scan for vulnerabilities in your dependencies. npm 7 also introduced support for automatic fixes for security issues.


### 7. **CLI Commands**

- **Yarn**:
  - Install dependencies: `yarn install` (instead of `npm install`)
  - Add a package: `yarn add <package>`
  - Remove a package: `yarn remove <package>`
  - Run scripts: `yarn run <script>`
  
- **npm**:
  - Install dependencies: `npm install`
  - Add a package: `npm install <package> --save` or `npm install <package>` (with npm 5+)
  - Remove a package: `npm uninstall <package>`
  - Run scripts: `npm run <script>`

In terms of basic functionality, the commands are quite similar, but Yarn’s commands can often be shorter due to its fewer options for adding or removing dependencies (e.g., `yarn add` instead of `npm install`).


### 8. **Community and Ecosystem**

- **Yarn**: Yarn is widely used in the community, especially in larger projects and companies that prioritize speed and deterministic builds. It has gained a solid following due to its early focus on performance and features like offline support.

- **npm**: npm, being the default package manager for Node.js, has the largest community and ecosystem. It is the go-to package manager for most Node.js projects and is deeply integrated into the Node.js environment.


### 9. **Compatibility**

- **Yarn**: Yarn is fully compatible with npm and can work with `package.json` files created by npm. It can install dependencies listed in `package.json` and respect both `yarn.lock` and `package-lock.json` files.

- **npm**: npm works seamlessly with Yarn projects, and you can switch between npm and Yarn without issues. However, it’s important to choose one tool and stick with it for a given project to avoid conflicts between the lock files.


### 10. **Popularity**

- **Yarn**: Yarn was initially more popular than npm due to its performance advantages and better features at the time. However, npm has caught up significantly in recent versions, and both package managers are widely used today.

- **npm**: npm is the most popular package manager and the default for Node.js projects. It has the largest community, and its updates in recent years have addressed many of the concerns that prompted developers to use Yarn in the first place.


Both Yarn and npm have their strengths and weaknesses, and the decision to use one over the other largely depends on your specific needs:

- **Choose Yarn if**:
  - You need faster installations (due to its parallel installation).
  - You work in environments where offline support is important.
  - You want more mature support for monorepos via workspaces.

- **Choose npm if**:
  - You prefer using the default package manager that comes with Node.js.
  - You want the largest ecosystem and community support.
  - You are already familiar with npm’s workflow and features.

Both package managers are continuously improving, and with the advent of npm 7+, npm is now a competitive choice for many developers. However, Yarn still has a niche in performance, especially for larger projects and teams.