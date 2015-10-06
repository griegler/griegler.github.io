---
layout: post
title:  "Recurring Terminal Commands"
comments: true
date:   2015-09-15 09:51:03
categories: git pdf compression remote
---
This is a small list of terminal commands that I need sometimes. 
Because I do not want to google them all the time, I state them here.


# Git

## Git ignore

* ignore all .txt files in the doc/ directory of your project (recursively).
{% highlight bash %}
doc/**/*.txt
{% endhighlight %}


## Git Remote

* Create a new remote branch by pushing to it.

{% highlight bash %}
git push remote_name branch_name  # pushes the current branch to the server remote_name with branch_name
{% endhighlight %}

* Add the upstream to the branch.

{% highlight bash %}
git branch -u remote_name/branch_name
{% endhighlight %}

* Delete a remote branch.

{% highlight bash %}
git push remote_name --delete branch_name
{% endhighlight %}

## Git SVN

* Checkout with std layout 

{% highlight bash %}
git svn clone http://svn.example.com/project --stdlayout
{% endhighlight %}


## Git Subtree

* Add remote.

{% highlight bash %}
git remote add <remote name> <remote URL>
{% endhighlight %}

* Add subtree (squash to reduce to one commit)

{% highlight bash %}
git subtree add –-prefix=<new folder> <remote> <branch> --squash
{% endhighlight %}

* Subtree push

{% highlight bash %}
git subtree push –-prefix=<subtree folder> <remote> <branch>
{% endhighlight %}

* Subtree pull

{% highlight bash %}
git subtree pull –-prefix=<subtree folder> <remote> <branch>
{% endhighlight %}


# PDF

* Convert PDF to grayscale

{% highlight bash %} 
gs -sOutputFile=output.pdf -sDEVICE=pdfwrite -sColorConversionStrategy=Gray -dProcessColorModel=/DeviceGray -dCompatibiltyLevel=1.4 -dNOPAUSE -dBATCH input.pdf
{% endhighlight %}

* Compress PDF (settings are screen, ebook, printer, prepress, default)

{% highlight bash %}
gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf
{% endhighlight %}


# Compressing

* Compress and decompress with xz

{% highlight bash %}
tar -c --xz -f archive.tar.xz /some_directory/
tar -x --xz -f archive.tar.xz 
{% endhighlight %}

Pass options (like compression level 2 and verbose) to xz via XZ_OPT system variable

{% highlight bash %}
XZ_OPT=-2v tar -c --xz -f archive.tar.xz /some_directory/
{% endhighlight %}

* Compress and decompress with lzma

{% highlight bash %}
tar -c --lzma -f archive.tar.lzma /some_directory/
tar -x --lzma -f archive.tar.lzma 
{% endhighlight %}

* Unpack an ISO with 7z

{% highlight bash %}
7z x file.iso
{% endhighlight %}

# Remote

* Inspect output of a running process from another terminal (pid = process id; needs root)

{% highlight bash %}
strace -p pid -e write
{% endhighlight %}
