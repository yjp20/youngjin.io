---
title: "Creating a custom theme in Hugo"
date: 2019-04-01T22:14:57-06:00
tags: ["code", "blog"]
draft: false
---

I've spent some time creating this site's theme on Hugo, which was the first time I've used it. As it turns out, making a theme on Hugo is very easy. The documentation is pretty managable, but if you want a tutorial that takes you from the very beginning to the end, this is it.

## Get Hugo

There are many ways to get Hugo. Check out their website and get it onto your computer.

## Generate the Hugo site
Creating a Hugo site is easy, just run the following command after installing Hugo:

```
hugo new site [name]
```

After that, navigate into the base of the new Hugo folder. Then run

```
hugo new theme [theme_name]
```

This will create the theme under `[name]/themes/[theme_name]`. Technically, that _is_ a theme, but clearly we would like to add more. To now run the server which updates live as we add changes, you just have to run

```
hugo server
```
to have an Hugo instance running at http://localhost:1313.

## Hugo file structure

Before we start creating our theme, the most important thing is to understand the file structure of Hugo. In our generated site folder, we should have something that looks like the following:

```
- [name]
  - archetypes
  - content
  - data
  - layouts
  - public
  - resources
  - static
  - themes
    - [theme-name]
  - config.toml
```

### `content`

Contains written information, such as a blog post written in markdown. As the name of the folder implies, this folder is concerned with the central content of your website.

### `archetypes`

Stores templates that can be used to generate new files for content. For example, you could have a `default.md` file in the archetypes folder then generate a new document with a given name inside the `content` folder.

### `data`

Stores extra data that can be used to supplement standalone pages, which then can be accessed within templates.

### `layouts`

Provides extra layouts that are not provided with the theme, which is important when you're trying to make a custom page such as a portfolio page. An example using this feature will be given later on.

### `public`

Hugo generates files into this folder, so you should basically never manually touch a file inside here.

### `static`

Static contains files such as css, javascript, and certain images. The images that are put into this folder should be used within the website in general, not within a post.

### `config.toml`

Familiarize yourself with Toml and look at the various options that are given within the official Hugo documentation here.


## Add an example post
Personally, before moving too far ahead, I like to create an example post so that I could see the site coming together as I work. For this, we have to first move out of our theme, back into the root directory. We can create an example document through the following command:

```
hugo new content/posts/example.md
```

You can name this file whatever you want, it won't effect the result on the site. In our case, we'll call it example.md. The Hugo command will then automatically generate the following header, in which it generates a file based on the `archetypes/default.md` file. You should see something like the following:

```
---
title: "Example"
date: 2019-04-01T22:12:51-06:00
draft: true
---
```

* `title`: this should be relative self-explanatory, it is the title that is displayed on the site.
* `date`: this is the published date that can be seen on the post. By default, the posts are sorted by this date. If the date is in the future, the post won't be displayed.
* `draft`: if the draft option is on, then the post won't get compiled and show on the site.

You can now add any markdown items below. I recommend copying in some kind of long-form text, since that more accurately shows what your site looks like.

```markdown
---
title: "Example"
date: 2019-04-01T22:12:51-06:00
draft: true
---

# Markdown is fully supported

## So are a variety of other flavors

If you prefer certain flavors, you should check it
out on the official documentation.
```

## Customize templates


## Add syntax highlighting

## Add custom pages




