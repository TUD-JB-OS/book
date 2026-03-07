---
title: General idea of publishing with Jupyter Book
short_title: General

authors:
    - id: FreekPols
    
kernelspec:
  name: python3
  display_name: 'Python 3'
--- 

<!-- Imagine that you have worked on code, created a prototype, or made a molecule or enzyme where its structure is crucial... and then your supervisor requires you to hand in a static pdf only... much of your efforts is not conveyed through this use of media. What if there is a better way? A way that shows what you actually have done and accomplished and even let the reader interact with it, for instance by looking the molecule from different angles, play with the code to see how it works, or inspect the prototype in 3D. And what if you still create a beautiful but static pdf version of your report, but without the need of any additional effort.  
We have created a workflow and a template that allows you to do so. For this, we used Jupyter Book - an open source tool that allows you to create beautiful, interactive, and dynamic books and reports using Jupyter Notebooks and Markdown. It allows you to combine text, interactive code and data-analysis, and multimedia content in a single document that can be easily shared and published, both as online website and pdf.
Using our starterkit, you are equipped with a working website that automatically generates a good looking pdf with every update. You can easily add content, references, analysis, and share it with your supervisor (or the world). The template is designed to be user-friendly and easy to use, you can design it to your own preferences. 
Moreover, we created a manual that helps you with creating interactive content.
Interested in learning how to use it, or already exited to setup your own repo? Visit ...

-->

```{note} to do
- instruction video
- printscreen of pdf and website
- interactive graph
- pdf output
```
> Here we briefly described our intends and why we think Jupyter Book is great to achieve this.

This book already shows how Jupyter Book can be used to create a clear report that combines text and multimedia content. To get an even better idea of what is possible, see this [video](#JB-publish-video).

(whyJB)=
## Why Jupyter Book?

Our idea is to engage young academics, starting from bachelors' students, in open science - being transparent about their data and data-processing and sharing their work openly with others. [Jupyter Book](https://jupyterbook.org/) is a great tool for this as it allows to write, code, and publish scientific articles, theses, and textbooks in a single environment. Using the Abstract Syntax Tree (AST), conversion from different format is possible and does not require additional effort.

```{figure} ../images/AST.png
:alt: figure showing that the markdown files can be converted to a pdf and website using the AST
:width: 100%

Your jupyterBook project can be converted to a pdf, docx and website.
```

```{iframe} https://tud365-my.sharepoint.com/personal/gvarnavides_tudelft_nl/_layouts/15/embed.aspx?UniqueId=b68ca022-d2b2-4928-b5e6-3b6eaa5c5632&embed=%7B%22ust%22%3Atrue%2C%22hv%22%3A%22CopyEmbedCode%22%7D&referrer=StreamWebApp&referrerScenario=EmbedDialog.Create
:label: JB-publish-video
:width: 100%
:caption: Video credit: G. Varnavides
:alt: Video showing the use of Jupyter Book with interactive functionality like zooming in.
```

With Jupyter Book, you can process data and fully show the analysis online whilst hiding the code in a pdf version like this:

+++{"no-pdf": true}
```{code-cell} Python
:tag: hide-input
x = 2
y = 5

print(x+y)
```
+++

It allows you to do calculations where the output value is used in the text - like using a variable in a sentence:

+++{"no-pdf": true}
```{code-cell} Python
:tag: hide-input
input_x = 2.034
output_y = input_x**2
```
+++ 

Where we use {eval}`output_y` in the text to show the output value. Note that the output is visible on the website, but if you inspect the pdf version, you will see that the code is hidden.

```{code-cell} Python
:tag: hide-input

import numpy as np
import matplotlib.pyplot as plt
import ipywidgets as widgets
from ipywidgets import interact

x = np.linspace(0, 20, 7)
y = 2.03 * x + np.random.normal(0, 3, len(x))

def update(a):

    plt.clf()
    fig, (ax1,ax2) = plt.subplots(1,2)
    ax1.plot(x, y, 'k.')
    ax1.plot(x, a*x, 'r--')
    ax2.plot(x, (y-a*x)**2, 'k.')
    plt.show()

interact(update, a=widgets.FloatSlider(min=-2, max=3, step=0.1, value=1))

```



(whatwedid)=
## What we have done

We created a **starterkit** which allows you to create a Jupyter Book project with a pdf version that is automatically generated with every update. With only a few steps, you can have your own Jupyter Book project up and running online - or if you prefer only locally or behind SSO login. 

We created **two templates**, one based on LaTeX and one based on Typst. These templates can be downloaded and tweaked to meet your preferences, but already look good out of the box. 

We created a **manual** and **instruction videos** that help you understand what is possible, how to use the starterkit and how to easily edit your content.

We tested our workflow with **multiple users** and got feedback on the user-friendliness and the design of the templates.


