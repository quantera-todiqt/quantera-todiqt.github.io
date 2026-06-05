---
layout: default
title: Events
---

<section class="wrapper style1 fade-up">
<div class="inner">
<h2>Events</h2>
<p>Upcoming workshops, schools, and meetings organised by or involving the QuantERA ToDiQT consortium.</p>

{% if site.data.events %}
{% assign sorted_events = site.data.events | sort: "date" %}
{% else %}
{% assign sorted_events = "" | split: "" %}
{% endif %}

{% if sorted_events.size == 0 %}
<p><em>No events scheduled yet — check back soon.</em></p>
{% else %}

<style>
.event-item {
  display: flex;
  gap: 1.5rem;
  padding: 1.5rem 0;
  border-bottom: 1px solid rgba(255,255,255,.1);
}
.event-item:last-child { border-bottom: none; }
.event-date-block {
  flex-shrink: 0;
  min-width: 68px;
  text-align: center;
  background: rgba(100,200,255,.15);
  border: 1px solid rgba(100,200,255,.3);
  border-radius: 6px;
  padding: .6rem .4rem;
  align-self: flex-start;
}
.event-month { font-size: .65rem; text-transform: uppercase; letter-spacing: .06em; opacity: .8; }
.event-day   { font-size: 1.8rem; font-weight: 700; line-height: 1; }
.event-year  { font-size: .65rem; opacity: .7; }
.event-info h3 { margin: 0 0 .3rem; }
.event-location { font-size: .85rem; opacity: .7; margin-bottom: .4rem; }
.event-tag {
  display: inline-block; font-size: .72rem; padding: .1rem .45rem;
  border-radius: 10px; background: rgba(255,255,255,.1); margin: .2rem .2rem 0 0;
}
@media (max-width: 540px) { .event-item { flex-direction: column; gap: .6rem; } }
</style>

{% for event in sorted_events %}
<div class="event-item">
  <div class="event-date-block">
    <div class="event-month">{{ event.date | date: "%b" }}</div>
    <div class="event-day">{{ event.date | date: "%-d" }}</div>
    <div class="event-year">{{ event.date | date: "%Y" }}</div>
  </div>
  <div class="event-info">
    <h3>{% if event.url and event.url != "" %}<a href="{{ event.url }}">{{ event.title }}</a>{% else %}{{ event.title }}{% endif %}</h3>
    <div class="event-location">{{ event.location }}{% if event.end_date and event.end_date != event.date %} &nbsp;|&nbsp; {{ event.date | date: "%b %-d" }}–{{ event.end_date | date: "%-d, %Y" }}{% else %} &nbsp;|&nbsp; {{ event.date | date: "%B %-d, %Y" }}{% endif %}</div>
    <p style="font-size:.9rem; line-height:1.6; margin:.2rem 0 .5rem;">{{ event.description }}</p>
    {% if event.tags %}{% for tag in event.tags %}<span class="event-tag">{{ tag }}</span>{% endfor %}{% endif %}
  </div>
</div>
{% endfor %}
{% endif %}

</div>
</section>
