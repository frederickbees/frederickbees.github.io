---
title: Outreach
permalink: /outreach/
kicker: What we do
heading: We show up
heading_em: with bees.
lede: From library story time to the Great Frederick Fair, FCBA runs public-facing programs all year. Here's what we offer — and how to book us.
---

## Programs at a glance

<div class="honeycomb" style="margin:2rem 0">
{% for card in site.data.what_we_do %}
  <article class="hc-card">
    <span class="icon"><svg width="40" height="40"><use href="#ic-{{ card.icon }}"/></svg></span>
    <h3>{{ card.title }}</h3>
    <p>{{ card.body | markdownify | remove: '<p>' | remove: '</p>' }}</p>
    <a class="more" href="{{ card.link_url | relative_url }}">{{ card.link_label }}</a>
  </article>
{% endfor %}
</div>

## Book an outreach event

We love doing school visits, scout talks, library demos, garden-club
presentations, and festival booths. Typical formats:

- **Classroom visit** (30–45 min) — observation hive, beekeeping gear to
  handle, Q&A. K–12.
- **Library / community talk** (45–60 min) — slides, samples, honey
  tasting. All ages.
- **Festival booth** — honey sales, observation hive, kids' activities.

Email [{{ site.data.contacts.general.email }}](mailto:{{ site.data.contacts.general.email }})
at least **four weeks ahead**. We'll match you with a volunteer who
lives near you.
