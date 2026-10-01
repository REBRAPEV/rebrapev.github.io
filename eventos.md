---
layout: page
permalink: /eventos/
title: Eventos e reuniões
eyebrow: Agenda
lead: "Reuniões da rede, escolas, encontros científicos e outras atividades de interesse da comunidade."
---
{%- comment -%}
  Each event is a file in _eventos/ (see README.md). GitHub Pages builds the
  site statically, so "upcoming" versus "past" is decided at build time
  (site.time): an event stays under "Próximos eventos" until the next build
  after its last day (end_date, or date for one-day events).
{%- endcomment -%}
{%- assign today = site.time | date: '%Y-%m-%d' -%}
{%- assign upcoming = '' | split: '' -%}
{%- assign past = '' | split: '' -%}
{%- assign sorted_events = site.eventos | sort: 'date' -%}
{%- for ev in sorted_events -%}
  {%- assign last_day = ev.end_date | default: ev.date | date: '%Y-%m-%d' -%}
  {%- if last_day >= today -%}
    {%- assign upcoming = upcoming | push: ev -%}
  {%- else -%}
    {%- assign past = past | unshift: ev -%}
  {%- endif -%}
{%- endfor %}

<div class="event-index">
<h2 id="proximos-eventos">Próximos eventos</h2>
{%- if upcoming.size > 0 %}
<div class="event-list">
{%- for ev in upcoming %}
{% include event-card.html event=ev heading='h3' %}
{%- endfor %}
</div>
{%- else %}
<p class="event-empty">Não há eventos programados no momento.</p>
{%- endif %}

<h2 id="eventos-realizados">Eventos realizados</h2>
{%- if past.size == 0 %}
<p class="event-empty">Nenhum evento realizado até o momento.</p>
{%- endif %}
{%- assign current_year = '' -%}
{%- for ev in past -%}
  {%- assign year = ev.date | date: '%Y' -%}
  {%- if year != current_year -%}
    {%- unless forloop.first %}
</div>
    {%- endunless %}
<h3 class="event-year">{{ year }}</h3>
<div class="event-list">
    {%- assign current_year = year -%}
  {%- endif %}
{% include event-card.html event=ev heading='h4' %}
  {%- if forloop.last %}
</div>
  {%- endif -%}
{%- endfor %}
</div>
