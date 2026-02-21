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

          {%- for l in row.links -%}

            {%- comment -%}
            Supports TWO formats in lecture_materials.yml:

            (A) Old format:
              - label: "Lecture 1 Draft Slides"
                url: "/assets/..."

            (B) New grouped format:
              - lecture: 1
                title: "Slides"
                pre_url: "/assets/..."
                post_url: "/assets/..."
            {%- endcomment -%}

            {%- if l.lecture -%}
              <li>
                Lecture {{ l.lecture }} {{ l.title }}
                {%- if l.pre_url and l.pre_url != "" -%}
                  [<a href="{{ l.pre_url | relative_url }}">Pre-class</a>]
                {%- endif -%}
                {%- if l.post_url and l.post_url != "" -%}
                  [<a href="{{ l.post_url | relative_url }}">Post-class</a>]
                {%- endif -%}
              </li>

            {%- else -%}
              {%- if l.url and l.url != "" -%}
                {%- if l.url contains "://" -%}
                  <li><a href="{{ l.url }}">{{ l.label }}</a></li>
                {%- else -%}
                  <li><a href="{{ l.url | relative_url }}">{{ l.label }}</a></li>
                {%- endif -%}
              {%- else -%}
                <li>{{ l.label }}</li>
              {%- endif -%}
            {%- endif -%}

          {%- endfor -%}

          {% if row.additional %}

            {% assign add_items = row.additional %}
            {% assign add_heading = nil %}
          
            {%- if row.additional.items -%}
              {% assign add_items = row.additional.items %}
              {% assign add_heading = row.additional.heading %}
            {%- endif -%}
          
            {% if add_items and add_items.size > 0 %}
              <li>
                {% if add_heading and add_heading.url and add_heading.url != "" %}
                  {% if add_heading.url contains "://" %}
                    <a href="{{ add_heading.url }}">{{ add_heading.label }}</a>
                  {% else %}
                    <a href="{{ add_heading.url | relative_url }}">{{ add_heading.label }}</a>
                  {% endif %}
                {% else %}
                  <span>Additional Materials:</span>
                {% endif %}
          
                <ul>
                  {% for a in add_items %}
                    {% if a.url and a.url != "" %}
                      {% if a.url contains "://" %}
                        <li><a href="{{ a.url }}">{{ a.label }}</a></li>
                      {% else %}
                        <li><a href="{{ a.url | relative_url }}">{{ a.label }}</a></li>
                      {% endif %}
                    {% else %}
                      <li>{{ a.label }}</li>
                    {% endif %}
                  {% endfor %}
                </ul>
              </li>
            {% endif %}
          
          {% endif %}
        </ol>
      </td>
    </tr>
  {% endfor %}
  </tbody>
</table>
