This repo is an initial attempt at converting the OSCA introduction sub-book to quarto. A few minor changes (listed below) is enough to get 90% of the way there and produce a decent looking render. There are some broken parts here and there. Figuring out the last 10% and how to automate the changes I did here by hand for the other sub-books will be more difficult.

# Changes implemented 

Changes necessary to get the document to render:

* `rename "s/Rmd$/qmd/" *.Rmd`
* edit chunk options to match qmd format. This usually involves 
     1) moving into the chunk
     2) adding #| to the start
     3) changing an = to a :
     4) possibly adding a space after the colon
     5) possibly changing TRUE/FALSE to true/false
     6) possibly changing the option name's format e.g. fig.cap -> fig-cap
     7) possibly remove BiocStyle-specific options for now e.g. fig.wide (which is NOT the same thing as fig.width)
     
* fix incompatible YAML e.g. `link-citations: yes` -> `link-citations: true`
* prefix the labels of figure-producing chunks with "fig-" so that quarto can easily reference them with @fig-sce
* remove title from yml of index.qmd
* delete lines with `r link(...)` cross-referencing magic for now
* copy DESCRIPTION from OSCA.intro so that `rebook::openingDetails()` can find the opening details like author info
* add `{.unnumbered}` to the first top level heading in index.qmd so that it doesn't get a chapter number
* ignore multi-book structure for now

# Rendering & output

Clone this repo, `cd` into it, then run `quarto render` (or `quarto preview` if you've previously rendered). A rendered version can be seen [here](https://ccb.connect.hms.harvard.edu/osca_intro_qmd/).

# Future steps

* Reincorporate the deleted `book` / `rebook` magic
* Investigate using the [quarto freeze](https://quarto.org/docs/projects/code-execution.html#freeze) option (sort of like chapter-level caching instead of knitr chunk-level caching) as an alternative way of managing the execution if book/rebook turns out to be non-viable.
* Utilize fancy quarto features like switchable themes
