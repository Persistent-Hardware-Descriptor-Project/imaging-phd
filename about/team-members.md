---
layout: page
title: Team Members
permalink: /about/team-members/
---

Our team brings together expertise in molecular cell biology, microscopy, bioimage-informatics, and cyberinfrastructure. 


{% assign sc_members = site.team | where_exp: "member", "member.sc == true" %}
{% assign team_members = site.team | where_exp: "member", "member.sc != true" %}

{% if sc_members.size > 0 %}
<details class="category-block" open>
  <summary class="category-header">
    <span class="category-title">Steering Committee</span>
    <span class="category-count">{{ sc_members.size }} member{% if sc_members.size != 1 %}s{% endif %}</span>
  </summary>
  <div class="team-container" id="team-list">
  {% for member in sc_members %}
  <div class="team-list-item">
    {% if member.photo %}
    <img src="{{ member.photo | relative_url }}" alt="Photo of {{ member.name }}" class="team-list-photo">
    {% else %}
    <div class="team-list-photo team-photo-placeholder"></div>
    {% endif %}
    <div class="team-list-info">
      <h3><a href="{{ member.url | relative_url }}">{{ member.name }}</a></h3>
      <p class="team-title">{{ member.title }}</p>
      {% if member.bio %}<p class="team-bio">{{ member.bio }}</p>{% endif %}
      <div class="team-links">
        {% if member.email %}<a href="mailto:{{ member.email }}" class="team-link">Email</a>{% endif %}
        {% if member.orcid %}<a href="https://orcid.org/{{ member.orcid }}" class="team-link">ORCID</a>{% endif %}
        {% if member.scholar %}<a href="{{ member.scholar }}" class="team-link">Google Scholar</a>{% endif %}
        {% if member.github %}<a href="{{ member.github }}" class="team-link">GitHub</a>{% endif %}
        {% if member.linkedin %}<a href="{{ member.linkedin }}" class="team-link">LinkedIn</a>{% endif %}
        {% if member.website %}<a href="{{ member.website }}" class="team-link">Website</a>{% endif %}
      </div>
    </div>
  </div>
  {% endfor %}
  </div>
</details> {% endif %} {% if team_members.size > 0 %}
<details class="category-block" open>
  <summary class="category-header">
    <span class="category-title">Team Members</span>
    <span class="category-count">{{ team_members.size }} member{% if team_members.size != 1 %}s{% endif %}</span>
  </summary>
  <div class="team-container" id="team-members-list">
    {% for member in team_members %}
    <div class="team-list-item">
      {% if member.photo %}
      <img src="{{ member.photo | relative_url }}" alt="Photo of {{ member.name }}" class="team-list-photo">
      {% else %}
      <div class="team-list-photo team-photo-placeholder"></div>
      {% endif %}
      <div class="team-list-info">
        <h3><a href="{{ member.url | relative_url }}">{{ member.name }}</a></h3>
        <p class="team-title">{{ member.title }}</p>
        {% if member.bio %}<p class="team-bio">{{ member.bio }}</p>{% endif %}
        <div class="team-links">
          {% if member.email %}<a href="mailto:{{ member.email }}" class="team-link">Email</a>{% endif %}
          {% if member.orcid %}<a href="https://orcid.org/{{ member.orcid }}" class="team-link">ORCID</a>{% endif %}
          {% if member.scholar %}<a href="{{ member.scholar }}" class="team-link">Google Scholar</a>{% endif %}
          {% if member.github %}<a href="{{ member.github }}" class="team-link">GitHub</a>{% endif %}
          {% if member.linkedin %}<a href="{{ member.linkedin }}" class="team-link">LinkedIn</a>{% endif %}
          {% if member.website %}<a href="{{ member.website }}" class="team-link">Website</a>{% endif %}
        </div>
      </div>
    </div>
    {% endfor %}
  </div>
</details> {% endif %}
