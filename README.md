# Template for a (PhD) thesis

## Overview of files
- `main.pdf`
  Can be found under *[Releases](https://github.com/tomdjong/thesis-template/releases/latest)*. Showcases the template
- `macros.sty`
  Add your personal macros here
- `thesis.sty`
  Packages used and their options.

  **NB**. The PDF metadata is set in this file. Be sure to update it.
- `references.bib`
  For the bibliography, note that some examples showcasing
  `biblatex`'s capabilities are provided.
- `main.tex`
  The root document that imports the chapters

### Front matter
- `titlepage.tex`
  Single title page (prints all data on the title page)
- `titlepages.tex`
  Title page (title, author, degree, and university) and info page with more detail.

  Provides `\titleBg` and `\titleColor` macros to control background image and font colour of title page, respectively; and `\dateInfo`, `\supervisionInfo`, `\citationInfo`, and `\copyrightInfo` macros to supply further detail to be printed on info page (see sample).
- `abstract.tex`
- `acknowledgements.tex`

### Main matter
- `chapter.tex`
  Showcases the coloured math environments, link colours, theorem numbering, as
  well as the commands for inserting symbols and terms in their respective
  indices
- `conclusion.tex`

## Options to the thesis package

The `\usepackage{thesis}` appearing in `main.tex` can be modified with the following options.

### `mathalpha`
The following options, when passed to the `thesis` package, will be passed on to `mathalpha`. See the [`mathalpha` documentation](https://ctan.math.illinois.edu/macros/latex/contrib/mathalpha/doc/mathalpha-doc.pdf).
- `cal=`: Set font for `\mathcal` (e.g. `cal=cm`)
- `frak=`: Set font for `\mathfrak` (e.g. `frak=euler`)
- `scr=`: Set font for `\mathscr` (e.g. `scr=rsfs`)
- `bb=`: Set font for `\mathbb` (e.g. `bb=ams`)

### `ttscale`
By default, the option `ttscale=.75` will be passed to the libertine package, making all `tt` fonts smaller. This can be changed by passing a different `ttscale` to `thesis` (e.g. `ttscale=1.0`).

## Coloured environments

The coloured/shaded (math) environments can be toggled on/off (globally) using a
boolean in `packages.sty`.

## Overfull `\hbox` warnings

The (coloured) environments generate overfull `\hbox` warnings. This is known,
as commented on in `packages.sty`:
```
% LaTeX thinks this is too wide (as becomes clear from the many "Overfull
% \hbox" warnings, but optically it looks spot on.
```

## Index of symbols
The `nomencl` package is used to generate the index of symbols. To set this
package up with `latexmk`, you should add
```
# Custom dependency and function for nomencl package
add_cus_dep( 'nlo', 'nls', 0, 'makenlo2nls' );
sub makenlo2nls {
system( "makeindex -s nomencl.ist -o \"$_[0].nls\" \"$_[0].nlo\"" );
}
```
to your `$HOME/.latexmkrc` as explained on [this StackExchange
post](https://tex.stackexchange.com/questions/105943/latexmk-and-nomencl).
