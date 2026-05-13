---
layout: page
title: Projects
permalink: /projects/
---

<!-- Add any intro text here — appears above the project listing -->

<div class="projects-listing">
  {% assign sorted_categories = site.data.categories | sort: "order" %}
  {% for category in sorted_categories %}
    {% assign category_projects = "" | split: "" %}
    {% for project in site.projects %}
      {% if project.categories contains category.id %}
        {% assign category_projects = category_projects | push: project %}
      {% endif %}
    {% endfor %}
    <details class="category-block">
      <summary class="category-header">
        <span class="category-title">{{ category.title }}</span>
        <span class="category-count">{{ category_projects.size }} project{% if category_projects.size != 1 %}s{% endif %}</span>
      </summary>
      {% if category.description %}
      <div class="category-description">{{ category.description }}</div>
      {% endif %}
      <div class="project-list">
        {% for project in category_projects %}
        <div class="project-item">
          <div class="project-header">
            <h3 class="project-title">{{ project.title }}</h3>
            {% if project.status %}
            <span class="project-status status-{{ project.status }}">{{ project.status }}</span>
            {% endif %}
          </div>
          {% if project.description %}
          <p class="project-description">{{ project.description }}</p>
          {% endif %}
          {% if project.outputs %}
          <div class="project-outputs">
            {% for output in project.outputs %}
            <a href="{{ output.url }}" class="output-link" target="_blank">{{ output.label }} ↗</a>
            {% endfor %}
          </div>
          {% endif %}
        </div>
        {% endfor %}
      </div>
    </details>
  {% endfor %}
</div>