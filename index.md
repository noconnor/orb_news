---
layout: default
title: Orb News
---

{% assign digests = site.pages | where_exp: "p", "p.path contains 'digests/'" | where_exp: "p", "p.name contains '.md'" | where_exp: "p", "p.name != 'latest.md'" | sort: "path" | reverse %}

{% assign latest = digests | first %}

{% if latest %}
<meta http-equiv="refresh" content="0; url={{ site.baseurl }}{{ latest.url }}">
<script>window.location.href = "{{ site.baseurl }}{{ latest.url }}";</script>

Redirecting to [latest digest]({{ site.baseurl }}{{ latest.url }})...
{% else %}

# Orb News

No digests available yet.

{% endif %}
