# latex3html

This is a modified version of Luca's
[LaTeX2WP](https://lucatrevisan.wordpress.com/latex-to-wordpress/).
Be warned; the modifications have not been made in a principled way...

Main changes are:
- Math rendered with MathJax
- Footnotes (as sidenotes)
- Bibliography support

Sample usage:

First, run pdflatex and bibtex on the source .tex file (in this case,
example-fastjl/fastjl.tex). This will generate the .bbl file.

Then, convert to html with:
```
python latex3html.py --bbl fastjl.bbl fastjl.tex
```

If you don't pass the .bbl, citations will remain as \cite.

Full usage:
```
usage: latex3html.py [-h] [--bbl BBL] [--outfile OUTFILE] [--bodyonly]
                     inputfile

turn LaTeX to HTML+MathJax

positional arguments:
  inputfile          LaTeX source

optional arguments:
  -h, --help         show this help message and exit
  --bbl BBL          BibTeX-compiled .bbl file
  --outfile OUTFILE  custom output filename
  --bodyonly         output only the HTML body, and no titleblock (useful for
                     embedding in a blog)
```

# Known Bugs

- Bibliography rendering somewhat broken with special characters
(see http://learningwitherrors.org/2016/06/03/small-bias/).

- Nesting \cite within a theorem/proof name doesn't work.
