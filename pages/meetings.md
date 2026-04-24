---
title: Meetings
permalink: /meetings/
layout: list
kicker: Monthly meetings
heading: Second Thursday.
heading_em: 7:00 PM. Bring questions.
lede: Our general meetings are open to the public — members, aspiring beekeepers, and curious neighbors all welcome. No RSVP needed.
---

<div class="reveal" style="margin-bottom:3rem">
  <p><strong>Where:</strong> {{ site.club.meeting_venue }}<br>
     <strong>When:</strong> {{ site.club.meeting_schedule }}</p>
</div>

<h2 class="section-title reveal">Upcoming meetings</h2>

<ul class="meeting-list reveal">
{% for m in site.data.meetings %}
  <li class="meeting-row">
    <div class="when">
      <span class="d">{{ m.date | date: "%-d" }}</span>
      <span class="m">{{ m.date | date: "%b %Y" }}</span>
      <span class="t">{{ m.time }}</span>
    </div>
    <div>
      <h3>{{ m.title }}</h3>
      <p class="who">{{ m.speaker }} · {{ m.venue }}</p>
      <p>{{ m.summary | markdownify | remove: '<p>' | remove: '</p>' }}</p>
    </div>
  </li>
{% endfor %}
</ul>
