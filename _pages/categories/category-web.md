---
title: "Web"
layout: archive
permalink: /categories/Web
toc_sticky: true
author_profile: true
sidebar_main: true
---

{% assign posts = site.categories.Web| sort:"order" %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}
