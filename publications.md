---
layout: default
title: Publications
---

<section class="wrapper style1 fade-up">
<div class="inner">
<h2>Publications</h2>
<p>Publications by QuantERA ToDiQT consortium members. Preprints are available on <a href="https://arxiv.org">arXiv</a>.</p>

{% if site.data.publications %}
{% assign pubs_by_year = site.data.publications | group_by: "year" | sort: "name" | reverse %}
{% else %}
{% assign pubs_by_year = "" | split: "" %}
{% endif %}

{% if pubs_by_year.size == 0 %}
<p><em>No publications listed yet — check back soon.</em></p>
{% endif %}

{% for year_group in pubs_by_year %}
<h3>{{ year_group.name }}</h3>
<div class="table-wrapper">
  <table>
    <tbody>
      {% for pub in year_group.items %}
      <tr>
        <td>
          <strong>{{ pub.title }}</strong><br/>
          <em>{{ pub.authors }}</em><br/>
          {{ pub.venue }}
          {% if pub.tags %}
          <br/>
          {% for tag in pub.tags %}
          <span style="display:inline-block;font-size:.75rem;padding:.1rem .45rem;border-radius:10px;background:rgba(255,255,255,.1);margin:.2rem .2rem 0 0;">{{ tag }}</span>
          {% endfor %}
          {% endif %}
          <br/>
          {% if pub.arxiv and pub.arxiv != "" %}
          <a href="{{ pub.arxiv }}" class="button small" style="margin-top:.5rem;">arXiv</a>
          {% endif %}
          {% if pub.doi and pub.doi != "" %}
          <a href="{{ pub.doi }}" class="button small" style="margin-top:.5rem;">DOI</a>
          {% endif %}
        </td>
      </tr>
      {% endfor %}
    </tbody>
  </table>
</div>
{% endfor %}

</div>
</section>
