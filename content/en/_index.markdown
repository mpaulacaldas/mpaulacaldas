---
title: Home
---

[<img src="https://simpleicons.org/icons/github.svg" style="max-width:15%;min-width:40px;float:right;" alt="Github repo" />](https://github.com/yihui/hugo-xmin)

# HUGO XMIN

## _Keep it simple, but not simpler_

**XMin** is a Hugo theme written by [Yihui Xie](https://yihui.name) in about four hours: half an hour was spent on the Hugo templates, and 3.5 hours were spent on styling. The main motivation for writing this theme was to provide a really minimal example to beginners of Hugo templates. This XMin theme contains about 130 lines of code in total, including the code in HTML templates and CSS (also counting empty lines).

:smile:


```bash
find . -not -path '*/exampleSite/*' \( -name '*.html' -o -name '*.css' \) | xargs wc -l
```

```
      49 ./content/es/post/2015-07-23-r-rmarkdown.html
      49 ./content/en/post/2015-07-23-r-rmarkdown.html
     118 ./public/note/index.html
     111 ./public/note/2017/06/13/a-quick-note/index.html
     107 ./public/note/2017/06/14/another-note/index.html
       0 ./public/index.html
     112 ./public/post/2015/07/23/lorem-ipsum/index.html
     147 ./public/post/2015/07/23/hello-r-markdown/index.html
     150 ./public/post/2015/07/23/rmd-toc/index.html
     123 ./public/post/index.html
     206 ./public/post/2016/02/14/a-plain-markdown-post/index.html
      60 ./public/css/style.css
       7 ./public/css/fonts.css
      98 ./public/404.html
     158 ./public/about/index.html
     113 ./public/tags/tutorial/index.html
     118 ./public/tags/pandoc/index.html
     138 ./public/tags/index.html
     118 ./public/tags/plot/index.html
     118 ./public/tags/blogdown/index.html
     128 ./public/tags/markdown/index.html
     118 ./public/tags/rstudio/index.html
     118 ./public/tags/r-markdown/index.html
     118 ./public/tags/mathjax/index.html
     118 ./public/tags/regression/index.html
     148 ./public/menu/index.html
      90 ./public/menu/404.html
     112 ./public/menu/tags/pandoc/index.html
     135 ./public/menu/tags/index.html
     112 ./public/menu/tags/plot/index.html
     112 ./public/menu/tags/blogdown/index.html
     117 ./public/menu/tags/markdown/index.html
     112 ./public/menu/tags/rstudio/index.html
     112 ./public/menu/tags/r-markdown/index.html
     112 ./public/menu/tags/mathjax/index.html
     112 ./public/menu/tags/regression/index.html
     115 ./public/menu/es/index.html
     139 ./public/menu/es/post/2015-07-23-r-rmarkdown/index.html
     198 ./public/menu/es/post/2016-02-14-hello-markdown/index.html
     104 ./public/menu/es/post/2015-07-23-lorem-ipsum/index.html
     105 ./public/menu/en/index.html
     150 ./public/menu/en/about/index.html
     115 ./public/menu/categories/index.html
     112 ./public/menu/categories/hugo/index.html
     117 ./public/menu/categories/example/index.html
     112 ./public/menu/categories/r/index.html
     116 ./public/fr/index.html
     100 ./public/fr/404.html
     111 ./public/fr/tags/index.html
     111 ./public/fr/categories/index.html
     131 ./public/es/index.html
     119 ./public/es/post/2015/07/23/lorem-ipsum-en-español/index.html
     154 ./public/es/post/2015/07/23/hola-r-markdown/index.html
     130 ./public/es/post/index.html
     213 ./public/es/post/2016/02/14/a-plain-markdown-post/index.html
     147 ./public/es/post/2015-07-23-r-rmarkdown/index.html
     206 ./public/es/post/2016-02-14-hello-markdown/index.html
     112 ./public/es/post/2015-07-23-lorem-ipsum/index.html
     100 ./public/es/404.html
     120 ./public/es/tags/pandoc/index.html
     143 ./public/es/tags/index.html
     120 ./public/es/tags/plot/index.html
     120 ./public/es/tags/blogdown/index.html
     125 ./public/es/tags/markdown/index.html
     120 ./public/es/tags/rstudio/index.html
     120 ./public/es/tags/r-markdown/index.html
     120 ./public/es/tags/mathjax/index.html
     120 ./public/es/tags/regression/index.html
     147 ./public/es/Untitled/2015-07-23-r-rmarkdown/index.html
     206 ./public/es/Untitled/2016-02-14-hello-markdown/index.html
     112 ./public/es/Untitled/2015-07-23-lorem-ipsum/index.html
     123 ./public/es/categories/index.html
     120 ./public/es/categories/hugo/index.html
     125 ./public/es/categories/example/index.html
     120 ./public/es/categories/r/index.html
     111 ./public/en/note/a-quick-note/index.html
     120 ./public/en/note/index.html
     113 ./public/en/note/2017/06/13/a-quick-note/index.html
     109 ./public/en/note/2017/06/14/another-note/index.html
     107 ./public/en/note/another-note/index.html
     275 ./public/en/index.html
     119 ./public/en/post/2015/07/23/lorem-ipsum/index.html
     154 ./public/en/post/2015/07/23/hello-r-markdown/index.html
     130 ./public/en/post/index.html
     213 ./public/en/post/2016/02/14/a-plain-markdown-post/index.html
     147 ./public/en/post/2015-07-23-r-rmarkdown/index.html
     206 ./public/en/post/2016-02-14-hello-markdown/index.html
     112 ./public/en/post/2015-07-23-lorem-ipsum/index.html
     100 ./public/en/404.html
     160 ./public/en/about/index.html
     115 ./public/en/tags/tutorial/index.html
     120 ./public/en/tags/pandoc/index.html
     147 ./public/en/tags/index.html
     120 ./public/en/tags/plot/index.html
     120 ./public/en/tags/blogdown/index.html
     125 ./public/en/tags/markdown/index.html
     120 ./public/en/tags/rstudio/index.html
     120 ./public/en/tags/r-markdown/index.html
     120 ./public/en/tags/mathjax/index.html
     120 ./public/en/tags/regression/index.html
     123 ./public/en/categories/index.html
     120 ./public/en/categories/hugo/index.html
     135 ./public/en/categories/example/index.html
     120 ./public/en/categories/r/index.html
     114 ./public/categories/index.html
     118 ./public/categories/hugo/index.html
     138 ./public/categories/example/index.html
     118 ./public/categories/r/index.html
      19 ./layouts/partials/foot_custom.html
       5 ./layouts/partials/head_custom.html
       6 ./layouts/partials/translations.html
      21 ./layouts/partials/header.html
      60 ./static/css/style.css
       7 ./static/css/fonts.css
       5 ./themes/hugo-xmin/layouts/404.html
      12 ./themes/hugo-xmin/layouts/_default/single.html
      20 ./themes/hugo-xmin/layouts/_default/list.html
      13 ./themes/hugo-xmin/layouts/_default/terms.html
       0 ./themes/hugo-xmin/layouts/partials/foot_custom.html
       0 ./themes/hugo-xmin/layouts/partials/head_custom.html
       9 ./themes/hugo-xmin/layouts/partials/footer.html
      20 ./themes/hugo-xmin/layouts/partials/header.html
      51 ./themes/hugo-xmin/static/css/style.css
       7 ./themes/hugo-xmin/static/css/fonts.css
   13696 total
```

I can certainly further reduce the code, for example, by eliminating the CSS, but I believe a tiny bit of CSS can greatly improve readability. You cannot really find many CSS frameworks that only contain 50 lines of code.

Although it is a minimal theme, it is actually fully functional. It supports pages (including the home page), blog posts, a navigation menu, categories, tags, and RSS. With [a little bit customization](https://github.com/yihui/hugo-xmin/blob/master/exampleSite/layouts/partials/foot_custom.html), it can easily support LaTeX math expressions, e.g.,

`$${\sqrt {n}}\left(\left({\frac {1}{n}}\sum _{i=1}^{n}X_{i}\right)-\mu \right)\ {\xrightarrow {d}}\ N\left(0,\sigma ^{2}\right)$$`

All pages not under the root directory of the website are listed below. You can also visit the list page of a single section, e.g., [posts](/post/), or [notes](/note/). See the [About](/about/) page for the usage of this theme.
