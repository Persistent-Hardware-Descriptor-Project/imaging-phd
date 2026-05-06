---
layout: page
title: Team Members
permalink: /about/team-members/
---

<!-- Add any intro text here — it will appear above the team listing -->
Our team brings together expertise in microscopy, bioinformatics, and cyberinfrastructure. 

---

<!--
<div class="team-view-toggle">
  <button class="toggle-btn active" onclick="setView('list')" id="btn-list">List View</button>
  <button class="toggle-btn" onclick="setView('grid')" id="btn-grid">Grid View</button>
</div>
-->

<div class="team-container" id="team-list">
  {% for member in site.team %}
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

<div class="team-container team-grid" id="team-grid" style="display:none;">
  {% for member in site.team %}
  <div class="team-card">
    {% if member.photo %}
    <img src="{{ member.photo | relative_url }}" alt="Photo of {{ member.name }}" class="team-card-photo">
    {% else %}
    <div class="team-card-photo team-photo-placeholder"></div>
    {% endif %}
    <div class="team-card-info">
      <h3><a href="{{ member.url | relative_url }}">{{ member.name }}</a></h3>
      <p class="team-title">{{ member.title }}</p>
      <div class="team-links">
        {% if member.email %}<a href="mailto:{{ member.email }}" class="team-link">Email</a>{% endif %}
        {% if member.orcid %}<a href="https://orcid.org/{{ member.orcid }}" class="team-link">ORCID</a>{% endif %}
        {% if member.scholar %}<a href="{{ member.scholar }}" class="team-link">Scholar</a>{% endif %}
        {% if member.github %}<a href="{{ member.github }}" class="team-link">GitHub</a>{% endif %}
        {% if member.linkedin %}<a href="{{ member.linkedin }}" class="team-link">LinkedIn</a>{% endif %}
        {% if member.website %}<a href="{{ member.website }}" class="team-link">Website</a>{% endif %}
      </div>
    </div>
  </div>
  {% endfor %}
</div>

<script>
function setView(view) {
  document.getElementById('team-list').style.display = view === 'list' ? 'block' : 'none';
  document.getElementById('team-grid').style.display = view === 'grid' ? 'flex' : 'none';
  document.getElementById('btn-list').classList.toggle('active', view === 'list');
  document.getElementById('btn-grid').classList.toggle('active', view === 'grid');
}
</script>