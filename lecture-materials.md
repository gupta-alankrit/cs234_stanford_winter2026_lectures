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

          {% if row.additional and row.additional.size > 0 %}
            <li>
              <span>Additional Materials:</span>
              <ul>
                {% for a in row.additional %}
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
        </ol>
      </td>
    </tr>
  {% endfor %}
  </tbody>
</table>
