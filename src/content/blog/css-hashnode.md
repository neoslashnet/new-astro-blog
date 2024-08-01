---
title: "Custom CSS For Your Hashnode Blog"
pubDate: 2021-03-21
intro: How to add custom CSS for your Hashnode blog
author: dg
tag: Networking, Fortinet
image: ../../assets/css.jpg
---

---
title: "Custom CSS For Your Hashnode Blog"
pubDate: 2021-03-21
intro: How to add custom CSS for your Hashnode blog
author: dg
tag: Networking, Fortinet
image: ../../assets/checklist.jpg
---

# Introduction

Last year I decided to move my blog over to Hashnode from Stackbit. I liked several aspects of Stackbit but felt like I needed a fresh start. I absolutely love the Hashnode platform. It has a wonderful, growing community and makes it easy to focus on your content rather than other elements of running a blog.

While there are several elements of Hashnode I enjoy, at the end of the day, **I'm not a developer!** Initially I felt like other IT folks would jump onboard, but that hasn't been the case. No one has ever mentioned anything to me about this, but I've felt a little out of place.

# Current State

For the last couple months I've been looking at going out on my own again. I ended up choosing to do my own thing on Vercel and use GitHub. I spent some time (Which I enjoy) tweaking the site and making it my own. I'm very happy how its turned out.

While going through this process I decided to use custom CSS on my Hashnode blog just to see what it would look like. Please note in order to use CSS you need to become an [Ambassador](https://hashnode.com/ambassador).

I may end up keeping my Hashnode blog for sharing some Python projects I plan to do but in any case, I thought I'd share my CSS so others can see how to customize their blog.

## Home Page

```bash
.blog-theme-switcher {
    display: none;
}
.blog-post-card-title {
    font-family: 'Montserrat', sans-serif;
}
.blog-author-area {
    font-family: 'Montserrat', sans-serif;
}
.blog-content-area {
     font-family: 'Montserrat', sans-serif;
     background-color: #111827;
}
.blog-post-card-brief {
     font-family: 'Montserrat', sans-serif;
     font-size: 0.9rem;
}
.blog-content-main {
    font-family: 'Montserrat', sans-serif;
    background-color: #111827;
}
.dark .bg-white {
    background-color: #111827;
}

.blog-author-card {
    background-color: #111827;
}
.blog-followers-count {
    display:none;
}
.blog-body {
    background-color: #111827;
}
.dark .blog-footer-area {
    background-color: #111827;
}
```

## Articles Page

```bash
.blog-theme-switcher {
    display: none;
}
.blog-post-card-title {
    font-family: 'Montserrat', sans-serif;
}
.blog-author-area {
    font-family: 'Montserrat', sans-serif;
    
}
.blog-content-area {
     font-family: 'Montserrat', sans-serif;
     background-color: #111827;
}
.blog-post-card-brief {
     font-family: 'Montserrat', sans-serif;
     font-style: italic;
}
.blog-content-main {
    font-family: 'Montserrat', sans-serif;
    background-color: #111827;
}
.dark .bg-white {
    background-color: #111827;
}

.blog-author-card {
    background-color: #111827;
}
.blog-followers-count {
    display:none;
}
.blog-body {
    background-color: #111827;
}
.dark .blog-footer-area {
    background-color: #111827;
}
.dark\:prose-dark {
    font-family: 'Montserrat', sans-serif;
    color: #babdc4;
}

.blog-similar-article {
    font-family: 'Montserrat', sans-serif;
}
```

## Pages Page

```bash
.blog-theme-switcher {
    display: none;
}
.blog-post-card-title {
    font-family: 'Montserrat', sans-serif;
}
.blog-author-area {
    font-family: 'Montserrat', sans-serif;
    
}
.blog-content-area {
     font-family: 'Montserrat', sans-serif;
     background-color: #111827;
}
.blog-post-card-brief {
     font-family: 'Montserrat', sans-serif;
     font-style: italic;
}
.blog-content-main {
    font-family: 'Montserrat', sans-serif;
    background-color: #111827;
}
.dark .bg-white {
    background-color: #111827;
}

.blog-author-card {
    background-color: #111827;
}
.blog-followers-count {
    display:none;
}
.blog-body {
    background-color: #111827;
}
.dark .blog-footer-area {
    background-color: #111827;
}
.dark\:prose-dark {
    font-family: 'Montserrat', sans-serif;
    color: #babdc4;
}

.dark .blog-subscription-form {
    background-color: #111827;
}
```

Thanks for reading and good luck on your blogging journey!