# Gutenberg metadata about each work

Selected fields of metadata about each of the Project Gutenberg works.

## Usage

``` r
data(gutenberg_metadata)
```

## Format

A
[`tibble::tibble()`](https://tibble.tidyverse.org/reference/tibble.html)
with one row for each work in Project Gutenberg and the following
columns:

- gutenberg_id:

  Numeric ID, used to retrieve works from Project Gutenberg

- title:

  Title

- author:

  Author, if a single one given. Given as last name first (e.g. "Doyle,
  Arthur Conan")

- gutenberg_author_id:

  Project Gutenberg author ID

- language:

  Language ISO 639 code, separated by / if multiple. Two letter code if
  one exists, otherwise three letter. See
  <https://en.wikipedia.org/wiki/List_of_ISO_639-2_codes>

- gutenberg_bookshelf:

  Which collection or collections this is found in, separated by / if
  multiple

- rights:

  Generally one of three options: "Public domain in the USA." (the most
  common by far), "Copyrighted. Read the copyright notice inside this
  book for details.", or "None"

- has_text:

  Whether there is a file containing digits followed by `.txt` in
  Project Gutenberg for this record (as opposed to, for example,
  audiobooks). If not, cannot be retrieved with
  [`gutenberg_download()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_download.md)

## Details

To find the date on which this metadata was last updated, run
`attr(gutenberg_metadata, "date_updated")`.

## See also

[`gutenberg_works()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_works.md),
[gutenberg_authors](https://docs.ropensci.org/gutenbergr/reference/gutenberg_authors.md),
[gutenberg_subjects](https://docs.ropensci.org/gutenbergr/reference/gutenberg_subjects.md)

## Examples

``` r
if (FALSE) { # interactive()

library(dplyr)
library(stringr)

gutenberg_metadata

gutenberg_metadata |>
  count(author, sort = TRUE)

# Look for Shakespeare, excluding collections (containing "Works") and
# translations
shakespeare_metadata <- gutenberg_metadata |>
  filter(
    author == "Shakespeare, William",
    language == "en",
    !str_detect(title, "Works"),
    has_text,
    !str_detect(rights, "Copyright")
  ) |>
  distinct(title)

# Note that the gutenberg_works() function filters for English
# non-copyrighted works and does de-duplication by default:

shakespeare_metadata2 <- gutenberg_works(
  author == "Shakespeare, William",
  !str_detect(title, "Works")
)

# See date last updated
attr(gutenberg_metadata, "date_updated")
}
```
