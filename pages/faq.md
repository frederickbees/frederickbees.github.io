---
title: FAQ
permalink: /faq/
layout: list
kicker: FAQ
heading: Things everyone
heading_em: quietly Googles.
lede: If your question isn't here, bring it to the next meeting — half our members are just collected Q&A in human form.
---

<div class="faq reveal">
{% for item in site.data.faqs %}
  <div class="faq-item">
    <button class="faq-q">{{ item.q }}</button>
    <div class="faq-a">{{ item.a | markdownify }}</div>
  </div>
{% endfor %}
</div>
