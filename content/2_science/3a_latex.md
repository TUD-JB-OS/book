---
title: LaTeX
# short_title: 
# subtitle: Using Overleaf and GitHub to publish the web-based version of a project
authors:
    - id: FreekPols
    - id: LuukFroling

--- 
# LaTeX

## Bachelor and Master Theses

A [TUD LaTeX template](https://github.com/TUD-JB-OS/latex_template) can be used to convert your theses markdown files into a PDF format. The template provides a ready-made structure, customisable settings, and optional elements like a cover image or logo. 

The template can be used by adding the template to the export section in the `myst.yml`: 

```{code} yaml

downloads:
    - id: output-pdf

exports:
    - format: pdf 
        output: exports/output_file.pdf
        template: { - TODO: replace with published link - }
        id: output-pdf
```

After adding the template, you can build a PDF file using the `--pdf` flag: 

``` 
jupyter book build --pdf
```

Additional options can be used to customise the output. A full example of an `export.yml` file can be found [here](https://github.com/TUD-JB-OS/latex_template/blob/main/example/export.yml).


:::{dropdown} Configuration options
:closed:

An example `export.yml` file can be found [here](https://github.com/TUD-JB-OS/latex_template/blob/main/example/export.yml). 

| Option | Type | Default | Description |
|-------|-------|---------|-------------|
| **link** | string | - | Link to the article online as a footnote on the first page |
| **showTOC** | boolean | `true` | Whether to show the table of contents after the title page |
| **tocDepth** | number | 2 | =The depth of the table of contents (e.g. 2 for sections and subsections) |
| **cover** | file | - | Path to an optional image for the title page (e.g. "images/front.png") | 
| **cover_width** | string | `0.9\\linewidth` | Width of the cover image (e.g. "8cm" for 8 centimeters, "0.9\linewidth" for 90% of the line width) | 
| **cover_margin** | string | `2em` | Vertical space between the title and the cover image (e.g. "2em" for 2em) | 
| **logo** | file | - | Path to an optional logo image to be placed at the top of each page | 
| **logo_width** | string | `1cm` | Width of the logo image in cm (e.g. "10" for 10cm) | 
| **margin_{side}** | string | `2.5cm` | margin of the page (e.g. "2.5cm" for 2.5 centimeters). Can be used for top, bottom, left and right. | 
| **papersize** | string | `a4paper` | Paper size to be used. See the [reference guide](https://www.overleaf.com/learn/latex/Page_size_and_margins#Reference_guide) for available sizes.  | 
| **show_pagenumbers** | string | `arabic` | Whether to show page numbers in the footer. Page numbers can be turned off by setting show_pagenumbers to `gobble`. | 
| **extra_information** | string | `\u00A0` | Extra information to be placed on the title page (e.g. "Version 2.0, Draft, university, course"). Default is a space character. | 



:::

## Scientific Publications

-
