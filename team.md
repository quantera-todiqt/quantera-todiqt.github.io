---
layout: default
title: Team
---

<section class="wrapper style1 fade-up">
<div class="inner">
<h2>Research Team</h2>
<p>The QuantERA ToDiQT consortium brings together five leading research groups working on device-independent quantum technologies.</p>

<style>
.team-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}
.team-card {
  background: rgba(255,255,255,0.05);
  border: 1px solid rgba(255,255,255,0.1);
  border-radius: 6px;
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
.team-card-header {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
}
.team-photo {
  width: 135px;
  height: 135px;
  object-fit: cover;
  object-position: top center;
  border-radius: 4px;
  flex-shrink: 0;
}
.team-photo-placeholder {
  width: 135px;
  height: 135px;
  background: rgba(255,255,255,0.1);
  border-radius: 4px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2rem;
  color: rgba(255,255,255,0.3);
}
.team-name { margin: 0 0 .2rem; font-size: 1.1rem; }
.team-role { font-size: .85rem; opacity: .7; margin-bottom: .15rem; }
.team-institution { font-size: .8rem; opacity: .6; }
.coordinator-badge {
  display: inline-block;
  font-size: .7rem;
  padding: .1rem .45rem;
  border-radius: 10px;
  background: rgba(100,200,255,.2);
  color: #64c8ff;
  margin-top: .3rem;
}
.team-links { display: flex; gap: .5rem; flex-wrap: wrap; margin-top: auto; }
.team-links a.button { font-size: .75rem; padding: .3rem .8rem; }
</style>

<div class="team-grid">
{% for member in site.data.team %}
<div class="team-card">
  <div class="team-card-header">
    {% if member.image and member.image != "" %}
    <img class="team-photo" src="{{ member.image | relative_url }}" alt="{{ member.name }}" />
    {% else %}
    <div class="team-photo-placeholder">?</div>
    {% endif %}
    <div>
      <h3 class="team-name">{{ member.name }}</h3>
      <div class="team-role">{{ member.role }}</div>
      <div class="team-institution">{{ member.institution }}</div>
      {% if member.coordinator %}<span class="coordinator-badge">Coordinator</span>{% endif %}
    </div>
  </div>
  <p style="font-size:.9rem; line-height:1.6; margin:0;">{{ member.description }}</p>
  <div class="team-links">
    {% if member.website and member.website != "" %}
    <a href="{{ member.website }}" class="button small">Website</a>
    {% endif %}
    {% if member.arxiv and member.arxiv != "" %}
    <a href="{{ member.arxiv }}" class="button small">arXiv</a>
    {% endif %}
  </div>
</div>
{% endfor %}
</div>

</div>
</section>
