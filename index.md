---
layout: default
title: Orb News — Archive
---

# Archive

{% assign digests = site.pages | where_exp: "p", "p.path contains 'digests/'" | where_exp: "p", "p.name contains '.md'" | where_exp: "p", "p.name != 'latest.md'" | sort: "path" | reverse %}

{% assign current_month = "" %}
{% for digest in digests %}
  {% assign parts = digest.path | split: "/" %}
  {% assign year = parts[1] %}
  {% assign month = parts[2] %}
  {% assign month_key = year | append: "-" | append: month %}
  {% if month_key != current_month %}
    {% assign current_month = month_key %}

### {{ year }}-{{ month }}

  {% endif %}
- [{{ digest.name | replace: ".md", "" }}]({{ digest.url }})
{% endfor %}