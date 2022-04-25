# Group webpage

This is the source code of the [group webpage](https://mcgill-nlp.github.io/), which was built using [Jekyll](https://github.com/jekyll/jekyll) and [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes).

## Steps to contribute

For any type of contribution, please follow these steps:
1. [Fork](./fork) the repository.
2. Add your contribution by editing the desired files.
3. Create a pull request: Click on the [Pull Request](https://github.com/McGill-NLP/group-webpage/pulls) tab and select "New pull request". Select the repository you forked and modified.
4. Wait for a team member to review and merge your pull request.

## Add new member

Navigate to [_data/authors.yml](./_data/authors.yml) and add the desired information at the end of the file. It has to follow the following template:

```yaml
<username>:
  name: # Full Name
  role: # One of: "Faculty", "Postdoc", "PhD", "Master", "Undergraduate", "Intern"
  date: "Jan 2042" # When the new member joined the group. Must be in the "MMM YYYY" format, or "Fall"/"Winter" instead of month.
  alumni: false # Whether the new member is an alumni
  avatar: "/assets/images/bio/default.jpg"  # Path to your image
  bio: # Describe about the new member (optional)
  links:  # optional
    - name: "Website"
      url: # Link to the new member's website
    - name: "GitHub"
      url: # Link to the new member's GitHub profile
    - name: "LinkedIn"
      url: # Link to the new member's LinkedIn profile
    - name: "Twitter"
      url: # Link to the new member's Twitter profile
    - name: "Scholar"
      url: # Link to the new member's Google Scholar profile
      icon: "fas fa-fw fa-graduation-cap"  # A custom icon is needed here
```

Replace `<username>` with your firstname or nickname. If someone already has the same name, you can append your lastname and/or start date, to your preference. This will be what you will use when writing a blog post or a publication abstract.

Note that the `avatar` field links to an image located in `assets/images/bio`. You will need to upload the image to the repository before it shows up. Make sure you choose a picture in `jpg` (to save space), an aspect ratio of 1:1, resolution of about 300x300, and mainly centered around the face. In a hurry, you may use the default image.

## Front matters and YAML

For any type of page or post (publication, blog post, course description), we use something called ["Front Matters"](https://jekyllrb.com/docs/front-matter/) to tell Jekyll about the purpose of the file. This is a block of YAML text at the beginning of the file. The rest of the file is regular [markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).

## Modify pages

To modify a page, navigate to [_pages](_pages/) and update the desired file. If you add a new file, you will also need to edit the [_data/navigation.yml](./_data/navigation.yml) file with the correct relative URL.

The following pages are mostly likely to be frequently updated:
* [home](_pages/home.md)
* [contact](_pages/contact.md)

The following pages are not likely to be frequently updated:
* [people](_pages/people.md) 
* [publications](_pages/publications.md)
* [blog](_pages/blog.md)
* [teaching](_pages/teaching.md)

Note: If you want to add new content to one of the pages above, please refer to the section on [creating a post](#creating-a-post).

The following files are only meant to be modified by the site maintainer in rare cases:
* [404](_pages/404.md)
* [category-archive](_pages/category-archive.md)
* [tag-archive](_pages/tag-archive.md)
* [year-archive](_pages/year-archive.md)



## Creating a post

### Publication

To add a link to a publication, create a new file called `<YYYY>-<MM>-<DD>-<shorthand>.md` in the [`_posts/papers` directory](https://github.com/McGill-NLP/group-webpage/tree/master/_posts/papers). Note that `<shorthand>` will determine the URL of the file, so choose carefully.

Every file should start with the following:
```yaml
---
title: "My cool paper" # Add official title
author: <username> # Add name to show profile in sidebar
categories: Publications # Used to list all posts about publications in /publications/
names: "Firstname lastname, Firstname lastname, ..." # names of all authors
link: https://arxiv.org/abs/1234.5678 # link to paper
code: https://github.com/McGill-NLP/example  # link to code (optional)
webpage: https://mcgill-nlp.github.io/project  # link to project (optional)
video: https://youtube.com  # link to video (optional)
twitter: https://twitter.com/username  # link to twitter thread (optional)
demo: https://project-demo.com  # link to interactive demo (optional)
thumbnail: /assets/images/papers/figure.jpg  # link to a thumbnail (optional)
venue: ACL 2022  # venue and year of the paper
tags: ACL # tag of the paper (exclude year, use shorthand)
---
```

Then, it should be followed with the content in markdown:

```markdown

*{{ page.names }}*

**{{ page.venue }}**

{% include display-publication-links.html pub=page %}

## Abstract
<!-- Your abstract here -->
```

Notes:

* `include display-publication-links.html` will display the icons and links to code, webpage, tweets, etc. `pub=page` refers to the page object, which is handled by Jekyll.
* `thumbnail` links to a image located in `assets/images/papers`. If you don't have one, remove that line. You will need to upload the image to the repository before it shows up. Make sure you choose a picture:
  * in `jpg` (to save space), 
  * an aspect ratio of 4:3 (A4 landscape), 
  * resolution of about 800x600, 
  * taken from your paper.

### Blog

To write a blog post, create a new file called `<YYYY>-<MM>-<DD>-<shorthand>.md` in the [`_posts/blog` directory](_posts/blog). Note that `<shorthand>` will determine the URL of the file, so choose carefully.

Every file should start with the following:
```yaml
---
title: "My cool blog post" # Add title
author: <username> # Add your name (see above)
categories: # Used to list all blog posts in /blog/
  - Blog
tags: # Choose tag(s) not clashing with a conference name (optional)
  - Pytorch
excerpt_separator: "<!--more-->"  # Separate the excerpt from the body (optional)
last_modified_at: "2016-03-09" # Add modification date if relevant (optional)
---
```

Followed by the content in markdown:

```markdown
*Your summary here will be previewed on `/publications/`*

<!--more-->

Some starting statement

## Section in the paper

More content.
```

### Teaching
To write a course description, create a new file called `<YYYY>-<MM>-<DD>-<shorthand>.md` in the [`_posts/teaching` directory](_posts/teaching). Note that `<shorthand>` will determine the URL of the file, so choose carefully.

```yaml
---
title: "COMP XYZ - Semester YYYY"  # Add course code, followed by the semester it's taught
author: siva  # Name of the instructor
categories:
  - Teaching  # Used to list all posts describing a course in /teaching/
tags:
  - Winter 2022  # Semester
link: "https://docs.google.com/document/d/..." # Link to an external course description
---
```

Then, add content relevant to the course using markdown below the `---`, e.g.:

```markdown
*summary here*

## Syllabus

Content of syllabus here

```

## Advanced

This section is meant for the maintainer(s) or developers of the site. Please consult the faculty members for more information on how to become a maintainer.

### Setup

You will need to install ruby and gem to use `jekyll` locally. This is only if you want to compile and run this site locally. If you want to modify a markdown file or a yaml file, you don't need to do that; please refer to the sections above for instructions.

For the instructions, see [Jekyll quickstart](https://jekyllrb.com/docs/).

To run the site locally, use the last command in the quickstart:
```bash
bundle exec jekyll serve
```

We use the `minimal-mistakes` theme. Specifically, we use the `remote-theme` installation method, which is why the repo doesn't contain all of the html, css, and yaml files required for the theme. To learn more, read [this minimal-mistakes doc section](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/#remote-theme-method). Note we are using a specific version of the theme, which can be found on `_config.yml`.


### Editing SCSS

If you need to modify some CSS attributes directly, you need to use [sass](https://sass-lang.com/documentation/syntax), or directly write CSS (which is still valid). You can create a new file in [_sass/custom](_sass/custom) and import it inside [_sass/main.scss](_sass/main.scss). Note that all files in [_sass/custom](_sass/custom) were added by the maintainers of this repo, in addition to the original styling provided by minimal-mistakes.

Here's a brief description:
* [_sass/custom/display-publications.scss](_sass/custom/display-publications.scss): Some custom CSS for styling the publications on `/publications/`, which did not have the same format in the original minimal-mistakes theme.
* [_sass/custom/no-sidebar.scss](_sass/custom/no-sidebar.scss): This adds an option to shift the page to the left side when there's no sidebar. Search for `no-sidebar` in [_config.yml](_config.yml) to see how to use it, or read [this post](https://mmistakes.github.io/minimal-mistakes/docs/layouts/#layout-based-and-user-defined-classes).
* [_sass/custom/people-card.scss](_sass/custom/people-card.scss): This is a custom CSS for styling the "cards" for each member in `/people/`.
* [_sass/custom/skin.scss](_sass/custom/skin.scss): This is a custom CSS for styling the skin of the website.

### Custom `_includes/`

`_includes/` contains HTML and MD files that can be called from any page. It's something specific to Jekyll. To use it in your page, simply do:

```markdown
{% include "my-file.html" %}
```

if you have a file at `_includes/my-file.html`. We have 5 custom `include` HTML files for this website. You may take a look at their usage by searching `include <name>.html` across the codebase.

### Custom `_layouts/`

You can create custom html layouts in `_layouts/`. To use them, simply specify, in the front matters of a page:
```yaml
layout: publication
```

where `my-layout.html` is the name of the layout in `_layouts/`. In our case, we have a custom `publications.html` layout for the `/publications/` page.


### Troubleshooting

If you have a question about using Jekyll, start a discussion on the [Jekyll Forum](https://talk.jekyllrb.com/) or [StackOverflow](https://stackoverflow.com/questions/tagged/jekyll). Other resources:

- [Ruby 101](https://jekyllrb.com/docs/ruby-101/)
- [Setting up a Jekyll site with GitHub Pages](https://jekyllrb.com/docs/github-pages/)
- [Configuring GitHub Metadata](https://github.com/jekyll/github-metadata/blob/master/docs/configuration.md#configuration) to work properly when developing locally and avoid `No GitHub API authentication could be found. Some fields may be missing or have incorrect data.` warnings.
