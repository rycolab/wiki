# Style Guide

## Header Example
The following is a sample author header. 

```latex
\usepackage{tipa}

\newcommand{\ucambridge}{\normalfont \text{\textipa{D}}}
\newcommand{\ethz}{\text{\normalfont \textipa{Q}}}
\newcommand{\fairesearch}{\normalfont \text{\textipa{@}}}

\author{Tiago Pimentel$^{\ucambridge}$ Josef Valvoda$^{\ucambridge}$ Rowan Hall Maudslay$^{\ucambridge}$ Ran Zmigrod$^{\ucambridge}$ \\
\textbf{Adina Williams$^{\fairesearch}$ Ryan Cotterell$^{\ucambridge,\ethz}$} \\
  $^{\ucambridge}$University of Cambridge~\;~$^{\fairesearch}$Facebook AI Research~\;~%
  $^{\ethz}$ETH Z\"{u}rich \\
  \texttt{tp472@cam.ac.uk},~\;~ \texttt{jv406@cam.ac.uk},~\;~ \texttt{rh635@cam.ac.uk}, \\
  \texttt{rz279@cam.ac.uk},~\;~ \texttt{adinawilliams@fb.com},~\;~ \texttt{ryan.cotterell@inf.ethz.ch}
}
```

## Use booktabs

http://tug.ctan.org/macros/latex/contrib/booktabs/booktabs.pdf
## Use cref

```latex
\usepackage{cleveref}
\crefname{section}{\S}{\S\S}
\Crefname{section}{\S}{\S\S}
\crefname{table}{Table}{Tables}
\crefname{figure}{Figure}{Figures}
\crefname{algorithm}{Algorithm}{}
\crefname{equation}{eq.}{}
\crefname{appendix}{App.}{}
\crefformat{section}{\S#2#1#3}  

The results of our method are shown in \cref{table:results}.
```

## Use todonotes
```latex
\usepackage{todonotes}
\makeatletter
\newcommand*\iftodonotes{\if@todonotes@disabled\expandafter\@secondoftwo\else\expandafter\@firstoftwo\fi} 
\makeatother
\newcommand{\noindentaftertodo}{\iftodonotes{\noindent}{}}
% Note that these macros accept optional arguments such as size=\small, bordercolor=red, and so on.  Capitalized versions are inline paragraphs instead of margin notes.
\newcommand{\fixme}[2][]{\todo[color=yellow,size=\scriptsize,fancyline,caption={},#1]{#2}} % to mark stuff that you know is missing or wrong when you write the text
\newcommand{\note}[4][]{\todo[author=#2,color=#3,size=\scriptsize,fancyline,caption={},#1]{#4}} % default note settings, used by macros below.

\newcommand{\ryan}[2][]{\note[#1]{ryan}{purple!40}{#2}}
See the following equation.\ryan{There is a mistake in ...}

```

##  How to format your bibliography
Please copy all citations from the [ACL Anthology](https://aclanthology.org/)
* Make sure all middle initials have periods.
* Make sure all things that need to remain capitalized are protected (in {}), e.g. language names or names of people (especially in titles)
* Make sure the capitalized is correct on all booktitles


## Equal Contribution Authors
Format authorship like this:

```latex
\author{Author1Name$\thanks{\quad Equal contribution}^{\ , \affiliation1}$~\;~Author2Name$\footnotemark[1]^{\ ,\affiliation2}$}
```

## Uploading to arXiv
Comment strip and remove unused files with command line tool arxiv-collector:

```bash
arxiv-collector main.tex 
```

This creates a zip-file that can be uploaded to arxiv directly and contains all the necessary files without comments and unused files.

You can download the tool here https://github.com/djsutherland/arxiv-collector or install it with `pip install arxiv-collector`. One can even add it to overleaf directly according to the docs!

Alternative tool: https://github.com/google-research/arxiv-latex-cleaner

## Numbering Equations

Taken from the CVPR style guide: “Please number all of your sections and displayed equations. It is important for readers to be able to refer to any particular equation. Just because you didn’t refer to it in the text doesn’t mean some future reader might not need to refer to it. It is cumbersome to have to use circumlocutions like “the equation second from the top of page 3 column 1”. (Note that the ruler will not be present in the final copy, so is not an alternative to equation numbers). All authors will benefit from reading Mermin’s description of how to write mathematics: http://www.pamitc.org/documents/mermin.pdf.”


## Special Symbols
* IPA symbols in Table 2 of https://www.tug.org/TUGboat/tb17-2/tb51rei.pdf. 
* Vietnamese letters: 
```latex
\usepackage[T5,T1]{fontenc}
```

## Miscellaneous

* Use ```\!``` before `\left(`, to remove the spacing between the function name and `(`. E.g. `\func\!\left( x \right)`.
* Use `\colon` instead of `:` when defining a mapping.


