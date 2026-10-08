---
layout: page
permalink: /noticias/
title: Notícias
eyebrow: Ciência e tecnologia de vidros
lead: "Notícias, descobertas e avanços sobre vidros, no Brasil e no exterior, selecionados pela REBRAPEV."
---
{%- comment -%}
  Each news item is a file in _noticias/ (see README.md). The most recent
  item is shown as a larger card; the others follow, newest first.
{%- endcomment -%}
{%- assign items = site.noticias | sort: 'date' | reverse -%}
{%- assign latest = items | first %}

<div class="event-index">
{%- if items.size == 0 %}
<p class="event-empty">Nenhuma notícia publicada até o momento.</p>
{%- else %}
<div class="event-list">
{% include news-card.html item=latest heading='h2' featured=true %}
</div>
{%- if items.size > 1 %}
<h2 class="news-older">Notícias anteriores</h2>
<div class="event-list">
{%- for item in items offset: 1 %}
{% include news-card.html item=item heading='h3' %}
{%- endfor %}
</div>
{%- endif %}
{%- endif %}
</div>
