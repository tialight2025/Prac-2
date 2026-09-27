# Practical 2 — Data Sources and Data Manipulation

This repository is where you'll write up your answers for Practical 2
("Working with Data: Data Sources and Data Manipulation").

## Repository contents

```
.
├── README.md                  <- this file
├── practical2-answers.qmd     <- template: fill in your answers here
└── data/                      <- put the downloaded .csv files here
```

## 1. Get the repository onto your computer

Use this repository as a template for your own personal answers.

(i) Click "Use this template" then "Create a new repository" and follow prompts to create a personal copy of this repo.
(ii) Clone the repo to your local computer with RStudio: **File > New Project > Version Control > Git**
(iii) Follow the prompt and paste your **personal repo**'s URL.

If you're still unsure about this workflow, the relevant chapter of
*Happy Git and GitHub for the useR* walks through it step by step:
<https://happygitwithr.com/usage-intro>.

A few other chapters from that book you'll might find useful over the
course:

- [Install Git](https://happygitwithr.com/install-git) — if Git isn't already set up on your machine
- [Connect to GitHub](https://happygitwithr.com/push-pull-github) — pushing and pulling changes
- [RStudio, Git, GitHub Hell](https://happygitwithr.com/rstudio-git-github) — troubleshooting common setup issues

## 2. Get the data

Download the two `.csv` files linked in the practical instructions on canvas and save
them into the `data/` folder in this repository:

- `data/reg-nurses-dataworld-1998-2020.csv`
- `data/nurse-licenses-ncsbn-2026-01-05.csv`

(Right-click each link → "Save As" / "Download Linked File As", and make sure
they land in `data/`, not your Downloads folder.)

## 3. Install the packages you'll need

Open `practical2-answers.qmd` in RStudio and try running the setup chunk at
the top. If any `library()` call fails with something like
`Error in library(tidyr) : there is no package called 'tidyr'`, install the
missing package(s) from the R console:

```r
install.packages(c("readr", "dplyr", "ggplot2", "tibble", "tidyr"))
```

You only need to do this once per machine. After installation `library()` will
just work to load the package. A few tips:

- Install packages in the **Console**, not inside the `.qmd` file itself.
  If `install.packages()` calls end up inside a code chunk, they'll try to
  reinstall the package every time you render the document, which is slow
  and unnecessary.
- `us_rent_income` (Question 12) ships with the `tidyr` package itself, so
  no extra download is needed — just `library(tidyr)` and
  `data(us_rent_income)`.
- Package documentation and vignettes worth skimming before you start:
  [tibble](https://tibble.tidyverse.org/articles/tibble.html),
  [readr](https://readr.tidyverse.org/articles/readr.html),
  [dplyr](https://dplyr.tidyverse.org/articles/dplyr.html),
  [ggplot2](https://ggplot2.tidyverse.org/articles/ggplot2.html).

## 4. Answer the practical

Work through `practical2-answers.qmd` in order. Write code in the empty
chunks and add your written answers underneath each question heading.

Render regularly (the "Render" button in RStudio, or
`quarto::quarto_render("practical2-answers.qmd")`) to check your document
still runs cleanly from top to bottom. Rendering in a fresh R session
(**Session > Restart R**, then Render) is the best way to check your script
is fully reproducible.

## 5. Commit and push your work

Commit early and often as you go, rather than in one big commit at the end —
it makes it much easier to see your progress and to recover earlier work if
something breaks.

You can use the RStudio console or in terminal.

If you're unsure what a Git error message means, the
[Happy Git](https://happygitwithr.com/) book (or pasting the exact error into
a search engine) is usually the fastest way to unblock yourself — most Git
errors are common and well documented.

## Troubleshooting checklist

- **"Package not found"** → install it from the Console (see step 3).
- **Data not loading** → check the file paths in `read_csv()` match where
  you actually saved the `.csv` files (they should be in `data/`).
- **Document won't render but code runs fine chunk-by-chunk** → try
  Session > Restart R, then Render again; this catches missing `library()`
  calls or objects created out of order.
- **Joining datasets gives unexpected `NA`s** → double check the join key
  (e.g. state names or years) matches exactly between datasets — mismatched
  spelling, capitalisation, or data types (character vs numeric year) are
  the usual culprits.
