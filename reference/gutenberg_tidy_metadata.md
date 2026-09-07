# Prepare metadata for a 1-to-1 join

Prepare metadata for a 1-to-1 join

## Usage

``` r
gutenberg_tidy_metadata(metadata, fields, sep = " & ")
```

## Arguments

- metadata:

  The metadata data frame (usually `gutenberg_metadata`).

- fields:

  The fields to include in the join.

- sep:

  The separator to use for multiple values (e.g., authors).

## Value

A data frame with one row per `gutenberg_id`.
