---
title: "Creating a custom theme in Hugo"
date: 2019-04-01T22:14:57-06:00
tags: ["code", "blog"]
draft: false
---

I've spent some time creating this site's theme on Hugo, which was the first time I've used it. As it turns out, making a theme on Hugo is very easy, albeit slightly lacking in some documentation.  During that process, I've learned a lot so I'll go through a step by step process of what it took to create this theme.

## Generate the hugo site
Creating a hugo site is easy, just run the following command after installing hugo:

```
hugo new site [name]
```

After that, navigate into the base of the new hugo folder. Then run

```
hugo new theme [theme_name]
```

This will create the theme under `[name]/themes/[theme_name]`. Technically, that _is_ a theme, but clearly we would like to add more. To now run the server which updates live as we add changes, you just have to run

```
hugo server
```
to have an hugo instance running at http://localhost:1313.

## Add an example post
Personally, before moving too far ahead, I like to create an example post so that I could see the site coming together as I work. For this, we have to first move out of our theme, back into the root directory. We can create an example document through the following command:

```
hugo new content/posts/example.md
```

You can name this file whatever you want, it won't effect the result on the site. In our case, we'll call it example.md. The hugo command will then automatically generate the following header, in which it generates a file based on the `archetypes/default.md` file.You should see something like the following:

```
---
title: "Example"
date: 2019-04-01T22:12:51-06:00
draft: true
---
```

* `title`: this should be relative self-explanatory, it is the title that is displayed on the site.
* `date`: this is the published date that can be seen on the post. By default, the posts are sorted by this date. If the date is in the future, the post won't show at all.
* `draft`: if the draft option is on, then the post won't get compiled and show.

You can now add any markdown items below. I recommend copying in some kind of long-form text, since that more accurately shows what your site looks like.

```markdown
---
title: "Example"
date: 2019-04-01T22:12:51-06:00
draft: true
---

# Markdown is fully supported

isn't that great
```

All you have to do to add more articles it to write more articles! Since hugo is a static generator, there's no need for complicated web administration panels like wordpress.

## Customize templates

## Add syntax highlighting

## Add custom pages




