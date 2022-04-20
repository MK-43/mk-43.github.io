---
title:  "[github pages] overall"
excerpt: "Describe how to create github pages"

categories:
  - jekyll
tags:
  - [blog]

toc: true
toc_sticky: true
 
date: 2022-04-19
last_modified_at: 2022-04-19
---

### _posts

포스트는 바로 최상단 아래 `_post` 카테고리에 존재해야 함.
없으면 새로 만든다.

### _config.yml

Settings that affect your entire site.

### YAML Front Matter

_config.yml 아래에 있는 `defaults`를 말하는 듯
any default value can be overridden by settings in a post, page, or collection file.

Using the `default` key in `_config.yml` you could set the layout for all posts

각각 개별 _configyml파일을 생성한다.

## jekyll

run jekyll server with my IP

```bash
bundle exec jekyll serve --host={my_ip}
```
