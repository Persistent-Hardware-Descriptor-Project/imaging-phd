---
layout: page
title: Projects
permalink: /projects/
---

{% include gantt-chart.html %}

<div class="projects-listing">
  {% assign sorted_objectives = site.objectives | sort: "order" %}
  {% for objective in sorted_objectives %}
    {% assign objective_deliverables = "" | split: "" %}
    {% for deliverable in site.deliverables %}
      {% if deliverable.objective == objective.id %}
        {% assign objective_deliverables = objective_deliverables | push: deliverable %}
      {% endif %}
    {% endfor %}

    <details class="category-block category-{{ objective.color }}"
             data-category-id="{{ objective.id }}"
             data-color="{{ objective.color }}">
      <summary class="category-header">
        <span class="category-title">{{ objective.title }}</span>
        <span class="category-count">{{ objective_deliverables.size }} deliverable{% if objective_deliverables.size != 1 %}s{% endif %}</span>
      </summary>

      {% if objective.image %}
        <div class="category-image"><img src="{{ objective.image | relative_url }}" alt="{{ objective.title }}"></div>
      {% endif %}
      {% unless objective.content == blank %}
        <div class="category-description">{{ objective.content }}</div>
      {% endunless %}

      <div class="deliverable-list">
        {% for deliverable in objective_deliverables %}
        <!-- anchor id matches gantt.yml's link: "#deliverable-<id>" -->
        <details class="deliverable-block" id="deliverable-{{ deliverable.deliverable_id }}">
          <summary class="deliverable-header">
            <span class="deliverable-id-badge">{{ deliverable.deliverable_id }}</span>
            <span class="deliverable-title">{{ deliverable.title }}</span>
            {% if deliverable.status %}
              <span class="deliverable-status status-{{ deliverable.status }}">{{ deliverable.status }}</span>
            {% endif %}
          </summary>

          {% if deliverable.description %}
            <p class="deliverable-description">{{ deliverable.description }}</p>
          {% endif %}
          {% unless deliverable.content == blank %}
            <div class="deliverable-body">{{ deliverable.content }}</div>
          {% endunless %}
          <a href="{{ deliverable.url | relative_url }}" class="deliverable-read-more">
            View full deliverable page →
          </a>
          {% if deliverable.outputs %}
          <div class="deliverable-outputs">
            {% for output in deliverable.outputs %}
            <a href="{{ output.url }}" class="output-link" target="_blank">{{ output.label }} ↗</a>
            {% endfor %}
          </div>
          {% endif %}

          <!-- Sub-deliverables: looked up by id, may be shared across multiple Deliverables -->
          {% if deliverable.subdeliverables %}
          <div class="subdeliverable-list">
            {% for sub_id in deliverable.subdeliverables %}
              {% assign sub = site.subdeliverables | where: "id", sub_id | first %}
              {% if sub %}
              <details class="subdeliverable-block">
                <summary class="subdeliverable-header">{{ sub.title }}</summary>
                <div class="subdeliverable-body">{{ sub.content }}</div>
              </details>
              {% endif %}
            {% endfor %}
          </div>
          {% endif %}
        </details>
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
        if (saved.includes(el.dataset.categoryId)) el.setAttribute('open', '');
    });

    // ── Persist open state whenever an accordion is toggled ───────────────────
    document.querySelectorAll('details.category-block').forEach(function (el) {
        el.addEventListener('toggle', function () {
            var open = Array.from(document.querySelectorAll('details.category-block[open]'))
                .map(function (d) { return d.dataset.categoryId; });
            sessionStorage.setItem(storageKey, JSON.stringify(open));
        });
    });

    // ── Gantt objective label click → open + scroll to matching accordion ─────
    // The shared key is data-color, which matches between gantt objectives
    // and category <details> blocks (green/red/blue/grey).
    document.querySelectorAll('.gantt-obj-label').forEach(function (label) {
        label.addEventListener('click', function () {
            var target = document.querySelector('details.category-block[data-color="' + this.dataset.color + '"]');
            if (!target) return;
            target.setAttribute('open', '');
            scrollToWithOffset(target);
        });
    });

    document.querySelectorAll('.gantt-jump-link').forEach(function (el) {
        el.addEventListener('click', function (e) {
            var targetId = this.dataset.target;
            var target = document.getElementById(targetId);
            if (!target) return;
            e.preventDefault();

            target.setAttribute('open', '');
            var parentCategory = target.closest('details.category-block');
            if (parentCategory) parentCategory.setAttribute('open', '');

            scrollToWithOffset(target);
            target.classList.add('deliverable-flash');
            setTimeout(function () { target.classList.remove('deliverable-flash'); }, 1500);
        });
    });

    function scrollToWithOffset(el) {
        var offset = 80;
        var top = el.getBoundingClientRect().top + window.scrollY - offset;
        window.scrollTo({ top: top, behavior: 'smooth' });
    }

    var compactBtn = document.getElementById('gantt-compact-toggle');
    var wrapper = document.getElementById('gantt-wrapper');
    var normalRowHeight = 36;
    var compactRowHeight = 6;

    compactBtn.addEventListener('click', function () {
        var isCompact = wrapper.classList.toggle('gantt-compact');
        compactBtn.setAttribute('aria-pressed', isCompact);
        compactBtn.textContent = isCompact ? 'Expand view' : 'Compact view';

        var rowHeight = isCompact ? compactRowHeight : normalRowHeight;
        wrapper.style.setProperty('--gantt-row-height', rowHeight + 'px');

        document.querySelectorAll('.gantt-obj-label').forEach(function (label) {
            var count = parseInt(label.dataset.deliverableCount, 10);
            label.style.height = (count * rowHeight) + 'px';
        });
    });
});
</script>
