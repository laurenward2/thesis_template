# Dissertation Template

This dissertation template is a modification of the [Bj\"orn Brandenburg template](https://www.cs.unc.edu/~bbb/).
Some minor adjustments were made to account for the inexplicable rule changes of UNC since 2013.

It was used as recently as April, 2022 to successfully get a dissertation past the grad school moderators.

## Structure

The template is structured into separate files, in distinct directories, as follows:

- **common** directory for preamble, macros, layout, and defining reference style
- **frontmatter** directory defining the style of title page, copyright page, acknowledgements (optional), dedication (optional), preface (optional), then the table of contents, list of figures, list of tables, and list of abbreviations and symbols.  Edit the `pages.tex` file to include/remove the optional pieces as desired
- **chapterX** each of these directories holds the text source and other files for each chapter
- **conclusion** the final chapter
- **appendix** example appendices, showing how they work


## Things to do

- in `common/macros.tex`, at the very top, change definitions for `\myname`, `myyear`, `myadvisor`, and `\mytitle`
- in `common/macros.tex`, add any custom `\newcommand` definitions used for your dissertation
- replace the abstract text in `frontmatter/abstract.tex`
- replace the symbols and abbreviation lists (if relevant) in `frontmatter/abbreviations.tex` and `frontmatter/symbols.tex`
- in `frontmatter/pages.tex`, comment-out the `include{}` directives for any optional sections you don't want (acknowledgement, dedication, preface)
- in `frontmatter/acknowledgement.tex`, replace the text with your own
- in `frontmatter/dedication.tex`, replace the dedication with your own.  Also remove the epigraph at the bottom, or use your own (I'm not sure how kosher epigraphs in dedication are)
- in `frontmatter/preface.tex`, replace the preface with your own
- in the chapter folders, include your Tex files, and any relevant figures or tables.  These show examples of how to work with figures and tables using the directory structure.
- additional chapters can be added to `diss.tex` as needed.

As you add more files, if you plan to use your own git repository, you should update the .gitignore file to manually include all new files.  This .gitignore file is setup to ignore everything unless it is explicitly included.  This means the local directory can be cluttered up without cluttering the remote repository.

## `makethesis`

The simple script `makethesis` runs pdflatex twice, copies over your local copy of `master.bib`, and then runs `pdflatex` twice.  This will update all resolvable citations and references in the paper.

You must edit this to point to your local copy of `master.bib`.  If you plan to use your own bibtex file, then you can erase the `cp ...` line and just include your bibtex file in the repository.

## Ongoing issues

- "Footnotes must be aligned with left margin."  They look aligned to me, but the grad school disagrees.  I don't remember how I got that past them, but eventually I did.

- The page numbers use a cheap hack to get centered numbers.  However, this results in the pdf displaying the page numbers including "-0.25in".   This problem occurs because the left margin is set to 1.25" for printing, and "centered" page numbers are centered relative to the text and not the margin; so page numbers must be manually shifted more to the left, and I did that by including `\hspace{-0.25in}` in the page-number definition (in `frontmatter/pages.tex`).  I think fancyheadr package could fix the issue.