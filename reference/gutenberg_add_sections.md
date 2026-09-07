# Add a section column to a Gutenberg tibble

Identifies section markers (chapters, cantos, letters, etc.) in Project
Gutenberg texts and adds a column indicating which section each line
belongs to. Sections are forward-filled, so all text between markers
belongs to the previous section.

## Usage

``` r
gutenberg_add_sections(
  data,
  pattern,
  ignore_case = TRUE,
  format_fn = NULL,
  group_by = "auto",
  section_col = "section"
)
```

## Arguments

- data:

  A [tibble::tibble](https://tibble.tidyverse.org/reference/tibble.html)
  with a `text` column containing the text to analyze. Typically `data`
  should be piped from
  [gutenberg_download](https://docs.ropensci.org/gutenbergr/reference/gutenberg_download.md)
  and contain a `gutenberg_id` column, but this is not required.

- pattern:

  A regex pattern to identify headers. Must match the specific
  formatting of your book. See Details and Examples for common patterns.

- ignore_case:

  Logical; should pattern matching be case-insensitive? Default is
  `TRUE`.

- format_fn:

  Optional function to format section text. Receives the matched text
  and returns formatted text. Common options include
  [stringr::str_to_title](https://stringr.tidyverse.org/reference/case.html)
  and
  [stringr::str_to_upper](https://stringr.tidyverse.org/reference/case.html)
  but a custom function can also be provided.

- group_by:

  Character vector of column names to group by before filling sections,
  or `NULL` to disable grouping. Defaults to `"auto"`, which
  automatically uses `"gutenberg_id"` if that column exists. Set to
  `NULL` to treat the entire dataset as one document, or specify custom
  column names for grouping (e.g., `group_by = "book_title"`).

- section_col:

  Character string specifying the name of the section column to create.
  Defaults to `"section"`.

## Value

A [tibble::tibble](https://tibble.tidyverse.org/reference/tibble.html)
with an added column named according to `section_col`, containing the
section marker for each row. Rows before the first section marker will
have `NA`.

## Details

### Common Section Patterns for Project Gutenberg Books

Different books use different formatting for their section markers. Here
are patterns for common formats:

- Chapters with Roman numerals: `"^Chapter [IVXLCDM]+"`

- Chapters with Arabic numerals: `"^Chapter [0-9]+"`

- Plays with both Roman and Arabic numerals:
  `"^(ACT|SCENE) [IVXLCDM0-9]+"`

- Books (e.g., *Paradise Lost*): `"^BOOK [IVXLCDM]+"`

- Cantos (e.g., *Dante's Inferno*): `"^CANTO [IVXLCDM]+"`

- Staves (e.g., *A Christmas Carol*): `"^STAVE [IVXLCDM]+"`

- Multiple formats (e.g., *Frankenstein*): `"^(Letter|Chapter) [0-9]+"`

Use
[`gutenberg_works()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_works.md)
to search for books and examine a few lines with
[`gutenberg_download()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_download.md)
to determine the exact format before writing your pattern.

## Examples

``` r
if (FALSE) { # interactive()
# Dante's "Inferno" - Cantos with Roman numerals
inferno <- gutenberg_download(1001) |>
  gutenberg_add_sections(pattern = "^CANTO [IVXLCDM]+")

# Mary Shelley's "Frankenstein"
# Letters and Chapters with Arabic numerals, normalized to title case
frankenstein <- gutenberg_download(84) |>
  gutenberg_add_sections(
    pattern = "^(Letter|Chapter) [0-9]+",
    format_fn = stringr::str_to_title
  )

# Classic Brontë sisters' works
# Chapters with Roman numerals, with trailing periods removed from section text
# Consider using `options(gutenbergr_cache_type = "persistent")`
# to prevent redownloading in the future.
bronte_sisters <- gutenberg_download(
  c(
    767,  # "Agnes Grey" by Anne Brontë
    768,  # "Wuthering Heights" by Emily Brontë
    969,  # "The Tenant of Wildfell Hall" by Anne Brontë
    1260, # "Jane Eyre" by Charlotte Brontë
    9182, # "Villette" by Charlotte Brontë
  ),
  meta_fields = c("author", "title")
) |>
  gutenberg_add_sections(
    pattern = "^\\s*CHAPTER [IVXLCDM]+",
    format_fn = function(x) str_remove(x, "\\.$")
  )

# Leo Tolstoy's "War and Peace"
# Add two custom named columns for hierarchical sections
war_and_peace <- gutenberg_download(2600) |>
  gutenberg_add_sections(
    pattern = "^BOOK [A-Z]+",
    section_col = "book"
  ) |>
 gutenberg_add_sections(
   pattern = "^CHAPTER [IVXLCDM]+",
   section_col = "chapter"
 )
}
```
