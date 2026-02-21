---
layout: default
title: Lecture Materials
permalink: /lecture-materials/
---

# Lecture Materials

Lecture materials for this course are given below.

<table class="materials-table">
  <thead>
    <tr>
      <th>Topic</th>
      <th>Course Materials</th>
    </tr>
  </thead>
  <tbody>
  {% for row in site.data.lecture_materials %}
    <tr>
      <td class="topic-col">{{ row.topic }}</td>

      <td class="materials-col">
        <ol class="lecture-list">
          {% for l in row.links %}
            <li><a href="{{ l.url | relative_url }}">{{ l.label }}</a></li>
          {% endfor %}

          {% if row.additional and row.additional.size > 0 %}
            <li>
              <strong>Additional Materials:</strong>
              <ul>
                {% for a in row.additional %}
                  <li><a href="{{ a.url }}">{{ a.label }}</a></li>
                {% endfor %}
              </ul>
            </li>
          {% endif %}
        </ol>
      </td>
    </tr>
  {% endfor %}
  </tbody>
</table>
