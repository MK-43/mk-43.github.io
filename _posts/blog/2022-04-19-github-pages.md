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

[Ref](https://ansohxxn.github.io/categories/blog/)
[minimal-mistakes](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)
[inline math](https://tex.stackexchange.com/questions/27633/mathjax-inline-mode-not-rendering)
[inline math should have no space](https://www.overleaf.com/learn/latex/Mathematical_expressions)

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

### installation

```bash
sudo apt install ruby-full build-essential zlib1g-dev

echo '# Install Ruby Gems to ~/gems' >> ~/.zshrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.zshrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc

gem install jekyll bundler

bundle install # install dependencies specified in your gem file

jekyll serve
```

run jekyll server with my IP

```bash
bundle exec jekyll serve --host={my_ip}
```

### Gemfile

### How to use LaTex on github pages + minimal mistakes + MathJax

[Ref](https://kevinfossez.github.io/posts/2020/04/blog-post-1/)

`_includes/head/custom.html`

```html
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {
      inlineMath: [ ['$','$'], ["\\(","\\)"] ],
      displayMath: [ ['$$','$$'], ["\\(","\\)"] ],
    },
    TeX: {
      Macros: {
        bra: ["\\langle{#1}|", 1],
        ket: ["|{#1}\\rangle", 1],
        braket: ["\\langle{#1}\\rangle", 1],
        bk: ["\\langle{#1}|{#2}|{#3}\\rangle", 3]
     }
   }
  });
</script>

<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/latest.js?config=TeX-MML-AM_CHTML' async></script>
```
