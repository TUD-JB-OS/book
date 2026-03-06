---
title: General idea of publishing with Jupyter Book
short_title: General

authors:
    - id: FreekPols
    

--- 

<!-- Imagine that you have worked on code, created a prototype, or made a molecule or enzyme where its structure is crucial... and then your supervisor requires you to hand in a static pdf only... much of your efforts is not conveyed through this use of media. What if there is a better way? A way that shows what you actually have done and accomplished and even let the reader interact with it, for instance by looking the molecule from different angles, play with the code to see how it works, or inspect the prototype in 3D. And what if you still create a beautiful but static pdf version of your report, but without the need of any additional effort.  
We have created a workflow and a template that allows you to do so. For this, we used Jupyter Book - an open source tool that allows you to create beautiful, interactive, and dynamic books and reports using Jupyter Notebooks and Markdown. It allows you to combine text, interactive code and data-analysis, and multimedia content in a single document that can be easily shared and published, both as online website and pdf.
Using our starterkit, you are equipped with a working website that automatically generates a good looking pdf with every update. You can easily add content, references, analysis, and share it with your supervisor (or the world). The template is designed to be user-friendly and easy to use, you can design it to your own preferences. 
Moreover, we created a manual that helps you with creating interactive content.
Interested in learning how to use it, or already exited to setup your own repo? Visit ...

-->

This book already shows how Jupyter Book can be used to create a clear report that combines text and multimedia content. To get an even better idea of what is possible, see this [video](#JB-publish-video).

Our idea is to engage young academics, starting from bachelors' students, in open science - being transparent about their data and data-processing and sharing their work openly with others. [Jupyter Book](https://jupyterbook.org/) seems to be a great tool for this at it allows simultaneously to write, code, and publish scientific articles, theses, and textbooks in a single environment. Using the Abstract Syntax Tree (AST), conversion from different format is possible and does not require additional effort.

```{iframe} https://tud365-my.sharepoint.com/personal/gvarnavides_tudelft_nl/_layouts/15/embed.aspx?UniqueId=b68ca022-d2b2-4928-b5e6-3b6eaa5c5632&embed=%7B%22ust%22%3Atrue%2C%22hv%22%3A%22CopyEmbedCode%22%7D&referrer=StreamWebApp&referrerScenario=EmbedDialog.Create
:label: JB-publish-video
:width: 100%
```

It allows to process data and to fully show the analysis online whilst hiding the code in a pdf version like this:

+++{"no-pdf": true}
```{code-cell} Python
:tag: hide-input
x = 2
y = 5

print(x+y)
```
+++

It also allows you to do calculations where the output value is used in the text - like using a variable in a sentence:

+++{"no-pdf": true}
```{code-cell} Python
:tag: hide-input
input_x = 2.034
output_y = input_x**2
```
+++ 

Where we use {eval}`output_y` in the text to show the output value.


- instruction video
- ideas of what we are aiming at
- what we developed....
- printscreen of pdf and website