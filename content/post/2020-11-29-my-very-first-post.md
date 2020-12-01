---
URL: /2020/11/30/very-first-blog-post/
author: Adrian Gabriel
categories:
- About
- R
date: "2020-11-29 09:00:00"
description: Creating your very first blog
excerpt: My very first blog post
image: "img/blog.jpg"
published: true
subtitle: Getting an idea of your data's underlying distribution
tags:
- R
- Statistics
- Data Science
title: Likelihood Estimation
output:
  hugormd::post:
    highlight_shortcode: false
---


```{r setup, include =False}
library(reticulate)
use_python("/usr/local/bin/python")
```

```python
import pandas as pd
import numpy as np
print("hello"*3)
```