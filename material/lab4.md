**Lab Instructions: Managing Documentation, Translation, and Deployment with Docusaurus**

### **Objective:**
In this lab, you will learn how to manage documentation versions, translate your site, and deploy your website to the cloud using Docusaurus. Follow the steps below to complete each part of the lab.

---

## **Part 0: Setup** 

You can continue from the previous lab. If you do, please commit your changes before proceeding. Alternatively, you can use the same workflow to generate a Docusaurus project:

```sh
npx create-docusaurus@latest week-nr-lab-nr classic
```

- When prompted, choose **JavaScript** (use the arrow keys to select and press Enter):
   ```
   » - Use arrow-keys. Return to submit.
   >   JavaScript
       TypeScript
   ```

- Change into the project directory and start the development server:
   ```sh
   cd week-nr-lab-nr 
   npm start   
   ```

By default, a browser window will open at [`http://localhost:3000`](http://localhost:3000). To stop the server, use `ctrl + C` (on Mac, use `cmd + C`).


---

## **Part 1: Manage Documentation Versions with Docusaurus**

### **Goal:**

Learn how to create and manage different versions of your documentation using Docusaurus.

### **Instructions:**

1. Navigate to the tutorial link: [Manage Docs Versions](https://tutorial.docusaurus.io/docs/tutorial-extras/manage-docs-versions/).
2. Follow the steps outlined in the tutorial:
   - Understand how versioning works in Docusaurus.
   - Create a new version of your documentation.
   - Maintain and update different versions.
3. Verify that your documentation versions are correctly displayed and accessible.
4. Useful Link: https://docusaurus.io/docs/versioning

### **Expected Outcome:**

By the end of this section, you should have a versioned set of documentation that allows users to switch between different releases.

---

## **Part 2: (OPTIONAL) Translate Your Site**

### **Goal:**

Enable multilingual support for your site by translating its content.

### **Instructions:**

1. Navigate to the tutorial link: [Translate Your Site](https://tutorial.docusaurus.io/docs/tutorial-extras/translate-your-site/).
2. Follow the steps outlined in the tutorial:
   - Understand the internationalization (i18n) feature in Docusaurus.
   - Set up the necessary configuration files.
   - Add translations for various languages.
3. Ensure that your site is accessible in multiple languages and test language switching functionality.
4. Useful Link: [Tutorial](https://docusaurus.io/docs/i18n/tutorial) and [Short video](https://www.youtube.com/watch?v=2Arz1j5n2u0)

### **Expected Outcome:**

By the end of this section, your site should be available in at least two languages, with an option for users to switch between them.

---

## Part 3: Deploy Your Website to the Cloud

> Please follow the instructions in this link for [deploying to GitHub Pages using GitHub Actions](./github-actions.md).
