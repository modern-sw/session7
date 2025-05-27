**Lab Instructions: Creating Pages, Documents, Blog Posts, and Deploying with Docusaurus**

### **Objective:**

In this lab, you will learn how to create pages, documents, and blog posts using Docusaurus, explore Markdown features, and deploy your website to the cloud. Follow the steps below to complete each part of the lab.

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

## **Part 1: Create a Page**

### **Goal:**
Learn how to create a standalone page in Docusaurus.

### **Instructions:**
1. Navigate to the tutorial link: [Create a Page](https://tutorial.docusaurus.io/docs/tutorial-basics/create-a-page).
2. Follow the steps outlined in the tutorial:
   - Understand the structure of Docusaurus pages.
   - Create a new page and add it to your site.
   - Customize the page content.
3. Verify that your new page appears correctly in the navigation.

### **Expected Outcome:**
By the end of this section, you should have a new page added to your Docusaurus site.

---

## **Part 2: Create a Document**

### **Goal:**

Learn how to create structured documentation using Docusaurus.

### **Instructions:**

1. Navigate to the tutorial link: [Create a Document](https://tutorial.docusaurus.io/docs/tutorial-basics/create-a-document).
2. Follow the steps outlined in the tutorial:
   - Create a new document inside the documentation folder.
   - Organize and structure your document.
   - Add metadata to your document.
3. Verify that your document is accessible through the sidebar.

### **Expected Outcome:**

By the end of this section, your site should contain a new document that is well-structured and accessible.

---

## **Part 3: Create a Blog Post**

### **Goal:**

Learn how to create and publish a blog post in Docusaurus.

### **Instructions:**

1. Navigate to the tutorial link: [Create a Blog Post](https://tutorial.docusaurus.io/docs/tutorial-basics/create-a-blog-post).
2. Follow the steps outlined in the tutorial:
   - Create a new blog post.
   - Add content using Markdown.
   - Set up metadata for the post.
3. Verify that your blog post appears correctly on the blog page.

### **Expected Outcome:**

By the end of this section, your Docusaurus site should have a blog post published.

---

## **Part 4: Markdown Features**

### **Goal:**

Explore Markdown features and their usage in Docusaurus.

### **Instructions:**

1. Navigate to the tutorial link: [Markdown Features](https://tutorial.docusaurus.io/docs/tutorial-basics/markdown-features).
2. Follow the steps outlined in the tutorial:
   - Learn about Markdown syntax supported in Docusaurus.
   - Implement different formatting styles in your documents and blog posts.
   - Test Markdown features such as tables, code blocks, and callouts.
3. Verify that Markdown formatting appears correctly on your site.

### **Expected Outcome:**

By the end of this section, you should have an understanding of how to format content effectively using Markdown in Docusaurus.

---

## **Part 5: Deploy Your Website to the Cloud**

> Please follow the instructions in this link for [deploying to GitHub Pages using GitHub Actions](./github-actions.md).