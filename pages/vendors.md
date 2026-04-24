---
title: Vendors
permalink: /vendors/
layout: list
kicker: Gear & suppliers
heading: Where to
heading_em: buy the stuff.
lede: A non-exhaustive list of the vendors our members actually use. No affiliate links, no kickbacks — just honest recommendations from a room full of opinionated beekeepers.
---

<ul class="plain-list reveal">
{% for v in site.data.vendors %}
  <li>
    <strong>{% if v.url != '#' %}<a href="{{ v.url }}" target="_blank" rel="noopener">{{ v.name }} ↗</a>{% else %}{{ v.name }}{% endif %}</strong>
    <p>{{ v.desc }}</p>
  </li>
{% endfor %}
</ul>

<p style="margin-top:2rem; color:var(--muted); font-size:.9rem"><em>Think something's missing? Tell us at the next meeting and we'll add it.</em></p>
