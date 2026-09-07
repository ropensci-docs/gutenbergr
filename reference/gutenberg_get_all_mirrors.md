# Get all mirror data from Project Gutenberg

Get all mirror data from <https://www.gutenberg.org/MIRRORS.ALL>. This
only includes mirrors reported to Project Gutenberg and verified to be
relatively stable. For more information on mirroring and getting your
own mirror listed, see <https://www.gutenberg.org/help/mirroring.html>.

## Usage

``` r
gutenberg_get_all_mirrors()
```

## Value

A
[`tibble::tibble()`](https://tibble.tidyverse.org/reference/tibble.html)
of Project Gutenberg mirrors and related data, or `NULL` (invisibly) if
the mirror list cannot be retrieved or parsed.

If a
[`tibble::tibble()`](https://tibble.tidyverse.org/reference/tibble.html)
is returned, it contains:

- continent:

  Continent where the mirror is located

- nation:

  Nation where the mirror is located

- location:

  Location of the mirror

- provider:

  Provider of the mirror

- url:

  URL of the mirror

- note:

  Special notes

## Examples

``` r
if (FALSE) { # interactive()
gutenberg_get_all_mirrors()
}
```
