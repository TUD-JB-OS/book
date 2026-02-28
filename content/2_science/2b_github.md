---
title: GitHub for Jupyter Book
short_title: GitHub
subtitle: Using GitHub to publish the web-based version of a project
authors:
    - id: FreekPols
    - id: LuukFroling
--- 

Jupyter Book can be used in combination with GitHub for version control and publishing a web-based version of a project (such as this book). 

## Create a repository from template

There are several TUD-templates available, depending on the purpose of the project. 

::::{grid} 3 3 3 3

:::{card}
:header: TUD Book template
:link: https://github.com/TUD-JB-OS/book_template
A basic JB template for educational textbooks for TUD.
:::

:::{card}
:header: TUD thesis template
:link: https://github.com/TUD-JB-OS/latex_template

[temporary link]

:::

:::{card}
:header: TUD manuscript template
:link: https://github.com/TUD-JB-OS/manuscript_template 
A template for publishing scientific work using JB.
:::
::::

To use one of the templates, follow the steps below to create a repository from the template:

1) Go to the repository of the template
2) Click the green button `use this template` and click `create a new repository`
3) choose a name for your repository and choose the option `public`

:::{tip}
The name of your repository will be included in the URL of your project! The URL will be `https://YOUR_USERNAME.github.io/YOUR_REPOSITORY/`
:::

Now that you have created your repository, you can enable [GitHub pages](https://pages.github.com/):

4) Select 'GitHub Actions' as the source for GitHub pages by navigating to Settings > Pages > Build and deployment, and selecting 'GitHub Actions' from the source dropdown (default is 'Deploy from a branch')

5) Go to the `code` section of your repository, and click on the gear-icon on the right side (near **About**). Check the box **Use your GitHub Pages website**. This will add a link to your page in the about section. 

6) Last, go to `Actions` in the top menu and click on the (red) `initial commit`, then select `re-run all jobs`. 

The book will now be deployed, try opening the link in your about section. 

## Using Github desktop

[GitHub desktop](https://docs.github.com/en/desktop) can be used to interact with GitHub using a GUI instead of the command line. In this section we will go over cloning the newly created repository to your device. First, make sure GitHub desktop is installed. Once installed, go to File > Clone repository and select your project, which should be listed under 'your repositories. 

Open the repository using an editor of choice (see [setting up a local workspace](./2a_local.md)) and make an edit to the template. To reflect the changes made in your editor on the GitHub page, save your changes and click on `commit files` and `push origin` in GitHub desktop. This will push your changes to your GitHub repository, and a new version of your project will be uploaded to the project's page. 

:::{tip}
When using GitHub Desktop, you can open the selected repository folder with `Ctrl+Shift+A` for quick access to different projects. 
:::

## Github editor

The GitHub editor can be used to make changes to a repository you have write access to, without copying the entire repo onto your device.  
