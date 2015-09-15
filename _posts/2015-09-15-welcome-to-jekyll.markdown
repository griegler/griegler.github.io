---
layout: post
title:  "Recurring Terminal Commands"
date:   2015-09-15 09:51:03
categories: jekyll update
---
This is a small list of terminal commands that I need sometimes. 
Because I do not want to google them all the time, I state them here.


# Git

## Git ignore

* ignore all .txt files in the doc/ directory of your project (recursively).
```bash
doc/**/*.txt
```
## Git Remote

* Create a new remote branch by pushing to it.

```bash
git push remote_name branch_name  # pushes the current branch to the server remote_name with branch_name
```

* Add the upstream to the branch.

```bash
git branch -u remote_name/branch_name
```

* Delete a remote branch.

```bash
git push remote_name --delete branch_name
```

## Git SVN

* Checkout with std layout 

```bash
git svn clone http://svn.example.com/project --stdlayout
```


## Git Subtree

* Add remote.

```bash
git remote add <remote name> <remote URL>
```

* Add subtree (squash to reduce to one commit)

```bash
git subtree add –-prefix=<new folder> <remote> <branch> --squash
```

* Subtree push

```bash
git subtree push –-prefix=<subtree folder> <remote> <branch>
```

* Subtree pull

```bash
git subtree pull –-prefix=<subtree folder> <remote> <branch>
```


# PDF

* Convert PDF to grayscale

```bash 
gs -sOutputFile=output.pdf -sDEVICE=pdfwrite -sColorConversionStrategy=Gray -dProcessColorModel=/DeviceGray -dCompatibiltyLevel=1.4 -dNOPAUSE -dBATCH input.pdf
```

* Compress PDF (settings are screen, ebook, printer, prepress, default)

```bash
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf
```


# Compressing

* Compress and decompress with xz

```bash
tar -c --xz -f archive.tar.xz /some_directory/
tar -x --xz -f archive.tar.xz 
```

* Compress and decompress with lzma

```bash
tar -c --lzma -f archive.tar.lzma /some_directory/
tar -x --lzma -f archive.tar.lzma 
```

# Remote

* Inspect output of a running process from another terminal (pid = process id; needs root)

```bash
strace -p pid -e write
```
