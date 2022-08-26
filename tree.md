---
title: Tree
category: CLI
layout: 2017/sheet
tags: [Featured]
updated: 2022-08-31
keywords:
  - HTML output
  - Full patch "link friendly" and for automation
---

Getting started
---------------

tree -if $PWD # "wget -m" to file list. might want to edit out the place you ran this command (e.g. /home/user/temp/projectWA/some.website.com)
tree PATH -H http://localhost -o out.html
ls -fR $PWD/* # also does the job but is more sucky, files in subdirectories will have ': \n . ..'
