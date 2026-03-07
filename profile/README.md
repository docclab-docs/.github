# Welcome to docclab-docs

This README describes conventions for repositories in this organization.  

## Naming conventions 

Please name the repository using the following format: 

  (Paper|Proposal)\_<Project\_theme>\_<Proposal\_venue|Paper\_venue>

In the above `<>` denotes placeholders for text you should replace with appropriate names.  `|` indicates an OR relationship. 

A valid repo for a conference submission might be `paper_contention_ispass26`.  It's a `paper`, `contention` is the project theme, and `ispass26` is the venue.  A valid repo for a proposal submission might be `proposal_cacti_nsf26`.  It's a `proposal`, `cacti` is the theme, and `nsf26` is the venue.      

## Directory structure within repos 

Directory structures within repos should resemble

```text
<repo name>/
├── submit/
│   └── figures/
│   └── tables/
│   └── sections/
├── reviews/
│   ├── reviews_<proposal_venue|paper_venue>.(txt|md)
│   └── rebuttal_<proposal_venue|paper_venue>.(txt|md)
├── <any_extra_directories>/
├── .gitignore
└── Makefile
```

`figures` and `tables` should include both image files (e.g., `.pdf`, `.graffle`) and wrapper text. `<extra directories>` may be anything, for example directories containing experimental results. Please include a `Makefile` so that the paper can be compiled with `Make`.

## File naming conventions

Name all image files as `figure_$1.*`. where $1 `*` is a wildcard depending on the content the file is describing and thefiletype.  Include wrapper tex files for figures and name them `figure_$1.tex` where $1 is the same name you used for the image file.  

Name all tables `table_*.tex` where `*` is a wildcard depending on the content the table decribes.  

Place all tables and image files and image file wrappers in the appropriate `tables/` or `figures/` subdirectories. 

## Branching conventions

After submission, create a branch named `<paper\_venue|proposal\_venue>_submit`.  You can then continue working in the repo on `main` to improve the submission until you get the accept/reject notification.

**If the work is accepted**, create a final branch named `<paper\_venue|proposal\_venue>_final` from the accepted version.

**If the work is rejected**, stop using the current repo.  Create a new repo for the next submission.

## Spell checking LaTeX files

Install `ispell` via Homebrew:

```
brew install ispell
```

To spell check a `.tex` file, use the `-t` flag to enable TeX mode (which tells `ispell` to skip LaTeX commands and focus on prose):

```
ispell -t <filename>.tex
```

`ispell` will step through each unrecognised word interactively.  For each word you can accept it, add it to your personal dictionary, or replace it.

## Checking for embedded fonts

`pdffonts` is part of the `poppler` package.  Install it via Homebrew:

```
brew install poppler
```

To check that all fonts are embedded in your compiled paper:

```
pdffonts paper.pdf
```

The output lists every font used.  Check the `emb` column — every font should show `yes`.  A `no` means that font is not embedded and may not render correctly on other machines or when submitted.

PDF figures should also have their fonts embedded.  To check a figure:

```
pdffonts figure_<name>.pdf
```

Run this on each `.pdf` file in your `figures/` directory before submission.
