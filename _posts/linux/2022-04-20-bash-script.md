---
title:  "[bash] overview"
excerpt: "Describe how to use bash"

categories:
  - linux
tags:
  - [bash]

toc: true
toc_sticky: true
 
date: 2022-04-20
last_modified_at: 2022-04-20
---

### declare variable

`declare`  
set variable values and attributes  
In most cases, it's enought with an implicit declartion in `bash`

```bash
my_var="some value"
```

But, sometimes you want a variable's value to only be integer.  

```bash
declare -i num=15
declare -r # readonly, but local scope
```

## readonly

the default scope is *global*

```bash
readonly b=1 # global
```

## set -e

used within the *bash* to stop execution instantly as a query exists while having a non-zero status.
also used when you need to know the error locaiton in the running code.
