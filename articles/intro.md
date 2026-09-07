# Getting Started with gutenbergr

The gutenbergr package helps you download and process public domain
works from [Project Gutenberg](http://www.gutenberg.org/). This vignette
introduces the package’s metadata datasets and core downloading
functionality.

## Required Libraries

``` r

library(dplyr)
library(stringr)
```

## Exploring the Metadata

### `gutenberg_metadata`

The `gutenberg_metadata` dataset contains information about each work in
the Project Gutenberg collection:

``` r

gutenberg_metadata
```

    #> # A tibble: 82,415 × 8
    #>    gutenberg_id title    author gutenberg_author_id language gutenberg_bookshelf
    #>           <int> <chr>    <chr>                <int> <fct>    <chr>              
    #>  1            1 "The De… Jeffe…                1638 en       Politics/American …
    #>  2            2 "The Un… Unite…                   1 en       Politics/American …
    #>  3            3 "John F… Kenne…                1666 en       Category: Essays, …
    #>  4            4 "Lincol… Linco…                   3 en       US Civil War/Categ…
    #>  5            5 "The Un… Unite…                   1 en       United States/Poli…
    #>  6            6 "Give M… Henry…                   4 en       American Revolutio…
    #>  7            7 "The Ma… NA                      NA en       Category: History …
    #>  8            8 "Abraha… Linco…                   3 en       US Civil War/Categ…
    #>  9            9 "Abraha… Linco…                   3 en       US Civil War/Categ…
    #> 10           10 "The Ki… NA                      NA en       Banned Books List …
    #> # ℹ 82,405 more rows
    #> # ℹ 2 more variables: rights <fct>, has_text <lgl>

You can filter this to find specific works:

``` r

gutenberg_metadata |>
  filter(title == "Persuasion")
```

    #> # A tibble: 3 × 8
    #>   gutenberg_id title     author gutenberg_author_id language gutenberg_bookshelf
    #>          <int> <chr>     <chr>                <int> <fct>    <chr>              
    #> 1          105 Persuasi… Auste…                  68 en       "Category: Novels/…
    #> 2        22963 Persuasi… Auste…                  68 en       ""                 
    #> 3        36777 Persuasi… Auste…                  68 fr       "FR Littérature/Ca…
    #> # ℹ 2 more variables: rights <fct>, has_text <lgl>

The metadata currently in the package was last updated on **25 June
2026**.

### `gutenberg_works()`

In most analyses, you’ll want to filter for English works, avoid
duplicates, and include only books with downloadable text. The
[`gutenberg_works()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_works.md)
function does this automatically:

``` r

gutenberg_works()
```

    #> # A tibble: 63,652 × 8
    #>    gutenberg_id title    author gutenberg_author_id language gutenberg_bookshelf
    #>           <int> <chr>    <chr>                <int> <fct>    <chr>              
    #>  1            1 "The De… Jeffe…                1638 en       Politics/American …
    #>  2            2 "The Un… Unite…                   1 en       Politics/American …
    #>  3            3 "John F… Kenne…                1666 en       Category: Essays, …
    #>  4            4 "Lincol… Linco…                   3 en       US Civil War/Categ…
    #>  5            5 "The Un… Unite…                   1 en       United States/Poli…
    #>  6            6 "Give M… Henry…                   4 en       American Revolutio…
    #>  7            7 "The Ma… NA                      NA en       Category: History …
    #>  8            8 "Abraha… Linco…                   3 en       US Civil War/Categ…
    #>  9            9 "Abraha… Linco…                   3 en       US Civil War/Categ…
    #> 10           10 "The Ki… NA                      NA en       Banned Books List …
    #> # ℹ 63,642 more rows
    #> # ℹ 2 more variables: rights <fct>, has_text <lgl>

You can also filter directly within the function:

``` r

gutenberg_works(author == "Austen, Jane")
```

    #> # A tibble: 15 × 8
    #>    gutenberg_id title    author gutenberg_author_id language gutenberg_bookshelf
    #>           <int> <chr>    <chr>                <int> <fct>    <chr>              
    #>  1          105 "Persua… Auste…                  68 en       "Category: Novels/…
    #>  2          121 "Northa… Auste…                  68 en       "Gothic Fiction/Ca…
    #>  3          141 "Mansfi… Auste…                  68 en       "Category: Novels/…
    #>  4          158 "Emma"   Auste…                  68 en       "Category: Novels/…
    #>  5          161 "Sense … Auste…                  68 en       "Category: Romance…
    #>  6          946 "Lady S… Auste…                  68 en       "Category: Novels/…
    #>  7         1212 "Love a… Auste…                  68 en       "Category: Romance…
    #>  8         1342 "Pride … Auste…                  68 en       "Best Books Ever L…
    #>  9        31100 "The Co… Auste…                  68 en       "Category: Romance…
    #> 10        37431 "Pride … Auste…                  68 en       "Category: Plays/F…
    #> 11        42078 "The Le… Auste…                  68 en       "Category: Biograp…
    #> 12        63569 "The Wa… Auste…                  68 en       "Category: Novels/…
    #> 13        74233 "Fragme… Auste…                  68 en       "Category: Novels/…
    #> 14        77117 "The Wa… Auste…                  68 en       ""                 
    #> 15        78656 "Duolog… Auste…                  68 en       ""                 
    #> # ℹ 2 more variables: rights <fct>, has_text <lgl>

``` r

# Using regular expressions
gutenberg_works(str_detect(author, "Austen"))
```

    #> # A tibble: 25 × 8
    #>    gutenberg_id title    author gutenberg_author_id language gutenberg_bookshelf
    #>           <int> <chr>    <chr>                <int> <fct>    <chr>              
    #>  1          105 Persuas… Auste…                  68 en       Category: Novels/C…
    #>  2          121 Northan… Auste…                  68 en       Gothic Fiction/Cat…
    #>  3          141 Mansfie… Auste…                  68 en       Category: Novels/C…
    #>  4          158 Emma     Auste…                  68 en       Category: Novels/C…
    #>  5          161 Sense a… Auste…                  68 en       Category: Romance/…
    #>  6          946 Lady Su… Auste…                  68 en       Category: Novels/C…
    #>  7         1212 Love an… Auste…                  68 en       Category: Romance/…
    #>  8         1342 Pride a… Auste…                  68 en       Best Books Ever Li…
    #>  9        17797 Memoir … Auste…                7603 en       Category: Biograph…
    #> 10        22536 Jane Au… Auste…               25392 en       Category: Biograph…
    #> # ℹ 15 more rows
    #> # ℹ 2 more variables: rights <fct>, has_text <lgl>

``` r

# Multiple conditions
gutenberg_works(author == "Dickens, Charles", has_text == TRUE)
```

    #> # A tibble: 94 × 8
    #>    gutenberg_id title    author gutenberg_author_id language gutenberg_bookshelf
    #>           <int> <chr>    <chr>                <int> <fct>    <chr>              
    #>  1           46 "A Chri… Dicke…                  37 en       Children's Literat…
    #>  2           98 "A Tale… Dicke…                  37 en       Historical Fiction…
    #>  3          564 "The My… Dicke…                  37 en       Mystery Fiction/Ca…
    #>  4          580 "The Pi… Dicke…                  37 en       Best Books Ever Li…
    #>  5          588 "Master… Dicke…                  37 en       Category: Novels/C…
    #>  6          644 "The Ha… Dicke…                  37 en       Christmas/Category…
    #>  7          650 "Pictur… Dicke…                  37 en       Category: Travel W…
    #>  8          653 "The Ch… Dicke…                  37 en       Category: Novels/C…
    #>  9          675 "Americ… Dicke…                  37 en       Category: Travel W…
    #> 10          676 "The Ba… Dicke…                  37 en       Christmas/Category…
    #> # ℹ 84 more rows
    #> # ℹ 2 more variables: rights <fct>, has_text <lgl>

### `gutenberg_subjects`

The `gutenberg_subjects` dataset pairs works with Library of Congress
classifications and subject headings:

``` r

gutenberg_subjects
```

    #> # A tibble: 265,327 × 3
    #>    gutenberg_id subject_type subject                                            
    #>           <int> <fct>        <chr>                                              
    #>  1            1 lcsh         United States -- History -- Revolution, 1775-1783 …
    #>  2            1 lcsh         United States. Declaration of Independence         
    #>  3            1 lcc          E201                                               
    #>  4            1 lcc          JK                                                 
    #>  5            2 lcsh         Civil rights -- United States -- Sources           
    #>  6            2 lcsh         United States. Constitution. 1st-10th Amendments   
    #>  7            2 lcc          JK                                                 
    #>  8            2 lcc          KF                                                 
    #>  9            3 lcsh         United States -- Foreign relations -- 1961-1963    
    #> 10            3 lcsh         Presidents -- United States -- Inaugural addresses 
    #> # ℹ 265,317 more rows

This is useful for finding works by genre or topic:

``` r

# Find detective stories
gutenberg_subjects |>
  filter(subject == "Detective and mystery stories")
```

    #> # A tibble: 1,002 × 3
    #>    gutenberg_id subject_type subject                      
    #>           <int> <fct>        <chr>                        
    #>  1          170 lcsh         Detective and mystery stories
    #>  2          173 lcsh         Detective and mystery stories
    #>  3          244 lcsh         Detective and mystery stories
    #>  4          305 lcsh         Detective and mystery stories
    #>  5          330 lcsh         Detective and mystery stories
    #>  6          481 lcsh         Detective and mystery stories
    #>  7          547 lcsh         Detective and mystery stories
    #>  8          863 lcsh         Detective and mystery stories
    #>  9          905 lcsh         Detective and mystery stories
    #> 10         1155 lcsh         Detective and mystery stories
    #> # ℹ 992 more rows

``` r

# Find Sherlock Holmes stories
gutenberg_subjects |>
  filter(grepl("Holmes, Sherlock", subject))
```

    #> # A tibble: 60 × 3
    #>    gutenberg_id subject_type subject                                           
    #>           <int> <fct>        <chr>                                             
    #>  1          108 lcsh         Holmes, Sherlock (Fictitious character) -- Fiction
    #>  2          221 lcsh         Holmes, Sherlock (Fictitious character) -- Fiction
    #>  3          244 lcsh         Holmes, Sherlock (Fictitious character) -- Fiction
    #>  4          834 lcsh         Holmes, Sherlock (Fictitious character) -- Fiction
    #>  5         1661 lcsh         Holmes, Sherlock (Fictitious character) -- Fiction
    #>  6         2097 lcsh         Holmes, Sherlock (Fictitious character) -- Fiction
    #>  7         2343 lcsh         Holmes, Sherlock (Fictitious character) -- Fiction
    #>  8         2344 lcsh         Holmes, Sherlock (Fictitious character) -- Fiction
    #>  9         2345 lcsh         Holmes, Sherlock (Fictitious character) -- Fiction
    #> 10         2346 lcsh         Holmes, Sherlock (Fictitious character) -- Fiction
    #> # ℹ 50 more rows

You can join this with
[`gutenberg_works()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_works.md)
to download books by subject:

``` r

# Get IDs of detective stories
detective_ids <- gutenberg_subjects |>
  filter(subject == "Detective and mystery stories") |>
  inner_join(gutenberg_works(), by = "gutenberg_id") |>
  pull(gutenberg_id)

# Download a sample
detective_stories <- gutenberg_download(
  detective_ids[1:5],
  meta_fields = c("title", "author")
)
```

### `gutenberg_authors`

The `gutenberg_authors` dataset contains author information including
aliases and birth/death years:

``` r

gutenberg_authors
```

    #> # A tibble: 26,928 × 7
    #>    gutenberg_author_id author        alias birthdate deathdate wikipedia aliases
    #>                  <int> <chr>         <chr>     <int>     <int> <chr>     <chr>  
    #>  1                   1 United States U.S.…        NA        NA https://… U.S.A. 
    #>  2                   3 Lincoln, Abr… NA         1809      1865 https://… United…
    #>  3                   4 Henry, Patri… NA         1736      1799 https://… NA     
    #>  4                   5 Adam, Paul    NA         1849      1931 https://… NA     
    #>  5                   7 Carroll, Lew… NA         1832      1898 https://… Dodgso…
    #>  6                   8 United State… NA           NA        NA https://… Agency…
    #>  7                   9 Melville, He… Melv…      1819      1891 https://… Melvil…
    #>  8                  10 Barrie, J. M… NA         1860      1937 https://… Barrie…
    #>  9                  11 Church of Je… NA           NA        NA https://… NA     
    #> 10                  12 Smith, Josep… Smit…      1805      1844 https://… Smith,…
    #> # ℹ 26,918 more rows

This can be useful for filtering by author characteristics:

``` r

# Find works by 19th century authors
nineteenth_century_gutenberg_authors <- gutenberg_authors |>
  filter(birthdate >= 1800, birthdate < 1900) |>
  inner_join(gutenberg_works(), by = "gutenberg_author_id")
```

## Downloading Books

### Single Book

Download a book using its Gutenberg ID with
[`gutenberg_download()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_download.md):

``` r

persuasion <- gutenberg_download(105, meta_fields = c("title", "author"))
```

``` r

persuasion
```

    #> # A tibble: 8,357 × 4
    #>    gutenberg_id text             title      author      
    #>           <int> <chr>            <chr>      <chr>       
    #>  1          105 "Persuasion"     Persuasion Austen, Jane
    #>  2          105 ""               Persuasion Austen, Jane
    #>  3          105 ""               Persuasion Austen, Jane
    #>  4          105 "by Jane Austen" Persuasion Austen, Jane
    #>  5          105 ""               Persuasion Austen, Jane
    #>  6          105 "(1818)"         Persuasion Austen, Jane
    #>  7          105 ""               Persuasion Austen, Jane
    #>  8          105 ""               Persuasion Austen, Jane
    #>  9          105 ""               Persuasion Austen, Jane
    #> 10          105 ""               Persuasion Austen, Jane
    #> # ℹ 8,347 more rows

The result is a tibble with:

- `gutenberg_id` - the book’s ID
- `text` - one row per line of text

### Multiple Books

Download multiple books by providing a vector of Gutenberg IDs:

``` r

books <- gutenberg_download(c(105, 109))
```

``` r

books
```

    #> # A tibble: 9,579 × 4
    #>    gutenberg_id text                         title                       author 
    #>           <int> <chr>                        <chr>                       <chr>  
    #>  1          109 "Renascence and Other Poems" Renascence, and Other Poems Millay…
    #>  2          109 ""                           Renascence, and Other Poems Millay…
    #>  3          109 ""                           Renascence, and Other Poems Millay…
    #>  4          109 "by"                         Renascence, and Other Poems Millay…
    #>  5          109 ""                           Renascence, and Other Poems Millay…
    #>  6          109 "Edna St. Vincent Millay"    Renascence, and Other Poems Millay…
    #>  7          109 ""                           Renascence, and Other Poems Millay…
    #>  8          109 ""                           Renascence, and Other Poems Millay…
    #>  9          109 ""                           Renascence, and Other Poems Millay…
    #> 10          109 ""                           Renascence, and Other Poems Millay…
    #> # ℹ 9,569 more rows

### Adding Metadata

Use the `meta_fields` argument to include additional information:

``` r

books <- gutenberg_download(c(105, 109), meta_fields = c("title", "author"))
```

``` r

books |>
  count(title)
```

    #> # A tibble: 2 × 2
    #>   title                           n
    #>   <chr>                       <int>
    #> 1 Persuasion                   8357
    #> 2 Renascence, and Other Poems  1222

### Downloading from `gutenberg_works()`

You can pipe the output of
[`gutenberg_works()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_works.md)
directly into
[`gutenberg_download()`](https://docs.ropensci.org/gutenbergr/reference/gutenberg_download.md):

``` r

# Download all of Aristotle's works with titles
aristotle_books <- gutenberg_works(author == "Aristotle") |>
  gutenberg_download(meta_fields = "title")
```

## What’s Next?

Now that you have book texts as tibbles, you can:

- Perform text analysis with the
  [tidytext](https://github.com/juliasilge/tidytext) package
- See the [Text Mining
  Example](https://docs.ropensci.org/gutenbergr/articles/text-mining.md)
  vignette for a complete analysis workflow
- Explore the [Natural Language Processing CRAN
  View](https://CRAN.R-project.org/view=NaturalLanguageProcessing) for
  more text analysis packages

## Additional Resources

- Match Wikipedia data with
  [WikipediR](https://cran.r-project.org/package=WikipediR) or
  [wikipediatrend](https://cran.r-project.org/package=wikipediatrend)
- Parse author names with
  [humaniformat](https://cran.r-project.org/package=humaniformat)
- Predict gender from names with
  [gender](https://cran.r-project.org/package=gender)
