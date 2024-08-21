# Template for a (PhD) thesis

## Overview of files
- `main.pdf`
  Can be found under *[Releases](https://github.com/tomdjong/thesis-template/releases/latest)*. Showcases the template
- `macros.sty`
  Add your personal macros here
- `packages.sty`
  Packages used and their options.

  **NB**. The PDF metadata is set in this file. Be sure to update it.
- `references.bib`
  For the bibliography, note that some examples showcasing
  `biblatex`'s capabilities are provided.
- `main.tex`
  The root document that imports the chapters

### Front matter
- `titlepage.tex`
  You can tweak the title page here
- `abstract.tex`
- `acknowledgements.tex`

### Main matter
- `chapter.tex`
  Showcases the coloured math environments, link colours, theorem numbering, as
  well as the commands for inserting symbols and terms in their respective
  indices
- `conclusion.tex`

## Coloured environments

The coloured/shaded (math) environments can be toggled on/off (globally) using a
boolean in `main.tex`.

## Overfull `\hbox` warnings

The (coloured) environments generate overfull `\hbox` warnings. This is known,
as commented on in `main.tex`:
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
