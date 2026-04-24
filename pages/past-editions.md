---
title: Past Editions
permalink: /past-editions/
layout: list
kicker: Fifty years
heading: Past
heading_em: editions.
lede: A short history of our recent years — speakers, themes, and the quiet milestones the club has hit along the way.
---

<ul class="meeting-list reveal">
{% for ed in site.data.past_editions %}
  <li class="meeting-row">
    <div class="when">
      <span class="d">{{ ed.year }}</span>
      <span class="m">Edition</span>
    </div>
    <div>
      <h3>{{ ed.theme }}</h3>
      <p>{{ ed.highlights }}</p>
    </div>
  </li>
{% endfor %}
</ul>
