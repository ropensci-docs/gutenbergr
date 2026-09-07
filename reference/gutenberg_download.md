# Download one or more works using a Project Gutenberg ID

Download one or more works by their Project Gutenberg IDs into a data
frame with one row per line per work. This can be used to download a
single work of interest or multiple at a time. You can look up the
Gutenberg IDs of a work using
[`gutenberg_works()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_works.md)
or the
[gutenberg_metadata](https://docs.ropensci.org/gutenbergr/reference/gutenberg_metadata.md)
dataset.

## Usage

``` r
gutenberg_download(
  gutenberg_id,
  mirror = gutenberg_get_mirror(verbose = verbose),
  strip = TRUE,
  meta_fields = character(),
  verbose = TRUE,
  use_cache = TRUE
)
```

## Arguments

- gutenberg_id:

  A vector of Project Gutenberg IDs, or a data frame containing a
  `gutenberg_id` column, such as from the results of
  [`gutenberg_works()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_works.md).

- mirror:

  A mirror URL to retrieve the books from. By default uses the mirror
  from
  [`gutenberg_get_mirror()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_get_mirror.md).

- strip:

  Whether to strip suspected headers and footers using
  [`gutenberg_strip()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_strip.md).

- meta_fields:

  Additional fields describing each book, such as `title` and `author`,
  to add from
  [gutenberg_metadata](https://docs.ropensci.org/gutenbergr/reference/gutenberg_metadata.md).

- verbose:

  Whether to show messages about the Project Gutenberg mirror that was
  chosen.

- use_cache:

  Whether to use caching. Defaults to `TRUE`.

  - See
    [`gutenberg_cache_set()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_cache_set.md)
    for details on configuring caching.

  - See
    [`gutenberg_cache_dir()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_cache_dir.md)
    to check your current cache location.

  - The files in the cache are `.rds` files that have already been
    processed into a `tbl_df`.

## Value

A two column `tbl_df` (see
[`tibble::tibble()`](https://tibble.tidyverse.org/reference/tibble.html))
with one row for each line of the text or texts, with columns:

- gutenberg_id:

  Integer column with the Project Gutenberg ID of each text

- text:

  A character vector of lines of text

## Examples

``` r
if (FALSE) { # interactive()
# Download "The Count of Monte Cristo"
gutenberg_download(1184)

# Download two books: "Wuthering Heights" and "Jane Eyre"
books <- gutenberg_download(c(768, 1260), meta_fields = "title")
books
dplyr::count(books, title)

# Download all books from Jane Austen
austen <- gutenberg_works(author == "Austen, Jane") |>
  gutenberg_download(meta_fields = "title")
austen
dplyr::count(austen, title)
}
```
