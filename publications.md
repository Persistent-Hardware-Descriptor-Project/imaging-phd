---
layout: page
title: Publications
permalink: /publications/
sections:
  - heading: "Data Management and Sharing"
    publications:
      - authors: "Bajcsy, P. et al."
        title: "Enabling global image data sharing in the life sciences - peer reviewed"
        journal: "Nat. Methods"
        volume: "22"
        pages: "672–676"
        year: "2025"
        doi_label: "10.1038/s41592-024-02585-z"
        doi_url: "https://doi.org/10.1038/s41592-024-02585-z"
      - authors: "Bialy, N. et al."
        title: "Harmonizing the generation and pre-publication stewardship of FAIR image data"
        journal: "ArXiv"
        year: "2024"
        doi_label: "10.48550/arXiv.2401.13022"
        doi_url: "https://doi.org/10.48550/arXiv.2401.13022"

  - heading: "Community Building"
    publications:
      - authors: "Reis, Y. et al."
        title: "People-Centred Funding as a Catalyst for Sustainable Imaging Infrastructure"
        journal: "J. Microsc."
        year: "2024"
        doi_label: "10.1111/jmi.70099"
        doi_url: "https://doi.org/10.1111/jmi.70099"
      - authors: "De Niz, M. et al."
        title: "Building momentum through networks: Bioimaging across the Americas"
        journal: "J. Microsc."
        volume: "294"
        issue: "special issue"
        pages: "420–439"
        year: "2024"
        doi_label: "10.1111/jmi.13318"
        doi_url: "https://doi.org/10.1111/jmi.13318"

  - heading: "Community Guidelines"
    publications:
      - authors: "Montero Llopis, P. et al."
        title: "Better Reporting is Better Science: Community-Defined Minimal Reporting Requirements for Light Microscopy"
        journal: "J. Cell Biol."
        volume: "225"
        pages: "e202601032"
        year: "2026"
        doi_label: "10.1083/jcb.202601032"
        doi_url: "https://doi.org/10.1083/jcb.202601032"
      - authors: "Cimini, B. A. et al."
        title: "The crucial role of bioimage analysts in scientific research and publication"
        journal: "J. Cell Sci."
        volume: "137"
        pages: "jcs262322"
        year: "2024"
        doi_label: "10.1242/jcs.262322"
        doi_url: "https://doi.org/10.1242/jcs.262322"
      - authors: "Schmied, C. et al."
        title: "Community-developed checklists for publishing images and image analyses"
        journal: "Nat. Methods"
        volume: "21"
        year: "2023"
        doi_label: "10.1038/s41592-023-01987-9"
        doi_url: "https://doi.org/10.1038/s41592-023-01987-9"

  - heading: "Data and Metadata Standards"
    publications:
      - authors: "Moxon, S. A. T. et al."
        title: "LinkML: an open data modeling framework"
        journal: "Gigascience"
        volume: "15"
        year: "2026"
        doi_label: "10.1093/gigascience/giad113"
        doi_url: "https://doi.org/10.1093/gigascience/giad113"
      - authors: "Moore, J. et al."
        title: "OME-Zarr: a cloud-optimized bioimaging file format with international community support"
        journal: "Histochem. Cell Biol."
        year: "2023"
        doi_label: "10.1007/s00418-023-02209-1"
        doi_url: "https://doi.org/10.1007/s00418-023-02209-1"

  - heading: "FAIR Facilities and Instruments"
    publications:
      - authors: "Mayernik, M. et al."
        title: "Recommendations Toward a Framework for Adoption and Use of Persistent Identifiers for Research Facilities, Platforms, and Instruments"
        journal: "Zenodo"
        year: "2026"
        doi_label: "10.5281/zenodo.18436644"
        doi_url: "https://doi.org/10.5281/zenodo.18436644"
      - authors: "Mayernik, M. et al."
        title: "FAIR Facilities and Instruments Workshop #3 Report: Synthesizing Community Input Toward Recommendations"
        journal: "University of Colorado Boulder"
        year: "2026"
        doi_label: "10.25810/QYD9-2T28"
        doi_url: "https://doi.org/10.25810/QYD9-2T28"

  - heading: "Research Resource Identification (RRID)"
    publications:
      - authors: "Bandrowski, A."
        title: "A decade of GigaScience: What can be learned from half a million RRIDs in the scientific literature?"
        journal: "Gigascience"
        volume: "11"
        year: "2022"
        doi_label: "10.1093/gigascience/giac058"
        doi_url: "https://doi.org/10.1093/gigascience/giac058"
---

{% for section in page.sections %}
<div>
  <h2>{{ section.heading }}</h2>
  
  {% for pub in section.publications %}
  <div>
    <p>
      {{ pub.authors }} {{ pub.title }}. 
      <i>{{ pub.journal }}</i> {% if pub.volume %}<b>{{ pub.volume }}</b>{% endif %}{% if pub.issue %}({{ pub.issue }}){% endif %}{% if pub.pages %}, {{ pub.pages }}{% endif %} 
      ({{ pub.year }}).
      {% if pub.doi_url %}
        DOI: <a href="{{ pub.doi_url }}" target="_blank">{{ pub.doi_label }}</a>
      {% endif %}
    </p>
  </div>
  {% endfor %}
</div>
{% endfor %}