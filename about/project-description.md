---
layout: page
title: Project Description
permalink: /about/project-description/

merit_headers: ["Merit Area", "Imaging-PHD Contribution"]
merits:
    - area: "Democratizing Scientific Infrastructure"
      contribution: |
        "Makes detailed, standardized instrument metadata openly available via persistent identifiers. Enables smaller labs and under-resourced institutions to build on others' hardware setups."
    - area: "Ensuring Long-Term Research Quality"
      contribution: |
        "PHDs improve instrument lifecycle tracking and quality assurance, supporting replicability and reducing hidden sources of error."
    - area: "Enabling Workforce Development"
      contribution: |
        "Empowers core facility staff and early-career researchers with tools and training for metadata best practices."
    - area: "Catalyzing New Discovery"
      contribution: |
        "Harmonized metadata enables data pooling and cross-study reanalysis, accelerating multi-institutional discoveries."

impact_headers: ["Who Benefits", "How Imaging-PHD Helps"]
impacts:
    - who: "Researchers"
      how: |
        "Gain access to well-documented instrument configurations,improving reproducibility and enabling meta-analyses."
    - who: "Educators & Trainees"
      how: |
        "Use PHD-linked metadata for real-world training on instrumentation and FAIR practices."
    - who: "Core Facility Staff"
      how: |
        "Receive credit for their contributions via PID linkage and gain tools for quality tracking."
    - who: "Under-resourced Institutions"
      how: |
        "Can reuse metadata and design experiments modeled after advanced facilities."
    - who: "Software Developers & Industry Partners"
      how: |
        "Integrate their tools with standardized APIs, enhancing interoperability and adoption."
---
{% include mermaid.html %}

<div class="mermaid">
graph LR
    A[Instrument] --> B[Metadata]
    B --> C[Persistent ID]
    C --> D[Publication]
    D --> E[Reuse]
</div>


Our technical design promotes long-term reuse, community adoption, and the scalability of reproducible research.

{% assign rows = page.merits %}

<table>
  {% for row in rows %}
    {% if forloop.first %}
    <tr>
      {% for header in page.merit_headers %}
        <th>{{ header }}</th>
      {% endfor %}
    </tr>
    {% endif %}
    {% tablerow pair in row %}
      {{ pair[1] }}
    {% endtablerow %}
  {% endfor %}
</table>

Broader impact is embedded in every layer of our platform—tools, people, and community.

{% assign rows = page.impacts %}

<table>
  {% for row in rows %}
    {% if forloop.first %}
    <tr>
      {% for header in page.impact_headers %}
        <th>{{ header }}</th>
      {% endfor %}
    </tr>
    {% endif %}
    {% tablerow pair in row %}
      {{ pair[1] }}
    {% endtablerow %}
  {% endfor %}
</table>