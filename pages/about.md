---
layout: page
title: About
description: 瞎折腾
keywords: kubi
comments: false
menu: 关于
permalink: /about/
---

一名爱折腾的技术男，技术不精，慢慢学，不断学


## 联系

{% for website in site.data.social %}
* {{ website.sitename }}：[@{{ website.name }}]({{ website.url }})
{% endfor %}

## Skill Keywords

{% for category in site.data.skills %}
### {{ category.name }}
<div class="btn-inline">
{% for keyword in category.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
