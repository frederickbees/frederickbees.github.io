---
title: Contacts
permalink: /contacts/
kicker: Who's who
heading: People to ask
heading_em: about things.
lede: The easiest way to reach the club is the contact form, but if you want a specific human, start here.
---

<div class="contact-grid">
{% for officer in site.data.contacts.board %}
  <div class="contact-card">
    <p class="role">{{ officer.role }}</p>
    <p class="name">{{ officer.name }}</p>
    <a href="mailto:{{ officer.email }}">{{ officer.email }}</a>
  </div>
{% endfor %}
</div>

## General inquiries

For anything that isn't role-specific, email
**[{{ site.data.contacts.general.email }}](mailto:{{ site.data.contacts.general.email }})**
or use the [contact form]({{ '/contact/' | relative_url }}).

### Mailing address

<pre style="font-family:var(--font-sans); background:var(--paper-2); border:1px solid var(--rule); padding:1rem; border-radius:var(--radius)">{{ site.data.contacts.general.mailing_address }}</pre>
