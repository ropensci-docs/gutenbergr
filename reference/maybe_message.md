# Display a message conditionally

Display a message conditionally

## Usage

``` r
maybe_message(verbose, message, class = NULL, ..., call = rlang::caller_env())
```

## Arguments

- verbose:

  Logical; whether to display the message.

- message:

  Message to display.

- class:

  Optional message class.

- ...:

  Additional arguments passed to
  [`cli::cli_inform()`](https://cli.r-lib.org/reference/cli_abort.html).

- call:

  The execution environment of the calling function.

## Value

Invisibly returns `NULL`. Called for its side effect of displaying a
message.
