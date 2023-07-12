# Style Guide

The most often used typesetting system in Rycolab is LaTeX. Major conferences such as ACL, EMNLP, and NAACL offer their own LaTeX template files, e.g. https://2023.aclweb.org/calls/style_and_formatting/. 
Cloning the template files from the conference website into [Overleaf](https://www.overleaf.com/) is a good starting point. However, there are some additional things to keep in mind when writing a paper in Rycolab.



## Use cref

```latex
\usepackage{cleveref}
\crefname{section}{\S}{\S\S} % {singular}{plural}
\Crefname{section}{\S}{\S\S} % \Cref{...} for capitalized version
\crefname{table}{Table}{Tables}
\crefname{figure}{Figure}{Figures}
\crefname{algorithm}{Algorithm}{}
\crefname{equation}{eq.}{}
\crefname{appendix}{App.}{}
\crefformat{section}{\S#2#1#3}  
% make sure to add \label{table:results} to the table.
The results of our method are shown in \cref{table:results}.
```

## Use todonotes
We use the [todonotes](https://ctan.org/pkg/todonotes) package to add comments and notes.
There are two styles of notes: margin notes and inline notes: margin notes are added to the margin of the page, while inline notes are added to the text. Conventionally, margin notes are defined as macros with lowercase names (e.g. `\ryan`), while inline notes are defined as macros with uppercase names (e.g. `\Ryan`). You can find a [color](#eth-colors) that you like for your todonotes.
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
\newcommand{\Ryan}[2][]{\ryan[inline,#1]{#2}\noindentaftertodo}

See the following equation.\ryan{There is a mistake in ...}
\Ryan{An inline note.}
```

## Use macros
It is often a good idea to define macros for frequently used symbols. This makes it easier to for proofreading or changing notations later on. 
The following example defines some macros. 
```latex
\definecolor{ETHPetrol}{RGB}{0,120,148} % green/blue

\newtoggle{color-macro}
\settoggle{color-macro}{true} % set to false to disable color macros

\iftoggle{color-macro}{
\colorlet{MacroColor}{ETHPetrol}
}{
\colorlet{MacroColor}{black}
}

%%%%%% The super-macro:
% While editing---it will make all the macros blue
\newcommand{\mymacro}[1]{{\color{MacroColor} #1}}
% For publishing---it will remove the custom color (just setting it to black is not enough, since the black would override any custom colors you would have in the main text).
% \newcommand{\mymacro}[1]{{#1}}

\newcommand{\bh}{\mymacro{\mathbf{h}}}
\newcommand{\bhi}{\mymacro{\mathbf{h}_i}}
\newcommand{\bt}{\mymacro{\boldsymbol{t}}}
\newcommand{\bw}{\mymacro{\boldsymbol{w}}}
```

If there are a lot of macros, it is a good idea to put them in a separate file, e.g. `macros.tex`, and include them in the main file with `\input{macros}`.

You can use the [ICLR template](https://github.com/ICLR/Master-Template/blob/master/math_commands.tex) for some common macros, e.g., vectors and matrices.

## Use thmtools for theorems
```latex
\usepackage{thmtools}
\usepackage{thm-restate} % to restate theorems
% https://ctan.math.illinois.edu/macros/latex/contrib/apxproof/apxproof.pdf
\usepackage{apxproof}
\declaretheorem{theorem}
\declaretheorem{lemma}
\newtheorem{der}{Derivation}
\newtheorem{cor}{Corollary}
\newtheorem{lemma}{Lemma}
\newtheorem{prop}{Proposition}
\newtheorem{myexample}{Example}
\newtheorem{assumption}{Assumption}
\newtheorem{transformation}{Transformation}
\newtheorem{remark}{Remark}
\newtheorem{defin}{Definition}
\theoremstyle{definition}

\usepackage{cleveref} % numbering theorems
\crefname{thm}{Theorem}{Theorems}
\crefname{defin}{Def.}{Defs.}

\begin{theorem} \label{thm:newthm}
    This is a theorem.
\end{theorem}
```

## Use booktabs

http://tug.ctan.org/macros/latex/contrib/booktabs/booktabs.pdf

## Numbering Equations

Taken from the CVPR style guide: “Please number all of your sections and displayed equations. It is important for readers to be able to refer to any particular equation. Just because you didn’t refer to it in the text doesn’t mean some future readers might not need to refer to it. It is cumbersome to have to use circumlocutions like “the equation second from the top of page 3 column 1”. (Note that the ruler will not be present in the final copy, so is not an alternative to equation numbers). All authors will benefit from reading Mermin’s description of how to write mathematics: http://www.pamitc.org/documents/mermin.pdf.”


## Special Symbols
* IPA symbols in Table 2 of https://www.tug.org/TUGboat/tb17-2/tb51rei.pdf. 
* To support Vietnamese letters: 
```latex
\usepackage[T5,T1]{fontenc}
```

### Emoji
Emojis can be fun to include in papers, for example for author affiliations, however, using them with the standard `pdflatex` compiler is not straightforward, but it is possible.
To be able to use them, do the following:
1. Copy the `emoji.sty` file from [here](https://github.com/henningpohl/latex-emoji/blob/master/emoji.sty.TEMPLATE) into the root of your Overleaf project.
2. Include the package using `\usepackage{emoji}`.
3. Create an `emojis` folder in your project and upload the PNGs of the emojis you want to use into the folder.
4. Add an emoji in the file `example.png` to text using `\emoji[emojis]{example}`.

##  How to format your bibliography
Please copy all citations from the [ACL Anthology](https://aclanthology.org/)
* Make sure all middle initials have periods.
* Make sure all things that need to remain capitalized are protected (in {}), e.g. language names or names of people (especially in titles)
* Make sure the capitalization is correct on all book titles


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

To use the [ETH logo](../logo/ethz-logo.png) as an affiliation, use the following code:
```latex
\author{AA AA\thanks{\hspace{0.5em}Equal contribution.} \qquad BB BB\footnote[1]{} \qquad CC CC \\
\setlength{\fboxsep}{2.5pt}%
\setlength{\fboxrule}{2.5pt}%
\fcolorbox{white}{white}{
    $\{$\texttt{\href{mailto:aa@inf.ethz.ch}{aa.aa}, }\texttt{\href{mailto:bb@inf.ethz.ch}{bb.bb}, }\texttt{\href{mailto:cc@inf.ethz.ch}{cc.cc}}$\}$\texttt{@inf.ethz.ch}
} \\
    {%
\setlength{\fboxsep}{2.5pt}%
\setlength{\fboxrule}{2.5pt}%
\fcolorbox{white}{white}{\includegraphics[width=.15\linewidth]{ethz-logo.png}}
}}
```


### Equal Contribution Authors
Format authorship like this:

```latex
\author{Author1Name$\thanks{\quad Equal contribution}^{\ , \affiliation1}$~\;~Author2Name$\footnotemark[1]^{\ ,\affiliation2}$}
```

## Uploading to arXiv
Comment strip and remove unused files with the command line tool arxiv-collector:

```bash
arxiv-collector main.tex 
```

This creates a zip file that can be uploaded to Arxiv directly and contains all the necessary files without comments and unused files.

You can download the tool [here](https://github.com/djsutherland/arxiv-collector) or install it with `pip install arxiv-collector`. According to the docs, one can even add it to Overleaf directly!

Alternative tool: https://github.com/google-research/arxiv-latex-cleaner


## Tips
* Use ```\!``` before `\left(`, to remove the spacing between the function name and `(`. E.g. `\func\!\left( x \right)`.
* Use `\colon` instead of `:` when defining a mapping.

## Miscellaneous
### ETH colors
https://ethz.ch/staffnet/en/service/communication/corporate-design/farbe.html
```latex 
\definecolor{ETHBlue}{RGB}{33,92,175} % blue
\definecolor{ETHGreen}{RGB}{98,115,19} % green
\definecolor{ETHPurpleDark}{RGB}{140,10,89} % purple
\definecolor{ETHPurple}{RGB}{163,7,116} % purple
\definecolor{ETHGray}{RGB}{111,111,111} % gray
\definecolor{ETHRed}{RGB}{183,53,45} % red
\definecolor{ETHPetrol}{RGB}{0,120,148} % green/blue
\definecolor{ETHBronze}{RGB}{142,103,19} % bronze
```
### ETH logos
https://ethz.ch/staffnet/en/service/communication/corporate-design/logo.html

