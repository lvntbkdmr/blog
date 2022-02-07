---
title: Customizing your brand and design settings
description: >-
  How to tweak a few settings in Ghost to transform your site from a generic
  template to a custom brand with style and personality.
pagetitle: Customizing your brand and design settings
slug: design
feature_image: https://static.ghost.org/v4.0.0/images/publishing-options.png
lastmod: '2022-01-22T20:09:25.000+00:00'
date: '2022-01-22T20:09:28.000+00:00'
summary: >-
  How to tweak a few settings in Ghost to transform your site from a generic
  template to a custom brand with style and personality.
i18nlanguage: en
weight: 0
draft: false
og_image: >-
  https://cdn.leventbekdemir.comhttps://static.ghost.org/v4.0.0/images/publishing-options.png
categories:
  - Getting Started
authors:
  - id: 5951f5fca366002ebd5dbef7
    name: Ghost
    slug: ghost
    profile_image: https://static.ghost.org/v4.0.0/images/ghost-user.png
    cover_image: null
    bio: You can delete this user to remove all the welcome posts
    website: https://ghost.org
    location: The Internet
    facebook: ghost
    twitter: ghost
    meta_title: null
    meta_description: null
    url: https://leventbekdemir.com/author/ghost/
cover:
  image: https://static.ghost.org/v4.0.0/images/publishing-options.png
  alt: asd
  caption: asd
  relative: false

---
As discussed in the [introduction](https://leventbekdemir.com/design/__GHOST_URL__/welcome/) post, one of the best things about Ghost is just how much you can customize to turn your site into something unique. Everything about your layout and design can be changed, so you're not stuck with yet another clone of a social network profile.

How far you want to go with customization is completely up to you, there's no right or wrong approach! The majority of people use one of Ghost's built-in themes to get started, and then progress to something more bespoke later on as their site grows.

The best way to get started is with Ghost's branding settings, where you can set up colors, images and logos to fit with your brand.

![](https://static.ghost.org/v4.0.0/images/brandsettings.png)

Ghost Admin → Settings → Branding

Any Ghost theme that's up to date and compatible with Ghost 4.0 and higher will reflect your branding settings in the preview window, so you can see what your site will look like as you experiment with different options.

When selecting an accent color, try to choose something which will contrast well with white text. Many themes will use your accent color as the background for buttons, headers and navigational elements. Vibrant colors with a darker hue tend to work best, as a general rule.

Installing Ghost themes
-----------------------

By default, new sites are created with Ghost's friendly publication theme, called Casper. Everything in Casper is optimized to work for the most common types of blog, newsletter and publication that people create with Ghost — so it's a perfect place to start.

However, there are hundreds of different themes available to install, so you can pick out a look and feel that suits you best.

![](https://static.ghost.org/v4.0.0/images/themesettings.png)

Ghost Admin → Settings → Theme

Inside Ghost's theme settings you'll find 4 more official themes that can be directly installed and activated. Each theme is suited to slightly different use-cases.

*   **Casper** _(default)_ — Made for all sorts of blogs and newsletters
*   **Edition** — A beautiful minimal template for newsletter authors
*   **Alto** — A slick news/magazine style design for creators
*   **London** — A light photography theme with a bold grid
*   **Ease** — A library theme for organizing large content archives

And if none of those feel quite right, head on over to the [Ghost Marketplace](https://ghost.org/themes/), where you'll find a huge variety of both free and premium themes.

Building something custom
-------------------------

Finally, if you want something completely bespoke for your site, you can always build a custom theme from scratch and upload it to your site.

Ghost's theming template files are very easy to work with, and can be picked up in the space of a few hours by anyone who has just a little bit of knowledge of HTML and CSS. Templates from other platforms can also be ported to Ghost with relatively little effort.

If you want to take a quick look at the theme syntax to see what it's like, you can [browse through the files of the default Casper theme](https://github.com/tryghost/casper/). We've added tons of inline code comments to make it easy to learn, and the structure is very readable.

    {{#post}}
    <article class="article {{post_class}}">
    
        <h1>{{title}}</h1>
        
        {{#if feature_image}}
        	<img src="{{feature_image}}" alt="Feature image" />
        {{/if}}
        
        {{content}}
    
    </article>
    {{/post}}

A snippet from a post template

See? Not that scary! But still completely optional.

If you're interested in creating your own Ghost theme, check out our extensive [theme documentation](https://ghost.org/docs/themes/) for a full guide to all the different template variables and helpers which are available.
