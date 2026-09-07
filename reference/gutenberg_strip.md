# Strip header and footer content from a Project Gutenberg book

Strip header and footer content from a Project Gutenberg book. This is
based on formatting heuristics (regular expression guesses), so it may
not be perfect.

## Usage

``` r
gutenberg_strip(text)
```

## Arguments

- text:

  A character vector where each element is a line of a book.

## Value

A character vector with Project Gutenberg headers and footers removed.

## Details

This function identifies the Project Gutenberg "start" and "end"
markers. It also attempts to strip out initial metadata paragraphs (such
as "Produced by...", "Transcribed from...", etc.).

Note that this will **not** strip:

- Tables of contents

- Prologues or introductions

- Other author-written text that appears at the start of a book

## Examples

``` r
if (FALSE) { # interactive()
library(dplyr)

# Download a book without stripping to see the headers
book <- gutenberg_works(title == "Pride and Prejudice") |>
  gutenberg_download(strip = FALSE)

# Look at the raw header and footer
head(book$text, 20)
tail(book$text, 20)

# Manually strip the text
text_stripped <- gutenberg_strip(book$text)

# Check the cleaned results
head(text_stripped, 10)
tail(text_stripped, 10)
}
```
