# **Lab: Docusaurus Customization**  

## **Objective**  

In this lab, you will explore the fundamentals of Docusaurus by working with an existing repository, analyzing documentation structure, and making modifications. You will also generate a custom logo using an online AI-based tool.  

---
## Part 1: 

### **Step 1: Fork and Clone the Repository**  

1. Fork the following GitHub repository: [FedericoTartarini.github.io](https://github.com/FedericoTartarini/FedericoTartarini.github.io).  
2. Clone the repository to the local machine using:  

   ```bash
   git clone https://github.com/YOUR_USERNAME/FedericoTartarini.github.io.git
   cd FedericoTartarini.github.io
   ```

3. Install Dependencies and Fix Outdated Packages

Once inside the project directory, you should install the necessary dependencies by running:  

```bash
npm install
npm audit fix
```

- `npm install` will install all required packages specified in `package.json`.  
- `npm audit fix` will attempt to resolve outdated or vulnerable dependencies to ensure better compatibility and security.   

4. To launch the site in a local environment, you should execute:  

```bash
npm start
```   

---

### **Step 2: Analyze Documentation Structure**  

You should compare the forked repository to the official Docusaurus tutorial: [Docusaurus Tutorial](https://tutorial.docusaurus.io/). Pay attention to the following elements:  
- GitHub repository URL differences  
- "Edit this page" link functionality  
- Copyright footer and header links  
- Page structure and navigation design  

Write a brief summary of the differences observed.  

---

### **Step 3: Modify the Page** 
 
1. Update the site with **personal information** (e.g., name, description, placeholder article).  
2. Ensure modifications are made only for learning purposes—actual projects should follow distinct styling and branding guidelines.  

---

### **Step 4: Generate a Custom Logo** 
 
To enhance visual identity, you should generate a **custom logo** using an online AI-based logo generator. Some possible tools include:    
- [Looka](https://looka.com/)  
- [Brandmark](https://brandmark.io/)  

Once generated, the logo should be added to the project following Docusaurus customization guidelines.  

---

### **Step 5: Explore Docusaurus Documentation Features**
  
Review the Docusaurus documentation to understand advanced features such as:  
- Using tabs: [Tabs Feature](https://docusaurus.io/docs/markdown-features/tabs)  
- Additional customization options  
- Any other functionality that enhances documentation usability  

---

## Part 2: Deploy Your Website to the Cloud

> Please follow the instructions in this link for [deploying to GitHub Pages using GitHub Actions](./github-actions.md).
