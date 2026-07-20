---
layout: page
permalink: /talks/
title: Talks and Posters
description: Invited seminars, conference talks, posters, and proceedings.
nav: true
nav_order: 2
---

<style>
  .talks-list {
    margin-top: 1rem;
  }
  .talk-row {
    display: flex;
    align-items: flex-start;
    gap: 0.75rem;
    padding: 0.6rem 0;
    border-bottom: 1px solid var(--global-divider-color);
  }
  .talk-row:last-child {
    border-bottom: none;
  }
  .talk-badge {
    flex: 0 0 auto;
    align-self: flex-start;
    margin-top: 0.15rem;
    padding: 0.15rem 0.6rem;
    border-radius: 1rem;
    font-size: 0.8rem;
    font-weight: 600;
    color: #ffffff;
    white-space: nowrap;
  }
  .talk-badge-talk {
    background-color: var(--global-theme-color);
  }
  .talk-badge-poster {
    background-color: #8e44ad;
  }
  .talk-body {
    flex: 1 1 auto;
  }
  .talk-conference {
    font-weight: 600;
  }
  .talk-title {
    font-style: italic;
    color: var(--global-text-color-light);
  }
  .talk-meta {
    font-size: 0.9rem;
    color: var(--global-text-color-light);
    margin-top: 0.15rem;
  }
</style>

## Conferences

<div class="publications">
  {% assign conference_groups = site.data.talks.conferences | group_by: "year" | sort: "name" | reverse %}
  {% for group in conference_groups %}
    <h2 class="bibliography">{% if group.name and group.name != "" %}{{ group.name }}{% else %}Undated{% endif %}</h2>
    <div class="talks-list">
      {% for entry in group.items %}
        <div class="talk-row">
          <div class="talk-badge talk-badge-{{ entry.type | downcase }}">{{ entry.type }}</div>
          <div class="talk-body">
            <div class="talk-conference">{{ entry.conference }}</div>
            {% if entry.title and entry.title != "" %}
              <div class="talk-title">
                {% if entry.link and entry.link != "" %}
                  <a href="{{ entry.link }}" target="_blank" rel="noopener">{{ entry.title }}</a>
                {% else %}
                  {{ entry.title }}
                {% endif %}
              </div>
            {% endif %}
            {% assign has_location = false %}
            {% if entry.location and entry.location != "" %}{% assign has_location = true %}{% endif %}
            {% assign has_date = false %}
            {% if entry.date and entry.date != "" %}{% assign has_date = true %}{% endif %}
            {% assign has_note = false %}
            {% if entry.note and entry.note != "" %}{% assign has_note = true %}{% endif %}
            {% if has_location or has_date or has_note %}
              <div class="talk-meta">
                {% if has_date %}{{ entry.date | date: "%B %-d" }}{% endif %}
                {% if has_date and has_location %} · {% endif %}
                {{ entry.location }}
                {% if has_note %} — {{ entry.note }}{% endif %}
              </div>
            {% endif %}
          </div>
        </div>
      {% endfor %}
    </div>
  {% endfor %}
</div>

## Seminars

<div class="publications">
  {% assign seminar_groups = site.data.talks.seminars | group_by: "year" | sort: "name" | reverse %}
  {% for group in seminar_groups %}
    <h2 class="bibliography">{% if group.name and group.name != "" %}{{ group.name }}{% else %}Undated{% endif %}</h2>
    <div class="talks-list">
      {% for entry in group.items %}
        <div class="talk-row">
          <div class="talk-body">
            <div class="talk-conference">{{ entry.conference }}</div>
            {% if entry.title and entry.title != "" %}
              <div class="talk-title">
                {% if entry.link and entry.link != "" %}
                  <a href="{{ entry.link }}" target="_blank" rel="noopener">{{ entry.title }}</a>
                {% else %}
                  {{ entry.title }}
                {% endif %}
              </div>
            {% endif %}
            {% assign has_location = false %}
            {% if entry.location and entry.location != "" %}{% assign has_location = true %}{% endif %}
            {% assign has_date = false %}
            {% if entry.date and entry.date != "" %}{% assign has_date = true %}{% endif %}
            {% assign has_note = false %}
            {% if entry.note and entry.note != "" %}{% assign has_note = true %}{% endif %}
            {% if has_location or has_date or has_note %}
              <div class="talk-meta">
                {% if has_date %}{{ entry.date | date: "%B %-d" }}{% endif %}
                {% if has_date and has_location %} · {% endif %}
                {{ entry.location }}
                {% if has_note %} — {{ entry.note }}{% endif %}
              </div>
            {% endif %}
          </div>
        </div>
      {% endfor %}
    </div>
  {% endfor %}
</div>

## Proceedings

<div class="publications">
{% bibliography -f proceedings.bib %}
</div>
