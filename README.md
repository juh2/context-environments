# Modular structured environment files for ConTeXt

## Disclaimer

I am new to ConTeXt, so don't expect anything fancy here. Most settings are copied from other people's setup.

## Purpose

This repository is part of my current setup to produce books for distribution by print on demand services like Createspace. I have a quite unusual setup because I don't edit ConTeXt files. I use Pandoc to produce XHTML files from Markdown sources. Then I use the XHTML file as input file to be typeset by ConTeXt.

For this process you need a special environment file which maps XML to ConTeXt. This file is provided by [Pablo Rodríguez](https://github.com/ousia). It is called [pandoc-xhtml](https://github.com/ousia/from-pandoc-to-context/blob/master/pandoc-xhtml.tex) and is part of the repository [from-pandoc-to-context](https://github.com/ousia/from-pandoc-to-context). Thanks a lot, Pablo, for sharing this!

Most books are not printed in a standard papersize so we have to setup our own papersizes. Papersizes in the book industry are called trim sizes. I define papersizes for trim sizes that are supported by Createspace. The papersizes are defined in the `env-trimsize*.tex` files. The name of the environment reflects the chosen trim size.

Settings that are not trim size dependent are defined in the other `env-*` files in this repository. The structure of the files will change over time.

## Usage

If you want to use this repository to typeset Markdown files via Pandoc, please do the following after installing Pandoc.

* Clone this repository

* Clone [from-pandoc-to-context](https://github.com/ousia/from-pandoc-to-context) in the same directory so that it is in the same parent directory as this repository.

* Create a Pandoc project.

   You can start with my [boilerplate](https://github.com/juh2/pandoc-project-boilerplate), but you have to adjust the Makefile according to convert Markdown to XHTML and to typeset the XHTML file with ConTeXt.

* Create a file called `env.tex` in your Pandoc project with the following content:

~~~~~~~~~~~
   \input ../context-environments/env-trimsize5-8.tex
   \input ../context-environments/env-fonts.tex
   \input ../context-environments/env-heading.tex
   \input ../context-environments/env-makeups.tex
   \input ../context-environments/layout.tex
   \input ../from-pandoc-to-context/pandoc-xhtml.tex
~~~~~~~~~~~

* Create a XHTML file with Pandoc from your Markdown sources.

* Compile the XHTML file with ConTeXt using the command option `--environment=env.tex`. This will load all environment files from this repository and the mapping file from the repo [from-pandoc-to-context](https://github.com/ousia/from-pandoc-to-context)

* Consider using the command option `--mode` to make use of the modes in the environment files.
