---
title: Publishing your Jupyter Book project
short_title: Publishing
# subtitle: Using the GitHub Integrated Development Environment to write and edit content
authors:
    - id: FreekPols
    - id: LuukFroling

--- 

> Here we briefly described the various ways of publishing your Jupyter Book project. 

Publishing here is meant as the dissemination of the content you have created in your Jupyter Book project to the public in a visualized way - e.g. not being only the source code. We will discuss only two formats: static html and pdf. Note that there are more ways to publish your content, e.g. through [curvenote](https://curvenote.com/) allowing for a dynamic build of the site.
 
## Interactive website
You can 


## Static pdf

## Workflow



### Final tweaks with typst
Final tweaks to a typst after automatic generation via Jupyter Book can be rendered by running:
`typst compile main.typ` 
assuming that the main document is called `main.typ` and all other files are included or importated

or, specifying an output file:

`typst compile main.typ output.pdf`

A live preview of the typst document can be viewed by running:

`typst watch main.typ` 

### checks
Check whether typst is installed and which version by running:
`typst --version`
