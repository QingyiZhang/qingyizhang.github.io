---
layout: page
title: Wiki
description: 多积累些有用的东西，便于自己随时翻阅
keywords: 维基, Wiki
comments: false
menu: 维基
permalink: /wiki/
---

> 能记住多少命令行和快捷键？能用多少？

<ul class="listing">
{% for wiki in site.wiki %}
{% if wiki.title != "Wiki Template" %}
<li class="listing-item"><a href="{{ site.url }}{{ wiki.url }}">{{ wiki.title }}</a></li>
{% endif %}
{% endfor %}
</ul>
