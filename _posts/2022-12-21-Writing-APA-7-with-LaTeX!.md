---
layout: post
title: Writing APA 7 with LaTeX!
tags: [Programming, LaTeX]
style: border
color: warning
---

I finally tried completing an entire assignment using just $\LaTeX{}$! Its an awesome typesetting tool, however, setting it up to write an APA 7 style document was quite a challenge.

I also couldn't find any comprehensive guides on how to do so and had to go through a billion Google searches before I finally got what I wanted. So I thought I'd make my own guide for anyone else who wants to get started with APA 7 in $\LaTeX{}$.

## Assumptions

I will assume that you are at least somewhat familiar with your LaTeX editor, and also that you know how to install LaTeX packages for whatever specific distribution you have.

For Windows users most people often recommend MiKTeX, which I already had installed on my system, however, as a heads up to anyone who is planning on writing LaTeX in VS Code, you'll need to have the Perl language installed in order to use MiKTeX.

For reasons I will explain some other time, I couldn't install Perl. So I grabbed the lightest distribution of LaTeX that I could find that worked with VS Code without Perl, that wonderfully light distribution is [TinyTeX](https://github.com/rstudio/tinytex)!

It basically just installs the TeXLive distribution without the gazillion packages it forces you to install. It also comes with the TeXLive package manager `tlmgr`.

## Package Requirements

You'll first need to install the following packages and all their dependencies:

-   BibLaTeX
-   Biber
-   biblatex-apa
-   latex-graphics
-   apa7
-   threeparttable
-   float
-   lipsum (Optional: it allows you to auto-generate Lorem Ipsum placeholder text)

As of right now, BibTeX only supports up to APA 6 references and citations. The only bibliography generator that supports APA 7 is Biber with BibLaTeX.

## Starting the TeX file

Now we'll just have to insert some boilerplate for the APA 7 document. For students, I've already created a template you can just copy and paste straight into your editor:

```latex
\documentclass[12pt, stu, hidelinks]{apa7}

\usepackage{newtxtext}
\usepackage{newtxmath}

\usepackage[style=apa]{biblatex}
\addbibresource{apa7-student.bib}

\title{Assignment Title}
\author{Student Name}
\course{CRSE 123: Sample Course Name}
\professor{Dr. Professor Name}
\duedate{\today}
\authorsaffiliations{University Name}

\abstract{
    \lipsum[1-2]
}

\begin{document}
\clearpage
\maketitle
\tableofcontents
\clearpage

\section{Introduction}

\lipsum[2-4]

\end{document}
```

Let's dive into each of those lines.

-   `\documentclass[12pt,stu,hidelinks]{apa7}`
    -   Defines the document class
    -   Font size `12pt`
    -   `stu` means its a student paper
        -   use `jou` for a printed journal appearance
        -   use `man` for a journal submission document
        -   use `doc` for just a typical LaTeX document appearance
    -   `hidelinks` will remove the colored boxes that LaTeX will keep drawing around every single citation and reference in your paper. They will still be hyperlinked to the reference page, just no annoying box.
-   `\usepackage{newtxtext}` and `\usepackage{newtxmath}`
    -   Use these packages to get the Times Roman font in your papers for both text and math.
    -   `newtx` is the newer and preferred package, but there are older implementations such as the `times` + `mathptmx` packages. Feel free to use whichever you like.
-   `\usepackage[style=apa]{biblatex}`
    -   Uses the BibLaTeX bibliography manager
    -   Tells it to format in APA 7 style
        -   use `apa6` for APA 6 style
-   `\addbibresource{apa7-student.bib}`
    -   Load the bibliography file. Replace `apa7-student.bib` with the actual filename of your bibliography file
-   The next set of lines just put all the details required for the title page
    -   Read more [here](https://mirror.niser.ac.in/ctan/macros/latex/contrib/apa7/apa7.pdf)
-   `\abstract{}`
    -   Text that goes in the abstract should be put within here.
    -   If you don't need an abstract just delete this line
-   `\begin{document}` and `\end{document}`
    -   This is where the content of your entire paper will be placed
-   `section{}`
    -   Creates a heading, will automatically format into APA 7 style
    -   Use `\subsection{}` and `\subsubsection{}` as needed for subsections

## APA Style Tables

Creating an APA style table is pretty simple using the `threeparttable` package:

```latex
% H comes with "float" package, it forces the floating object to be drawn exactly where the command is located by turning it into a non-floating object.
\begin{table}[H]
	\centering
	\begin{threeparttable}
		\caption{Text that shows below the title "Table X"}
		\begin{tabular}{llll} % 4 columns
			\toprule
			Column 1 & Column 2 & Column 3 & Column 4 \\
			\midrule
			entry 1  & 47.34    & 0.13     & 0.19\%  \\
			entry 2  & 89.21    & 0.12     & 0.16\%  \\
			\bottomrule
			total    & 136.55   & 0.25     & 0.35\%
		\end{tabular}
	\end{threeparttable}
\end{table}
```

Declare the `\toprule` command before you all the entries you want included in the table head. Then `\midrule` for the main body of the table, and finally `\bottomrule` for the end of the table, total results or conclusions.

Using the `threeparttable` package, this will automatically render as a beautiful APA style table!

## Creating and Citing Figures

Creating figures requires a little bit of work. First you'll need to move the image file that you wish to use in your figure into the same directory as your TeX document. Putting it into a subfolder also works, as we will be addressing the file by its relative path.

Then, we'll create a LaTeX figure using the following code:

```latex
\begin{figure}[H]
	\makebox[\textwidth]{\includegraphics[width=0.8\paperwidth]{image_path.jpg}}
	\caption{Name of the Figure}
	\label{fig:NameUsedForCitation}
\end{figure}
```
