---
title: Contact
permalink: /contact/
kicker: Get in touch
heading: Say hello.
heading_em: We read everything.
lede: For most questions, the fastest path is email. For swarms, use the bee removal form — it reaches a volunteer immediately.
---

## Common paths

- **Report a swarm:** [Bee Removal form ↗]({{ site.club.bee_removal_form }}){:target="_blank" rel="noopener"}
- **Join or renew:** [{{ '/join/' | relative_url }}]({{ '/join/' | relative_url }})
- **Ask about classes:** [{{ site.data.contacts.general.email }}](mailto:{{ site.data.contacts.general.email }})
- **Board &amp; officers:** [{{ '/contacts/' | relative_url }}]({{ '/contacts/' | relative_url }})

## General email

**[{{ site.data.contacts.general.email }}](mailto:{{ site.data.contacts.general.email }})** — reaches the board.

## Mailing address

<pre style="font-family:var(--font-sans); background:var(--paper-2); border:1px solid var(--rule); padding:1rem; border-radius:var(--radius)">{{ site.data.contacts.general.mailing_address }}</pre>

## Social

{% for s in site.data.contacts.general.social %}
- [{{ s.label }} ↗]({{ s.url }}){:target="_blank" rel="noopener"}
{% endfor %}
