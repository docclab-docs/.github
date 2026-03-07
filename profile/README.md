# Welcome to docclab-docs

This README describes conventions for repositories and documents in this organization.  

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

Name all image files as `figure_$1.*`. where $1 and `*` are wildcards depending on the content the file is describing and the filetype.  Include wrapper tex files for figures and name them `figure_$1.tex` where $1 is the same name you used for the image file.  

Name all tables `table_*.tex` where `*` is a wildcard depending on the content the table decribes.  

Place all tables and image files and image file wrappers in the appropriate `tables/` or `figures/` subdirectories. 

## Branching conventions

All new work should be done on the main branch. Checkpoint work for a submission, ArXiv, or final copy by creating a new branch. Name the branch `<venue><year>\_(submit|final|arxiv-vX)`.  So, a valid branch might be `ispass26_submit`.  

If a paper is rejected, stop using the current repo. Create a new repo for the next submission.  In such cases, the initial contents of the new repo and the final contents of the main branch of the previous repo will be identical. 

## Spell checking LaTeX files

Install `ispell` via Homebrew:

```
brew install ispell
```

To spell check a `.tex` file, use the `-t` flag to enable TeX mode (which tells `ispell` to skip LaTeX commands and focus on prose):

```
ispell -t <filename>.tex
```
To spell check all files in a directory, use wildcards. Do not forget to spell check the main tex file, any place you defined commands, and files within the `tables/` and `figures/` directories!

```
ispell -t *.tex
```

`ispell` will step through each unrecognised word interactively.  For each word you can accept it, add it to your personal dictionary, or replace it.

## Checking for embedded fonts

`pdffonts` is part of the `poppler` package.  Install it via Homebrew:

```
brew install poppler
```

To check that all fonts are embedded in your compiled paper:

```
pdffonts <paper_name>.pdf
```

The output lists every font used.  Check the `emb` column — every font should show `yes`.  A `no` means that font is not embedded and may not render correctly on other machines or when submitted.

PDF figures should also have their fonts embedded.  To check a figure:

```
pdffonts figure_<name>.pdf
```

Run this on each `.pdf` file in your `figures/` directory before submission.
