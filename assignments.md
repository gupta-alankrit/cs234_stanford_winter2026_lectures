---
layout: default
title: Assignments
permalink: /assignments/
---

# Assignments

## Assignments and Due Dates

<table class="assignments-table">
  <thead>
    <tr>
      <th>Event</th>
      <th>Status</th>
    </tr>
  </thead>
  <tbody>
  {% for a in site.data.assignments %}
    <tr>
      <td class="event-col">{{ a.event }}</td>
      <td class="status-col">
        {% for line in a.status_lines %}
          <div class="status-line">
            {% for p in line.parts %}
              {% if p.url and p.url != "" and p.label %}
                {% if p.url contains "://" %}
                  <a href="{{ p.url }}">{{ p.label }}</a>
                {% else %}
                  <a href="{{ p.url | relative_url }}">{{ p.label }}</a>
                {% endif %}
              {% elsif p.text %}
                {{ p.text }}
              {% elsif p.label %}
                {{ p.label }}
              {% endif %}
            {% endfor %}
          </div>
        {% endfor %}
      </td>
    </tr>
  {% endfor %}
  </tbody>
</table>
