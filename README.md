# R-Ladies global blog

[![Netlify Status](https://api.netlify.com/api/v1/badges/728e663f-18fb-432c-80d6-840c043ce50a/deploy-status)](https://app.netlify.com/sites/stoic-curran-741947/deploys)

## Editors

- Chrissy Zasada [`@ChrisZasa`](https://github.com/ChrisZasa)

## Maintainers

- Athanasia M. Mowinckel [`@Athanasiamo`](https://github.com/Athanasiamo)

---

# Contribute

## Install dependecies

```r
# required R pacakges
install.packages(c('blogdown', 'magrittr', 'stringr'))

# optional workflow
# install.packages('usethis')

# hugo installation for version required
blogdown::install_hugo("0.80.0")
```

## Clone the project

Choose your own workflow! You can proceed via either:

1. `git` commands in the terminal, or

2. through the `usethis` package 
  - An in-depth overview of this workflow is available at 
[Pull Request Flow with usethis](https://www.garrickadenbuie.com/blog/pull-request-flow-usethis/?interactive=1&steps=) by Garrick Aden-Buie.

### via git in the terminal


```sh
# Clone
git clone https://github.com/rladies/blog.git

# Enter
cd blog/

# replace my_branch with any name you like
# will now be working on a copy of the main repo
git checkout -b my_branch
```

Open the folder in RStudio.

### via {usethis}

```r
# this forks and clones the repo
usethis::create_from_github("rladies/blog")

# this creates a new branch for your post
usethis::pr_init("my_branch")
```


## Write a new blog post

There are two ways to create a new post:

1. Use the blogdown addin in RStudio to create a new post: `Addins` -> `New post`, OR
 
2. `blogdown::new_post()` (See [documentation](https://pkgs.rstudio.com/blogdown/reference/hugo_cmd.html) for arguments to complete.)


Complete fields with relevant information, following these guidelines to make
posts easily discoverable.

- **Title**: Post title. This is the main feature, it shows in the list and the
post page.
- **Author**: Post author. This is not currently visible when rendered on the
site, but please still complete this field. We will work to make it visible and
to show in a menu.
- **Date**: Post date. The date *must* be static, nothing like `r Sys.Date()`,
otherwise every time the blog is generated a new date is set in the blog post.
The **format must be YYYY-mm-dd**.
- **Description**: Post subtitle. As an example, we used it to set the title of
the post series of the 2018 IWD project. It shows in the posts list and in the
post page.
- **Tags**: Post tags. They should include meaningful information; for recurrent
posts please follow previous tags. 4 or 5 tags is a good number.
[Tags](http://blog.rladies.org/tags/).
- **Categories**: Post categories. Like tags but the theme is more general. This
field is currently not visible and is optional.
[Categories](http://blog.rladies.org/categories/).

All of the information will be shown in the post yaml, and can also be edited later.

Example:

```yaml
---
title: "1. Behind the scenes of R-Ladies IWD2018 Twitter action!"
author: "R-Ladies"
date: "2018-03-26"
description: "Part 1: Ideation and Creation!"
tags:
- iwd
- twitter
- part1
- 2018
categories:
- IWD
- R-Ladies
---
```

Once submitted, 

- within `content/post` 

- a new folder is created like `yyyy-mm-dd-your-post-title`

- with an outline for your post named `index.Rmd`

Add all files needed for the post (images, data files, gifs, etc.) should be 
added to the new folder `content/post/yyyy-mm-dd-your-post-title`. 

As you write you post, remember to `knit` your post to see how it looks! 
The blogdown site will use the markdown file created from your knitted `index.Rmd` 
on the site, not your `Rmd` itself. You can preview the entire site with your post with `blogdown::serve_site()`. 

## After you write your post

Once your post looks as you want it to on your local machine, it's time to push the post
up to the main repository for review.

### via git in the terminal


```sh
# Add the post
git add content/post/yyyy-mm-dd-your-post-title

# Add a commit message to the post
git commit -m "my commit message"

# Push changes online (replace my_branch with your branch name)
git push --set-upstream origin my_branch
```

### via {usethis}


In the RStudio git pane, check your post folder and commit with a message. 

Then push with 

```r
usethis::pr_push()
```

This will automatically open up the page in GitHub where you can make a pull request.

## Create Pull Request

Once you have pushed your changes online, make a [Pull request (PR)](https://github.com/rladies/blog/pulls) to the master branch. 

If you do not know who should review your post, please request `@ChrisZasa`; otherwise,
tag the appropriate individual.

If you are an external contributor (not a member of the R-Ladies Global administration team),
in the comment please write `@ChrisZasa this post is ready for review!` 

If you are an internal contributor (a member of the R-Ladies Global administration team), please
assign `@ChrisZasa` to review.


## Site Preview 

You can follow the build of the site with your post in [GitHub actions](https://github.com/rladies/blog/actions), and see the previewed page once 
it is done building by looking at the Netlify section of the build.


## From Forks

If you are working on a fork of the repository, rather than a branch, you should
PR to the `fork_merge` branch, and notify `@Athanasiamo`.

Previews are only created for branches of this repo, not forks, so she will need
to merge it into a temporary branch to generate the preview.

## Clarification

If anything is unclear in these guidelines, please submit [an issue](https://github.com/rladies/blog/issues) 
so that we can assist you and improve our documentation.
