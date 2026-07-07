---
# INSTRUCTIONS
# ------------
# Copy this file, rename it using the convention: obj-N-short-name.md
# id and color MUST match the corresponding objective entry in _data/gantt.yml
# order controls display order on /projects/
# This file's standalone page now lives at /objectives/short-name/ (flat,
# not nested under /projects/ — see the naming-consistency pass).

obj_id: obj-1                # must match objectives[].id in _data/gantt.yml
title: "1 - Definition of NGM"
order: 1
color: green              # must match objectives[].color in _data/gantt.yml — green | red | blue | grey
image: /assets/images/objectives/placeholder.png   # optional — delete this line if not needed
---

Objective description goes here. This is the full body — write as much text as you
need, and add images inline with standard markdown or an HTML <img> tag, e.g.:

![Alt text describing the image](/assets/images/objectives/placeholder.png)

This content renders inside the Objective's accordion header on /projects/.
