---
# INSTRUCTIONS
# ------------
# Copy this file, rename it using the convention: short-deliverable-name.md
# Fill in all fields below. Delete any lines you don't need.
#
# deliverable_id MUST match the id used for this deliverable in _data/gantt.yml
#   (e.g. "1-1", "2-3", "4-2")
# objective MUST match the id of one file in _objectives/ (e.g. "obj-1")
# subdeliverables is a list of ids from _subdeliverables/*.md — a sub-deliverable
#   id can be listed here AND in another deliverable's list; the same content
#   will render in both places (and at its own standalone URL).

layout: deliverable
title: "Deliverable Title"
description: "A short description — one or two sentences. Appears in the listing card."
deliverable_id: "1-1"
objective: obj-1
subdeliverables: []          # e.g. [framework-model-presentation, stakeholder-review]
status: "active"    # active | development | support | complete | planned
# Output links — delete any you don't need
outputs:
  - label: "Website"
    url: "http://www.somesite.com"
  - label: "GitHub"
    url: "https://github.com/placeholder"
  - label: "Publication"
    url: "https://doi.org/placeholder"
  - label: "Documentation"
    url: "https://placeholder.org"
---

Deliverable description goes here. This body content appears on the individual
deliverable page at /deliverables/short-deliverable-name/ AND inline in the
Projects accordion (but not in the listing card, which uses `description` above).
