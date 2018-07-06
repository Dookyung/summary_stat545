
# cm001 - introduction 


## Intro to course; S/W install; acct sign-ups

### Data Domination

> "Software programming, algorithm development and other technological skills can give scientists an edge in their fields."
> --- Careers,31 August 2017

> "A picture is worth a thousand words."


### Data Science Tool :

- R

- Rstudio : an integrated development enviroment(IDE) for R

- Rmarkdown


\begin{center}\includegraphics[width=0.75\linewidth]{diagrams/Rmarkdown} \end{center}


\begin{center}\includegraphics[width=0.75\linewidth]{diagrams/Markdown} \end{center}


\begin{center}\includegraphics[width=0.75\linewidth]{diagrams/html} \end{center}


- git and github : Version control systems(VCS) and collaboration tools.


\begin{center}\includegraphics[width=0.75\linewidth]{diagrams/git_finaldoc} \end{center}


- GNU Make

    * How to make end products more integrated and more reproducible?
    
    * How to keep everything up-to-date?
    
    * if the data changes, how do we remember to remake the figure 2B and 4?



\begin{center}\includegraphics[width=0.75\linewidth]{diagrams/make} \end{center}



\begin{center}\includegraphics[width=0.75\linewidth]{diagrams/make2} \end{center}


### What is Data Science?



\begin{center}\includegraphics[width=0.75\linewidth]{diagrams/datascience} \end{center}



\begin{center}\includegraphics[width=0.75\linewidth]{diagrams/dsskill} \end{center}



\begin{center}\includegraphics[width=0.75\linewidth]{diagrams/dsworkflow} \end{center}



\begin{center}\includegraphics[width=0.75\linewidth]{diagrams/bigdata} \end{center}



\begin{center}\includegraphics[width=0.75\linewidth]{diagrams/3d} \end{center}


## Deep Thoughts about data analytic work; intro to R and RStudio

### To do before next class:

-  [swirl](http://swirlstats.com): "a software package for the R programming language that turns the R console into an interactive learning environment"


### Basics of working with R at the command line and RStudio goodies

- Launch RStudio/R and notice the default panes:

  * Console (entire left)
  * Environment/History (tabbed in upper right)
  * Files/Plots/Packages/Help (tabbed in lower right)

[Customizing RStudio](https://support.rstudio.com/hc/en-us/articles/200549016-Customizing-RStudio).

- Make an assignment.


```r
x <- 3 * 4
x
#> [1] 12
```

"assignments" form:


```r
objectName <- value
```

  * Keyboard shortcut for assignment operator `<-` is Alt + - (the minus sign).

  * RStudio offers many handy [keyboard shortcuts](https://support.rstudio.com/hc/en-us/articles/200711853-Keyboard-Shortcuts). 
  
  * Alt+Shift+K brings up a keyboard shortcut reference card.


- Object names 

```
i_use_snake_case
other.people.use.periods
evenOthersUseCamelCase
```

Make another assignment

```r
this_is_a_really_long_name <- 2.5
```

To inspect this, try out RStudio's completion facility: type the first few characters, press TAB, add characters until you disambiguate, then press return.

Make another assignment

```r
jenny_rocks <- 2 ^ 3
```

R has a mind-blowing collection of built-in functions that are accessed like so


```r
functionName(arg1 = val1, arg2 = val2, and so on)
```

- `seq()` which makes regular sequences of numbers

    * Type `se` and hit TAB.
    

```r
seq(1,10)
#>  [1]  1  2  3  4  5  6  7  8  9 10
```



```r
yo <- "hello world"
```



```r
y <- seq(1, 10)
y
#>  [1]  1  2  3  4  5  6  7  8  9 10
```

Surrounding the assignment with parentheses, which causes assignment and "print to screen" to happen.


```r
(y <- seq(1, 10))
#>  [1]  1  2  3  4  5  6  7  8  9 10
```

Not all functions have (or require) arguments:


```r
date()
#> [1] "Fri Jul  6 21:00:12 2018"
```

- The workspace is where user-defined objects accumulate. You can also get a listing of these objects with commands:


```r
objects()
#> [1] "jenny_rocks"                "this_is_a_really_long_name"
#> [3] "x"                          "y"                         
#> [5] "yo"
ls()
#> [1] "jenny_rocks"                "this_is_a_really_long_name"
#> [3] "x"                          "y"                         
#> [5] "yo"
```

remove the object named `y`


```r
rm(y)
```

To remove everything:


```r
rm(list = ls())
```

or click the broom in RStudio's Environment pane.

### Workspace and working directory

#### Workspace, .RData

#### Working directory

You can explicitly check your working directory with:


```r
getwd()
```

__Although I do not recommend it__, in case you're curious, you can set R's working directory at the command line like so:


```r
setwd("~/myCoolProject")
```

__Although I do not recommend it__, you can also use RStudio's Files pane to navigate to a directory and then set it as working directory from the menu: Session --> Set Working Directory --> To Files Pane Location. (You'll see even more options there). Or within the Files pane, choose __More__ and __Set As
Working Directory__.

### RStudio projects

Keeping all the files associated with a project organized together -- input data, R scripts, analytical results, figures -- is such a wise and common practice that RStudio has built-in support for this via its _projects_.

[Using Projects](https://support.rstudio.com/hc/en-us/articles/200526207-Using-Projects)


Let's enter a few commands in the Console, as if we are just beginning a project:


```r
a <- 2
b <- -3
sig_sq <- 0.5
x <- runif(40)
y <- a + b * x + rnorm(40, sd = sqrt(sig_sq))
(avg_x <- mean(x))
#> [1] 0.45
write(avg_x, "avg_x.txt")
plot(x, y)
abline(a, b, col = "purple")
```



\begin{center}\includegraphics[width=0.7\linewidth]{intro_files/figure-latex/toy-line-1} \end{center}



```r
dev.print(pdf, "toy_line_plot.pdf")
#> pdf 
#>   2
```

```
source(file.r)
```

In your favorite OS-specific way, search your files for `toy_line_plot.pdf` and presumably you will find the PDF itself (no surprise) but _also the script that created it (`toy-line.r`)_. This latter phenomenon is a huge win. One day you will want to remake a figure or just simply understand where it came from. If you rigorously save figures to file __with R code and not ever ever ever the mouse or the clipboard__, you will sing my praises one day. Trust me.

### stuff

It is traditional to save R scripts with a `.R` or `.r` suffix. 

Comments symbol : `#`  
de(comment) : Ctrl+Shift+C 

This workflow will serve you well in the future:

  * Create an RStudio project for an analytical project
  * Keep inputs there
  * Keep scripts there; edit them, run them in bits or as a whole from there
  * Keep outputs there (like the PDF written above)

Many long-time users never save the workspace, never save `.RData` files (I'm one of them), never save or consult the history. 

Option to disable the loading of .RData and permanently suppress the prompt on exit to save the workspace (go to Tools->Options->General).






