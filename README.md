R data analysis template
========================

Over years I came up with a quite standardized template. Though it usually degraded to copying a number of files from previous projects.  With this template I try to formalize this approach.

[cookiecutter](https://github.com/audreyr/cookiecutter) is a tool to template new project files and folder structures.  It still seems quite active and has templates beyond a single language it seems a promising home for this task.

These templates also contain some sample code for my reference how to achieve typical tasks.  The most code is written in R files and derivatives like rmd and rnw.  But I also make use of `make` for building the project, and additional shell utilites like latexmk and pandoc.  At some future point I will provide a setup script - at the moment you will need to weed through dependencies manually.

News
------

I am learning more and more about the R package workflow.  Combining
this *and* a Make based workflow seems a waste.  I start the package
[vignetteEngineMake](https://github.com/bdcaf/vignetteEngineMake) to
bring make based vignettes to R packages.

*2018-07-17*  I am currently considering integrating this with
[vignetteEngineMake](https://github.com/bdcaf/vignetteEngineMake).
The idea is to use `devtools` to create the package - however I find
for larger vignettes a make based workflow more helpful.  In
particular I am thinking about scripts that download huge datasets
from servers - it is not suggested to pack those into R packages -
however I need to work on code that needs datasets going into
gigabytes to reasonable show it's performance.

Requirements
------------
Install `cookiecutter` command line: `pip install cookiecutter`

or alternatively

Install `cookiecutter` command line: `brew install cookiecutter`

Usage
-----
Generate a new Cookiecutter template layout: `cookiecutter gh:bdcaf/cookiecutter-r-data-analysis`.
It creates a minimal project that can be run typing `make`.
Explore the `Readme.md` in the generated directory for more.

**Note**
Many functions used require that the project is a valid R package.
The slug must be a valid package name, therefore it must only consist of characters, numbers and `.`, also it must start with a character.
I wrote a simple replacement for spaces to dots, but for the rest you are on your own!



Workflow
----------

 + Input data is put in the `data` directory.
 + Transformed data which can be recreated in the `work` directory
 + Output for publication or else is put in the `artifacts` folder
 + `R` source code is put in the `r` folder
 + Textual stuff like markdown, tex, rmd and rnw files in the doc
 	 folder

Notes
------

- When used *within* a R package I find it useful to put reused code in
the packages R folder so it can be reloaded using `devtools::load_all`
or apropriate version.


Requirements
------------

This exemplary workflow has plenty of dependencies. The main ones are:
 - R with knitr, pander, dplyr, ggplot packages
 - pandoc for Word file
 - latex for pdf generation.

License
-------
This project is licensed under the terms of the [MIT License](/LICENSE)
