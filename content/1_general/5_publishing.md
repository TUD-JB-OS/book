---
title: Publishing your Jupyter Book project
short_title: Publishing
# subtitle: Using the GitHub Integrated Development Environment to write and edit content
authors:
    - id: FreekPols
    - id: LuukFroling

--- 


 
## web


## pdf


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