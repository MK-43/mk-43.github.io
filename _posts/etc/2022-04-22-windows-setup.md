---
title:  "[react] overview"
excerpt: "Describe how to use react"

categories:
  - web
tags:
  - [react]

toc: true
toc_sticky: true
 
date: 2022-04-20
last_modified_at: 2022-04-20
---

### ctrl + shift &rarr; change between multiple keyboard layouts
[Just remove english keyboard](https://superuser.com/questions/957552/how-to-delete-a-keyboard-layout-in-windows-10)

### windows 10 - How to disable Office key keyboard shortcut opening Office app? - Super User
refer to [this](https://superuser.com/questions/1455857/how-to-disable-office-key-keyboard-shortcut-opening-office-app)  

Changing the open command for this keyboard shortcut to rundll32 resolved the issue for me.   
Using an elevated cmd, run the following command:  
`REG ADD HKCU\Software\Classes\ms-officeapp\Shell\Open\Command /t REG_SZ /d rundll32`