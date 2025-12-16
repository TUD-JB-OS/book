---
title: Setting up a local workspace
short_title: Get Started
subtitle: Using the Jupyter Book command-line tools with Visual Studio Code
authors:
    - id: FreekPols
    - id: LuukFroling
---

This page will explain how to install the Jupyter Book command-line tools on your device, and how to start a local development server using Visual Studio Code. 

## Install required tools 

Before getting started, make sure the following are installed: 

- An environment manager ([pip](https://pypi.org/project/pip/) will be used in this book)
- [Git](https://git-scm.com/install/) and/or [Github Desktop](https://desktop.github.com/download/) 
- [Visual Studio Code](https://code.visualstudio.com/) (or another editor of choice)

If you prefer alternatives to pip, the [Jupyter Book documentation](https://jupyterbook.org/stable/get-started/install/) describes several other installation methods

## Install Jupyter Book 

With the required tools in place, the next step is to install Jupyter Book itself.  
This gives you access to the `jupyter-book` command-line tools. To install Jupyter Book, open a terminal and run:

```bash 
pip install "jupyter-book>=2.0.0"
```

After installation, you can verify that Jupyter Book is available by checking the version:

```
jupyter book --version
```

which shows `v2.0.0` if successfully installed.

## Starting a project

There are 2 ways to start a project. 

(initialise-local-project)=

### new project

The Jupyter Book package comes with an `init` command, used to initialise a new myst project in the current directory. Using VScode, open the project folder and start a terminal using 'Ctrl + Shift + `' (or by clicking Terminal > New Terminal). In the terminal, initialise a new jupyter book project:  

```bash
jupyter book init
```

To get started writing content in your new project folder, refer to the [Jupyter Book documentation](https://jupyterbook.org/stable/get-started/create-content/).

### Use template 

Alternatively, there are several TUD templates to choose from.

[todo, link templates and how to use them]

## Simple Browser extension 

The Simple Browser extension provides an easy way to see live updates in VScode. 

:::{tip}
VScode has a large extension marketplace, making it easy to add tools like live previews and Markdown support. To read more about extensions, visit the [extension market place](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace)
:::

To open a live preview of your project, start a built-in server and open Simple Browser:

1) Start a local development instance
```bash
jupyter book start
```

Once loaded the project should be accessible through the local host, using a link similar to `https://localhost:3000` (check the terminal). 

2) Open Simple Browser from the command pallete. Press Ctrl+shirt+p and search for 'simple browser'. When prompted for an URL, provide the URL shown in the command line. 

Try saving an edit to a markdown file, and the change will be reflected on the webpage!


