---
title: Retrieving RMarkdown YAML metadata
author: ''
date: '2020-04-13'
categories:
  - R
tags:
  - rmarkdown
  - ymlthis
slug: rmarkdown-yaml-metadata
description: About rmarkdown's metadata object and the yamlthis package.
---

I recently discovered two nice features of the [rmarkdown](https://github.com/rstudio/rmarkdown/) package that deal with the YAML metadata of R Markdown documents: the `metadata` object and the `yaml_front_matter()` function. Both of these are generally used "behind the scenes" in the code of other R packages, but I found them very useful in my day-to-day reporting workflow. In this post, I will explain my understanding of these objects, and I will show a couple of helper functions I created with the [ymlthis](https://ymlthis.r-lib.org/index.html) package.  



## Using `metadata` in R Markdown templates

The `metadata` object returns the YAML metadata of the __current__ R Markdown document as a list. Keep in mind that this object is only created in the knit environment, i.e. when you render your document. For example, this post has the following metadata specified at the top of the `` file:

```yaml
---
title: Retrieving RMarkdown YAML metadata
author: ''
date: '2020-04-13'
categories: R
tags:
- rmarkdown
- ymlthis
slug: rmarkdown-yaml-metadata
description: About rmarkdown's metadata object and the yamlthis package.
---

```

Calling `metadata` will return a list with this metadata when we knit the document.

```r 
library(rmarkdown)
metadata
#> $title
#> [1] "Retrieving RMarkdown YAML metadata"
#> 
#> $author
#> [1] ""
#> 
#> $date
#> [1] "2020-04-13"
#> 
#> $categories
#> [1] "R"
#> 
#> $tags
#> [1] "rmarkdown" "ymlthis"  
#> 
#> $slug
#> [1] "rmarkdown-yaml-metadata"
#> 
#> $description
#> [1] "About rmarkdown's metadata object and the yamlthis package."

```

In an interactive R session, `metadata` will return an empty list.

Usually, we will refer to `metadata` parameters in inline code calls. For example, the following line in the source document

```
> This post was written on `r format(as.Date(metadata$date), '%B %d, %Y')`.
```

will be rendered as

> This post was written on April 13, 2020.

I have found the `metadata` object to be particularly useful when creating templates. A great example is the [xaringan template of the rstudio::conf2019 workshops](https://github.com/rstudio-conf-2020/slide-templates/blob/master/xaringan/index.). RStudio's template defines the title, subtitle, author and tutorial session in the YAML front matter of the R Markdown document, and later refers back to these objects via `metadata` to create the first slide of the presentation. This makes it easier to adapt the template as the main document parameters are defined at the top of the R Markdown file.

You may have noticed that `metadata` is similar to the `params` list used in parametrised reports. The main difference between the two is that `params` is designed for _iteration_. This is because the fields specified in `params` can be easily overridden via `rmarkdown::render()`. If you want to learn more about parametrised reports, I recommend the [bookdown book](https://bookdown.org/yihui/rmarkdown/parameterized-reports.html), or [Mike Smith's Talk from rstudio::conf2019](https://resources.rstudio.com/rstudio-conf-2019/the-lazy-and-easily-distracted-report-writer-using-rmarkdown-and-parameterised-reports). If you are interested in how `metadata` and `params` came to be, have a look at [issue #33](https://github.com/rstudio/rmarkdown/issues/33) of the rmarkdown package.

## Copying defaults with `yaml_front_matter()` and `ymlthis`

The `yaml_front_matter()` function returns a list with the YAML metadata of __any__ R Markdown file. Unlike `metatdata`, `yaml_front_matter()` also works outside of the knit environment.

```r 
yaml_front_matter("index.en.Rmarkdown") # provide file path
#> $title
#> [1] "Retrieving RMarkdown YAML metadata"
#> 
#> $author
#> [1] ""
#> 
#> $date
#> [1] "2020-04-13"
#> 
#> $categories
#> [1] "R"
#> 
#> $tags
#> [1] "rmarkdown" "ymlthis"  
#> 
#> $slug
#> [1] "rmarkdown-yaml-metadata"
#> 
#> $description
#> [1] "About rmarkdown's metadata object and the yamlthis package."

```

I was very excited when I learned about `yaml_front_matter()`[^community] because it allowed me to write a helper function for a repetitive task that I do all the time: opening up previous R Markdown document with a configuration I like, copying its YAML metadata, and using it to create or update another RMarkdown file.

[^community]: Thanks to this [answer](https://community.rstudio.com/t/how-can-i-read-parse-the-metadata-from-an-rmarkdown-file/47886/8) by Christophe Dervieux on RStudio Community.

To do this, I took advantage of the [ymlthis](https://ymlthis.r-lib.org/index.html) package, which provides tools to write YAML metadata of R Markdown documents.

```r 
library(magrittr) # for the pipe %>%
library(ymlthis)
copy_yaml <- function(input, ...) {
  input %>% 
    yaml_front_matter() %>%   # get the YAML metadata
    yml() %>%                 # transform list to yml object
    yml_replace(...) %>%      # replace fields specified in ...
    use_yml()                 # copy YAML header to clipboard
}
```

The `copy_yaml()` function defined above lets me grab the YAML metadata of any R Markdown document, update the fields that I wish to change, and get have the updated YAML header copied to my clipboard.

```r 
copy_yaml(
  "index.en.Rmarkdown", 
  title = "New title", 
  author = "María Paula Caldas"
  )
#>   ---
#>   title: New title
#>   author: María Paula Caldas
#>   date: '2020-04-13'
#>   categories: R
#>   tags:
#>   - rmarkdown
#>   - ymlthis
#>   slug: rmarkdown-yaml-metadata
#>   description: About rmarkdown's metadata object and the yamlthis package.
#>   ---
#> ● Paste into R Markdown or YAML file
```

I also wrote a similar function that creates a new R Markdown file with the YAML specifications of another.

```r 
create_with_yaml <- function(input, output, ...) {
  input %>% 
    yaml_front_matter() %>%
    yml() %>%
    yml_replace(...) %>%
    use_rmarkdown(output) # creates an Rmd file
}
```

Although simple, I find myself using these functions relatively often. I will definitely be looking more into ymlthis to see how I take advantage of more of its functionalities!
