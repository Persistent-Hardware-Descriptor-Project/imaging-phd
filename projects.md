---
layout: page
title: Projects
permalink: /projects/
---

{% include gantt-chart.html %}

<div class="projects-listing">
  {% assign sorted_categories = site.data.categories | sort: "order" %}
  {% for category in sorted_categories %}
    {% assign category_projects = "" | split: "" %}
    {% for project in site.projects %}
      {% if project.categories contains category.id %}
        {% assign category_projects = category_projects | push: project %}
      {% endif %}
    {% endfor %}
    <details class="category-block category-{{ category.color }}"
             data-category-id="{{ category.id }}"
             data-color="{{ category.color }}">
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
            <h3 class="project-title">
              {% unless project.content == blank %}
                <a href="{{ project.url | relative_url }}">{{ project.title }}</a>
              {% else %}
                {{ project.title }}
              {% endunless %}
            </h3>
            {% if project.status %}
            <span class="project-status status-{{ project.status }}">{{ project.status }}</span>
            {% endif %}
          </div>
          {% if project.description %}
            <p class="project-description">{{ project.description }}</p>
          {% endif %}
          {% unless project.content == blank %}
            <a href="{{ project.url | relative_url }}" class="project-read-more">
              View project →
            </a>
          {% endunless %}
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

<script>
document.addEventListener('DOMContentLoaded', function () {
    var storageKey = 'iphd-open-categories';

    // ── Restore open accordion state from sessionStorage ──────────────────────
    // Keeps whichever categories were open when the user last left this page,
    // so clicking a project and hitting Back (or the ← Return link) restores
    // the view they left.
    var saved = JSON.parse(sessionStorage.getItem(storageKey) || '[]');
    document.querySelectorAll('details.category-block').forEach(function (el) {
        if (saved.includes(el.dataset.categoryId)) {
            el.setAttribute('open', '');
        }
    });

    // ── Persist open state whenever an accordion is toggled ───────────────────
    document.querySelectorAll('details.category-block').forEach(function (el) {
        el.addEventListener('toggle', function () {
            var open = Array.from(
                document.querySelectorAll('details.category-block[open]')
            ).map(function (d) { return d.dataset.categoryId; });
            sessionStorage.setItem(storageKey, JSON.stringify(open));
        });
    });

    // ── Gantt objective label click → open + scroll to matching accordion ─────
    // The shared key is data-color, which matches between gantt objectives
    // and category <details> blocks (green/red/blue/grey).
    document.querySelectorAll('.gantt-obj-label').forEach(function (label) {
        label.addEventListener('click', function () {
            var color = this.dataset.color;
            var target = document.querySelector(
                'details.category-block[data-color="' + color + '"]'
            );
            if (!target) return;
            target.setAttribute('open', '');
            // Small offset so the summary header isn't hidden under the sticky nav
            var offset = 80;
            var top = target.getBoundingClientRect().top + window.scrollY - offset;
            window.scrollTo({ top: top, behavior: 'smooth' });
        });
    });
});
</script>
