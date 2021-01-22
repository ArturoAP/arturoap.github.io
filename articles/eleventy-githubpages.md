---
title: Publish your eleventy site on github pages
description: Work around the github + jekyll settings and get your eleventy site up and running on githubpages
date: 2021-01-10
tags:
  - eleventy
  - github
---

So you've decided to build your site/blog using eleventy and now that you want to publish on github pages, you find out its not working, get constant 404s or get github build error messsages that leave you wondering, which config am I missing?, is there something wrong with my code?, isn't it supposed to just work? its just a static site after all.

Well fear no more the following guide will show you the way on how to configure github and eleventy without the need of external tools, or cumbersome process.

## No Jekyll
The first step is to tell github that our site is not based on jekyll source, to do so you simply add an empty `.nojekyll` file to the root directory of the repo ... thats it.

## Github Source
Next step is to configure where the static pages are located, Github repo settings allows you to choose any branch and a folder either `root` (default) or `docs` as the static pages source, for the purpose of this article we're going to go with `master` branch and `docs` folder.

## Eleventy
Now that our repo has been configured we have to tell Eleventy where to put our static pages, to do so we head over to `.eleventy.js` and modify/add the output configuration:

``` javascript/6
module.exports = function(eleventyConfig) {
  return {
    dir: {
      input: ".",
      includes: "_includes",
      data: "_data",
      output: "docs"
    }
  };
};
```

Next time you run eleventy it will output the generated files to docs folder, if it doesn't create the directory for you you can just add it manually.

## Workflow

