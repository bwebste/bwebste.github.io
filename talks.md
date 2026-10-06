---
layout: single
title: Talks
permalink: /talks/
author_profile: true
---

Recordings and slides from some of my talks that are available online, newest first.  A fuller list of talks is in my [CV](/CV.pdf).

{% assign talks_by_year = site.data.talks | group_by_exp: "t", "t.date | slice: 0, 4" %}
{% for year in talks_by_year %}
## {{ year.name }}
{% for t in year.items %}
{%- capture links -%}
{%- if t.video %} · [video]({{ t.video }}){% endif -%}
{%- for v in t.videos %} · [{{ v.label }}]({{ v.url }}){% endfor -%}
{%- if t.slides %} · [slides]({{ t.slides }}){% endif -%}
{%- endcapture -%}
{%- if t.date.size == 7 %}{% assign when = t.date | append: "-01" | date: "%B %Y" %}{% else %}{% assign when = t.date | date: "%B %-d, %Y" %}{% endif %}
- **{{ t.title }}**<br>
  {{ t.venue }}, {{ when }}{% if t.notes %} ({{ t.notes }}){% endif %}<br>
  {{ links | remove_first: " · " }}
{% endfor %}
{% endfor %}
