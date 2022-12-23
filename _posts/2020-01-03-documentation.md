---
title: Documentation
description: Refer to this post for making changes to your jekyll site.
image: https://picsum.photos/id/180/500/300
layout: page
---

## Features

### Tailwind

The theme is built using TailwindCSS. Customizing the theme to your needs can be done without touching any CSS file.
It also has a **Purge** on build. This way you will be using only the styles that you need.

### Lightning Speed

![Pagespeed](/assets/images/screenshots/pagespeed.png)

### Super Performance, SEO, and Accessibility

![Lighthouse Test](/assets/images/screenshots/lighthouse-test.png)
{: .grid .justify-center}

### Math

Display beautiful math equations using mathjax. This feature can be disabled for performance.

$$ \frac{\sqrt{a^2+b^2}}{ \cos^{-1}\theta \sin^{-1}\theta } $$

### Comments

The theme includes integrated Disqus comments. This can be disabled if needed.

### Installation

Once you extract the theme zip file, run the following commands.

- `npm install`

- `bundle install`

- `npm run dev` for testing the site locally.

- `npm run build`

This will build the HTML site in _/public_ directory. This can be hosted anywhere. Either on conventional hosting or on a static hosting service.

You easily host it as pages using GitHub, Gitlab etc.

In most cases, it is drag-drop upload.

### Usage

The theme uses a centralized data from where you can make almost all the changes to the entire site.

The files that are responsible for the information shown on the website reside in _\_data_ directory as shown below.

```plaintext
├── \_data
| ├── settings.yml
| └── sidebar.yml
| └── about.yml
| └── skills.yml
| └── services.yml
.
.
```

An example of `sidebar.yml` is shown below

```yaml
name: John Owens
image: /path/to/image.img
designations:
  - Teacher
  - Freelancer
  - Blogger
  - Programmer

social:
  - title: LinkedIn
    link: "#"
    icon: fa-linkedin

  - title: Facebook
    link: "#"
    icon: fa-facebook-square

  - title: Twitter
    link: "#"
    icon: fa-twitter-square

  - title: Github
    link: "#"
    icon: fa-github-square

  - title: StackOverflow
    link: "#"
    icon: fa-stack-overflow

sidebar-links:
  - title: Download CV
    link: "#/path/to/pdf"

  - title: Contact me
    link: mailto:your-email.com
```

The above file is responsible for all the elements in the sidebar. Changing it would reflect in the site.

### Color schemes

You can choose from more than 50 color schemes from [tailwind colors](https://tailwindcss.com/docs/customizing-colors){: rel="nofollow noopener noreferrer"}. You can change the color scheme in _\_data/settings.yml_ as shown below.

```yml
color-scheme: blue-500
```

### Contact form

The theme provides a built-in contact form. You will have to add one line in _\_data/settings.yml_ to make it work.

Get an account from formspree.io. Go to integration. Copy the endpoint which would look like this

`https://formspree.io/f/mdowsdwy` and put it in **settings.yml** as shown below

```yml
formspree-action: https://formspree.io/f/mdowsdwy
```

### Skills

Skills can be updated through a file in _\_data/skills.yml_. Here is how it would look like.

```yml
- name: HTML
  skillLevel: 90
  color: "text-red-400"

- name: CSS
  skillLevel: 80
  color: "text-green-400"

- name: JavaScript
  skillLevel: 60
  color: "text-yellow-400"

- name: Python
  skillLevel: 70
  color: "text-indigo-400"

- name: Photoshop
  skillLevel: 70
  color: "text-blue-400"

- name: Svelte
  skillLevel: 50
  color: "text-red-400"
```

You can choose any tailwind class.

> All sections in the website have a file in \_data directory which can be updated.

### Works

You can add new projects or works in _\_works_ directory. You can have markdown files in here just like blog posts.
The index of all works/projects can be found at `/works/`.

### Blog Posts

You can add blog posts in _\_posts_ directory. The index of all the blog posts can be found at `/blog/`.

### Screenshots

![Figs Jekyll Theme online resume cv](/assets/images/screenshots/blue.png){: loading="lazy"}

![Figs Jekyll Theme online resume cv](/assets/images/screenshots/indigo.png){: loading="lazy"}

![Figs Jekyll Theme online resume cv](/assets/images/screenshots/gray.png){: loading="lazy"}

![Figs Jekyll Theme online resume cv](/assets/images/screenshots/green.png){: loading="lazy"}

![Figs Jekyll Theme online resume cv](/assets/images/screenshots/yellow.png){: loading="lazy"}

![Figs Jekyll Theme online resume cv](/assets/images/screenshots/red.png){: loading="lazy"}

{% include cta.html %}
