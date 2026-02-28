# Welcome to docclab-docs

This README describes conventions for repositories in this organization.  

## Naming conventions 

Please name the repository using the following format: 

(Paper|Proposal)_<Project_theme>_<Proposal_venue|Paper_venue>

In the above `<>` denotes placeholders for text you should replace with appropriate names.  `|` indicates an OR relationship. 

A valid repo for a conference submission might be `paper_contention_ispass26`.  It's a `paper`, `contention` is the project theme, and `ispass26` is the venue.  A valid repo for a proposal submission might be `proposal_cacti_nsf26`.  It's a `proposal`, `cacti` is the theme, and `nsf26` is the venue.      

## Directory structure within repos 

Diretory structures within repos should resemble 

```text
<repo name>/
├── submit/
│   └── figures/
|   └── tables/
|   └── sections/
├── reviews/
│   ├── reviews_<confname>.py
│   └── rebuttal_<confname>.py
├── <any_extra_directories>/
│   ├── test_main.py
│   └── test_utils.py
├── .gitignore
└── Makefile
```

`figures` and `tables` should include both image fiels (e.g., `.pdf`, .`graffle`) and wrapper text. `<extra directories>` may be anything, for example directories containing experimental results. Please include a `Makefile` so that the paper can be compiled with `Make`.

## File naming conventions

Name all image files as `figure_$1.*`. where $1 `*` is a wildcard depending on the content the file is describing and thefiletype.  Include wrapper tex files for figures and name them `figure_$1.tex` where $1 is the same name you used for the image file.  

Name all tables `table_*.tex` where `*` is a wildcard dependong on the content the table decribes.  

Place all tables and image files and image file wrappers in the appropriate `tables/` or `figures/` subdirectories. 

## Tagging conventions 

After submission, tag the repo with `<paper_venue|proposal_venue>_submit`.  You can then continue working in the repo to improve the submission until you get teh accept/reject notification.  

**If the work is accepted**, you may continue working in the repo.  Tag the final version with `<paper_venue|proposal_venue>_final`.  

**If the work is rejected**, stop using the current repo.  Create a new repo for the next submission.  

## Experimental best practices





