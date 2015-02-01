
This is a collection of scripts for easily creating new [Jekyll](http://jekyllrb.com/) posts. I wrote them in Python (v3), because Python is pretty ubiquitous and has good-enough argument parsing. These scripts are modularized, so you can replace a script (using whatever language you like) to get the other scripts to do something different.


## `jekyll-post`

```
$ jekyll-post "S0me rand@m T1tle" -a "tags:['python', 'scripting']" -c blog
/home/malcolm/website/blog/_posts/2014-04-25-s0me-randm-t1tle.md
```

`jekyll-post` makes it easy to make new posts. It automatically generates the path (via `$JEKYLL_SITE_PATH` and `jekyll-post-filename`), and inserts the header attributes. Let's run the same command as above, but instead of making a new post in the `blog` category, we'll write the post to stdout:

```
$ jekyll-post "S0me rand@m T1tle" -a "tags:['python', 'scripting']" -o -
---
layout:    'default'
date:      '2014-04-25 13:03:26-04:00'
title: |
  S0me rand@m T1tle
tags:      ['python', 'scripting']
---
```

Note that when `jekyll-post` creates a new file, like in the first command, it writes the path of that new file to stdout. This lets you wrap the call to `jekyll-post` to edit the new post straight away:

```
$ vim `jekyll-post "Scripting is fun" -c notes`
```


## `jekyll-link`

```
$ jekyll-link "https://example.org/example-url"
/home/malcolm/website/blog/_posts/2014-04-25-the-title-in-the-html.md
```

`jekyll-link` is a wrapper around `jekyll-post`. It takes a URL, fetches it, and uses the contents of `<title>` tag for the title of the post, and makes a new post in the `links` category (by default).

For me, it reduces the friction of adding a new link to my [linkblog](http://minglis.id.au/links/index.html) to a single command with no repetition.


## Installing

To get these executable files on your PATH (assuming `~/.local/bin` is on your PATH), you might do something like:

```
$ cd ~/.local/bin
$ for s in ~/projects/jekyll-scripts/{jekyll-*,title-from-url}; do ln -s "$s"; done
```


## Help

All the scripts take `-h` or `--help` as an argument to describe all their arguments. I hope that their source code is also quite readable.

Please [raise an issue](https://github.com/mcinglis/jekyll-scripts/issues) if you're lost, or have a suggestion.

