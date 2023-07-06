# Rycolab BibTeX Etiquette

## A few Notes on the Author's list

If the authors are coming from different institutions/departments, these should be listed in a consistent way (e.g., in the order “institute, department, university”).

The author's list should reference their institutions and email addresses. Superscript numbers are OK for this (however, check that they are in normal font, not bolded - LaTeX can bold them by default - \normalfont can help here), but you can also use something fancier, like emoji.

The **email addresses** should be clustered by the same domains to save space.
For example, email addresses `a@x.com`, `b@x.com`, `c@x.com` should be rendered as `{a, b, c}@x.com`.
In LaTeX, this can be done as follows: 

```latex
$\{$ \texttt{\href{mailto:abc@x.com}{author name}} $\}$\texttt{@x.com}
```

In this case a, b, and c will be clickable and will take one directly to the mail client to send the email.
You should use \texttt for the text in the addresses. If you use the package inconsolata (just load it), the addresses will also be rendered more nicely.

## References

### Where to get the information
Not all sources of BibTeX are equal. As often as possible, try to get the BiBTeX from the original source (NeuriPS, ACL Anthology, IEEE, Springer should have well-formatted BibTeX files).
Nonetheless, the entries are not always correct (90% of them will be correct but Ryan will find 100% of the mistakes) and in case of doubts, check the original publication and fill in the entries yourself.

### Entry Types
BibTeX offers different entry types (see https://www.overleaf.com/learn/latex/Bibliography_management_with_bibtex).
The general rules are:
* `@article` for journal articles,
* `@inproceedings` for conference proceeding articles,
* `@book` for books.
For journal and conference articles, the publisher field should be removed.


### Capitalisation
By default, BibTeX will print the citation titles in lowercase (except for the capitalisation of the first character of the title).
You should watch out for two things:
1. Capitalisation of acronyms, proper nouns (names of particular people, places, things…), words following a colon, and beginnings of a new sentence in titles must be protected by enclosing the capitalised characters in {}.
2. For German citations, the capitalisation of nouns must be protected the same way.


### General Rules/Remarks

1. The .bst file is the style file for BibTeX (like .sty files for LaTeX).
    1. It sets for example that publishers aren't displayed for articles.

2. Remove the abstract entries from the BibTeX fields for better readability.
3. Always try to add a link in the url BibTeX field. This can either be a link to the paper pdf, a link to book information on the publisher’s website or even to a Wikipedia page in the case of a book.
    1. When looking for paper pdfs, prefer ACL Anthology or OpenReview to Arxiv.
    2. Prefer book links to the publisher’s website to Google Books.
4. Make sure the pages field is correct. Some conferences (NeurIPS) do not have pages anymore, but if they do, find them in the original conference paper pdf and check they are correct in the BibTeX field.
5. When modifying the BibTeX fields (copying them from scratch from the sources), make sure you don’t change the entry key so that the references in the main text are not lost.
6. The DOI entries usually don’t end up in the pdf, so you don’t have to worry about them, but they are included in TACL works, so you have to make sure they’re correct in that case.
7. Make sure that special characters are rendered correctly. Encode them properly if there are any.
8. Most often, the middle initials should have periods (British sometimes don't; check in the original publication).
    1. Keep in mind that Ryan does not publish with his middle name.
9. If the booktitle field (for conferences, that is the conference name) or the journal field (for journals) contains the place of the conference/journal, remove it.
10. To be consistent, do not abbreviate names in the author’s list.

