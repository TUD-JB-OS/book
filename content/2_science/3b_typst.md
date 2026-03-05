---
title: Typst Thesis Template
# short_title: 
# subtitle: Using Overleaf and GitHub to publish the web-based version of a project
authors:
    - id: FreekPols
    - id: LuukFroling
    - id: MaciejTopyla
--- 

For bachelor / master thesis we created a template utilizing [Typst](https://typst.app/), a modern typesetting system. When you use the [starterkit](https://github.com/TUD-JB-OS/starterkit), the build of a Typst thesis using this template is automated. That is, with every new commit the pdf export of the thesis is updated and include at the top right corner of your site.

Although the template comes with default settings that already let your thesis look professional, you can customize the output by changing the `typst_config.yml` file. In this file you can specify which content to include in the export, how to style the document and how to layout the pages. Below you find the `typst_config.yml` file with the defaults settings and explanations of the different options.

```{code} yml
:linenos:
:filename: typst_config.yml
version: 1
project:
  downloads:
    - id: thesis-pdf
  exports:
    - id: thesis-pdf
      format: typst
      template: https://github.com/TUD-JB-OS/typst_template
      output: ./exports/thesis_typst.pdf

      show_cover_full: true
      show_title_page: true
      show_title_page_image: false
      show_contributor_affiliations: true
      show_toc: true
      show_list_of_figures: false
      show_list_of_tables: false
      frontmatter_numbering: roman
      mainmatter_numbering: arabic

# page layout and styling      
      paper_size: a4
      margin_top_cm: 2.5
      margin_bottom_cm: 2.5
      margin_left_cm: 3.0
      margin_right_cm: 2.0
      font_body: Libertinus Serif
      font_mono: Consolas
      font_size_pt: 11
      line_spacing_em: 1
      
      toc_depth: 3
      logo: config/assets/brand/logo.svg

      # Cover variant: simple | graphical | custom
      cover_page_variant: graphical
      cover_background_image: figures/cover.jpg
      cover_title_box_opacity_pct: 55
      
      # Title-page variant: simple | formal | custom
      title_page_variant: "formal"
      title_page_image: figures/cover.jpg
      title_page_image_anchor: bottom
      title_page_image_width_cm: 3
      title_page_image_dx_cm: 0
      title_page_image_dy_cm: -3.0
```

## Override defaults
| Option | Type | Default | Description |
|-------|-------|---------|-------------|
| **show_cover_full** | boolean | `true` | Whether to show the full cover page |
| **show_title_page** | boolean | `true` | Whether to show the title page |
| **show_title_page_image** | boolean | `false` | Whether to show an image on the title page |
| **show_contributor_affiliations** | boolean | `true` | Whether to show contributor affiliations |
| **show_toc** | boolean | `true` | Whether to show the table of contents |
| **show_list_of_figures** | boolean | `false` | Whether to show the list of figures |
| **show_list_of_tables** | boolean | `false` | Whether to show the list of tables |
| **frontmatter_numbering** | string | `roman` | Page numbering style for frontmatter (e.g. "roman" for roman numerals) |
| **mainmatter_numbering** | string | `arabic` | Page numbering style for main content (e.g. "arabic" for numbers) |
| **paper_size** | string | `a4` | Paper size to be used (e.g. "a4", "letter") |
| **margin_top_cm** | number | `2.5` | Top margin in centimeters |
| **margin_bottom_cm** | number | `2.5` | Bottom margin in centimeters |
| **margin_left_cm** | number | `3.0` | Left margin in centimeters |
| **margin_right_cm** | number | `2.0` | Right margin in centimeters |
| **font_body** | string | `Libertinus Serif` | Font to use for body text |
| **font_mono** | string | `Consolas` | Font to use for monospaced text |
| **font_size_pt** | number | `11` | Base font size in points |
| **line_spacing_em** | number | `1` | Line spacing in em units |
| **toc_depth** | number | `3` | Depth of the table of contents |
| **logo** | file | - | Path to logo image (e.g. "config/assets/brand/logo.svg") |
| **cover_page_variant** | string | `graphical` | Cover page design variant ("simple", "graphical", or "custom") |
| **cover_background_image** | file | - | Path to background image for cover page |
| **cover_title_box_opacity_pct** | number | `55` | Opacity of title box on cover in percentage |
| **title_page_variant** | string | `formal` | Title page design variant ("simple", "formal", or "custom") |
| **title_page_image** | file | - | Path to image for title page |
| **title_page_image_anchor** | string | `bottom` | Anchor position of title page image |
| **title_page_image_width_cm** | number | `3` | Width of title page image in centimeters |
| **title_page_image_dx_cm** | number | `0` | Horizontal offset of title page image in centimeters |
| **title_page_image_dy_cm** | number | `-3.0` | Vertical offset of title page image in centimeters | 

