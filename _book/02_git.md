
# R Markdown test drive

#### Overview

Here is the official R Markdown documentation: <http://rmarkdown.rstudio.com>

#### Step 0: Software installation and configuration

#### Step 1: Get ready to work

#### Step 2: Practice with RStudio's boilerplate R Markdown document

Do this: *File > New File > R Markdown ...*

  - Give it an informative title. 
  - Accept the default Author or edit if you wish.
  - Accept the default output format of HTML.
  - Click OK.
  
Click on "Knit HTML" or do *File > Knit Document*. RStudio should display a preview of the resulting HTML. 

#### Step 3: Take control of the output format

The magical process that turns your R Markdown to HTML is like so: `foo.Rmd --> foo.md --> foo.html`. 

**Output format** 

html:

``` yaml
    ---  
    title: "Something fascinating"  
    author: "Jenny Bryan"  
    date: "2018-07-07"
    output:  
      html_document:  
        keep_md: true  
    ---  
```

GitHub-flavored markdown:

``` yaml
    ---  
    title: "Something fascinating"  
    author: "Jenny Bryan"  
    date: "2018-07-07"
    output: github_document
    ---  
```

#### Step 4: Swap out the "guts" of the document

Insert an empty R chunk:

    
    ```r
    ## insert your brilliant WORKING code here
    ```

#### Step 5: Develop your report


#### Step 6: Publish your report


Creating, commiting, and pushing markdown is a very functional, lighweight publishing strategy. 

This is (sort of) another example of keeping things machine- and human-readable, which is bliss. By making `foo.Rmd` available, others can see and run your __actual code__. By sharing `foo.md` and/or `foo.html`, others can casually browse your end product and decide if they even want to bother.


#### Troubleshooting

Make sure RStudio and the `rmarkdown` package (and its dependencies) are up-to-date.

Get rid of your `.Rprofile` at least temporarily.

Insert a chunk in your `.Rmd` document so that it renders even when there are errors.

    
    
Tolerate errors in one specific chunk.

    
    ```r
    ## your sketchy code goes here ;) 
    ```

Check your working directory.

  * `getwd()`
  * `list.files()`

Don't try to change working directory within an R Markdown document.

Don't be in a hurry to create a complicated sub-directory structure.


### HTML on GitHub

I have more [general ideas](bit006_github-browsability-wins.html) about how to make a GitHub repo function as a website.


#### Be savvy about your files

Keep files in the plainest, web-friendliest form that is compatible with your main goals. Plain text is the very best. GitHub offers special handling for certain types of files:

  * Markdown files, which may be destined for conversion into, e.g., HTML
  * Markdown files named `README.md`
  * HTML files, often the result of compiling Markdown files
  * Source code, such as `.R` files
  * Delimited files, containing data one might bring into R via `read.table()`
  * PNG files
  
#### Get over your hang ups re: committing derived products
  
Let's acknowledge the discomfort some people feel about putting derived products under version control. 

The taboo of keeping derived products under version control originates from compilation of binary executables from source. Software built on a Mac would not work on Windows and so it made sense to keep these binaries out of the holy source code repository. 


#### Markdown

**Keep intermediate Markdown.** Commit both `foo.Rmd` and `foo.md`, even if you choose to `.gitignore` the final `foo.html`. As of [September 2014](https://github.com/github/markup/pull/343), GitHub renders R Markdown files nicely, like Markdown, and with proper syntax highlighting, which is great. But, of course, the code blocks just sit there un-executed, so my advice about keeping intermediate Markdown still holds. You want YAML frontmatter that looks something like [this](https://gist.github.com/jennybc/402761e30b9be8023af9#file-yaml_frontmatter_rmd_keep_md-yml) for `.Rmd`:




``` yaml
---
title: "Something fascinating"
author: "Jenny Bryan"
date: "`r format(Sys.Date())`"
output:
  html_document:
    keep_md: TRUE
---
```

or like [this](https://gist.github.com/jennybc/402761e30b9be8023af9#file-yaml_frontmatter_r_keep_md-yml) for `.R`:

``` yaml
#' ---
#' title: "Something fascinating"
#' author: "Jenny Bryan"
#' date: "`r format(Sys.Date())`"
#' output:
#'   html_document:
#'     keep_md: TRUE
#' ---
```

#### `README.md`

`README.md` at the top-level of your repo as the *de facto* landing page. This is analogous to `index.html`.

Some repositories consist solely of `README.md`. 

  * Jeff Leek's write-ups on [How to share data with a statistician](https://github.com/jtleek/datasharing) 
  
  * [Developing R packages](https://github.com/jtleek/rpackages). 
  
  
`README`-only repos vs gists : 

  * [PNGs README gallery](https://github.com/Reproducible-Science-Curriculum/rr-organization1/tree/27883c8fc4cdd4dcc6a8232f1fe5c726e96708a0/slides/organization-slides) 

