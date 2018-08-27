---
layout: "post"
title: "Jotform coding into site"
date: "2018-08-17 15:49:00"
expire_date: 2018-11-07 13:00:00
image: 
news_image_alt: 'Photo of issue'
article_lead: >-
  IE issue search box . . .
video_content: false
video_link: ''
categories: server
---

# Jotform coding into our static Jekyll sites
Getting Jotform into our Jekyll sites as we don't want to use iframes in the compiled pages on the site. This came up as we were testing between Target x and Jotform.

## Get code out of Jotform

To get the code out of Jotform we need to:
1. hit publish
2. Click on the link.
3. Click view source
4. Copy and save out to html page.

## Jotform Jotform into our code with Jquery

We need to make the code work as it is using $ sign and our jquery is as well which is causing a conflict.
