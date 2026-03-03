---
title: Writing, editing and storing content
short_title: Editing
# subtitle: 
authors:
    - id: FreekPols


--- 

There are multiple ways to write, edit and store content for Jupyter Book projects, and showing your content to the world (or not).
In the table below, we have summarized various possibilities, specified the requirements and highlighted their pros and cons. 
In the next chapters, each of these options is elaborated on, providing step-by-step instructions to get started.


## Storing

````{tab-set}
```{tab-item} Local
Description:  
You can write, edit and store your source files locally. 
If you want to see the output of the content in either web- or pdf-format, you'll need to have installed software (see below).

Pros:
- Not visible to outside world when in development
- Not supporting big tech with feeding data

Cons:
- Not available to others
- Back ups not automated
- No version control
```

```{tab-item} GitHub
Description:  
GitHub is a platform especially for software developers. 
It is owned by MicroSoft.

Pros:
- Version control
- Automated deploy of files
- No local software install required
- Well documented/support

Cons:
- Big Tech
- 
```

```{tab-item} GitLab
Description: 

Pros:
- Version control
- Automated deploy of files
- No local software install required

Cons:
- Functionality depends on university (and even faculty level)
- Less documented than GitHub.

```
```` 

## Writing and editing
Here we merely summarize the different ways of writing and editing your content.
Information for how to use / enable it is covered in the subsequent chapters.

````{tab-set}
```{tab-item} [Local with VSC](./4_local.md)
You can edit your project on your local machine. 

|requirements|pros|cons|
|---|---|---|
|python|Full control over project and environment | Requires installation and setup |
|JB|Works offline| Easy to use extensions for writing and editing|
|Node| | |
|code editor (e.g., VS Code)| Not visible to others until deployed|

```

```{tab-item} GitHub web editor 
If you work with GitHub, you can use the GitHub {abbr}`IDE`.

|requirements|pros|cons|
|---|---|---|
|GitHub account|No installation required|Little inconvenient with including new files |
|Deploy file | | |
|Internet connection|Accessible from any device with internet|Dependent on internet connection|

```

```{tab-item} Overleaf 

|requirements|pros|cons|
|---|---|---|
|Overleaf account|What you see is what you get editor | .tex files only (in basic version) |
|See GitHub web editor|LaTeX pdf | |
| |Integrated text AI |Dependent on internet connection|
```

```{tab-item} Jupyter Lab 
|requirements|pros|cons|
|---|---|---|
|Jupyter Lab|.ipyb and .md files | Requires installation and setup |
|MyST extension |

```

```{tab-item} GitLab
GitLab is advised at various Universities for multiple reasons. 
One is digital souverenity: the servers where the source files are stored are located at the campus.
The other is that an additional back-up is made which can be accessed by people from the university.


|requirements|pros|cons|
|---|---|---|
|GitLab account|No installation required| Not automatic deployed |
|gitlab.ci | | |
|Internet connection|Accessible from any device with internet|Dependent on internet connection|
```
````
