---
title: Searching Haml files with ack
nav: articles
date: 2012-05-14
updated: 2014-11-20
categories: vim
---

*This article describes how you can configure your ack settings to search for additionals files.  UPATE: [Andy Lester](http://andylester.org), the author of ack, give me feedback about this article.*


Recently I was working on a Rails project and was using Vim with the `:Ack <pattern>` command to search after a certain typed string "Übreschrift" and would like to replace it with the correct version "Überschrift". I typed into the console `:Ack Übreschrift` and I couldn't find a single match. What went wrong?


## Questions to answer

Why couldn't I find the file with that content? Was I in the wrong directory? No:


```bash
$ pwd
-> $HOME/git-repositories/brokenlifts
```


Did I used the wrong pattern? No, I searched after the right word "Übreschrift". Did I used the wrong command?  No, I tried `ack-grep` in the terminal to search for other common words like *test* or *string* and could only find results in *.rb, *.js files but not in `*.html.haml` files. Tada, found the mistake, `ack` is per default not configured to include these very special file types. If your press `ack -f` (thanks [Andy Lester](http://petdance.com/) for this note) you will get the output of all files ack will go through - and this command didn't displayed `*.html.haml` files.


## Solve problems .ackrc

I created the `$HOME/.ackrc` and added the entries to include these special filename:


```bash
--type-add
html=.html.haml
```


Now my search worked and I got hits in `*.html.haml` files for searching the term "Übreschrift".


## Further refinements

Since I'm working with Rails there are other file types like `sass, erb, less, scss, ..` I would like to include into the search:


```bash
--type-add
html=.html.erb,.html.haml,.haml
--type-add
css=.sass,.less,.scss
```


And there might be directories I don't want to have in my search path. Let's ignore them and speed up our search:


```bash
# ignore certain file types
--type-set=ignorables=.log,.tmp,.pdf

# ignore whole directories
--ignore-dir=vendor
--ignore-dir=log
--ignore-dir=tmp
--ignore-dir=doc
--ignore-dir=coverage
```


If you would like to see the specified files for your grep environment search, use `ack --help types` - this will print all information you need. Here is an example:


```bash
$ ack --help types
=>
  --[no]actionscript .as .mxml
  --[no]ada          .ada .adb .ads
  --[no]asm          .asm .s
  --[no]batch        .bat .cmd
  --[no]binary       Binary files, as defined by Perl's -B op (default: off)
  --[no]cc           .c .h .xs
  --[no]cfmx         .cfc .cfm .cfml
  --[no]cpp          .cpp .cc .cxx .m .hpp .hh .h .hxx
  --[no]csharp       .cs
  --[no]css          .css .sass .less .scss
  --[no]elisp        .el
  --[no]erlang       .erl .hrl
  --[no]fortran      .f .f77 .f90 .f95 .f03 .for .ftn .fpp
  --[no]haskell      .hs .lhs
  --[no]hh           .h
  --[no]html         .htm .html .shtml .xhtml .html.erb .html.haml .haml
  --[no]ignorables   .log .tmp .pdf
...
```


## Further reading

- [ack](http://betterthangrep.com/)

