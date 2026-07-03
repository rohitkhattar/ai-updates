---
layout: page
title: Archive
permalink: /archive/
---

{% assign postsByYear = site.posts | group_by_exp: "post", "post.date | date: '%Y'" %}
{% for year in postsByYear %}
## {{ year.name }}

{% assign postsByMonth = year.items | group_by_exp: "post", "post.date | date: '%B'" %}
{% for month in postsByMonth %}
### {{ month.name }} {{ year.name }}

{% for post in month.items %}
- [{{ post.date | date: "%-d %b" }} — {{ post.title }}]({{ post.url | relative_url }})
{% endfor %}
{% endfor %}
{% endfor %}
