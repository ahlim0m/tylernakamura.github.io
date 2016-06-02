---
layout: post
title: "Sym Link For _posts/ in Jekyll"
date: 2016-06-01 20:57
comments: false
categories: Jekyll sym link _posts posts
---

When creating a new Jekyll post, I often need to cd into the _posts folder. 
You will notice that a Jekyll project precedes names with an '_'
For example, note that the contents of this simple Jekyll site:

```bash
.
├── _config.yml
├── _includes
│   ├── footer.html
│   ├── head.html
│   ├── header.html
│   ├── icon-github.html
│   ├── icon-github.svg
│   ├── icon-twitter.html
│   └── icon-twitter.svg
├── _layouts
│   ├── default.html
│   ├── page.html
│   └── post.html
├── _posts
├── _sass
│   ├── _base.scss
│   ├── _layout.scss
│   └── _syntax-highlighting.scss
├── about.md
├── css
│   └── main.scss
├── feed.xml
├── index.html
└── posts -> _posts
```

To get into _posts/, I hate typing in the underscore. Thus I created a symbolic link to allievate the great ordeal of typing in that single underscore.

```bash
ln -s _posts posts
```

You can read more about how symbolic links work [here](https://en.wikipedia.org/wiki/Symbolic_link).








