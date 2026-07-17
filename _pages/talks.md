---
layout: page
permalink: /talks/
title: Talks
description: Invited seminars, conference talks, posters, and proceedings.
nav: true
nav_order: 2
---

<style>
  .talk-row {
    display: flex;
    align-items: flex-start;
    gap: 1rem;
    padding: 0.6rem 0;
    border-bottom: 1px solid var(--global-divider-color);
  }
  .talk-row:last-child {
    border-bottom: none;
  }
  .talk-date {
    flex: 0 0 4.5rem;
    text-align: right;
    color: var(--global-text-color-light);
    font-weight: 600;
    padding-top: 0.15rem;
  }
  .talk-badge {
    flex: 0 0 auto;
    align-self: flex-start;
    margin-top: 0.1rem;
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
  }
</style>

## Conferences

<div class="talks-list">
  {% for entry in site.data.talks.conferences %}
    <div class="talk-row">
      <div class="talk-date">{{ entry.date }}</div>
      <div class="talk-badge talk-badge-{{ entry.type | downcase }}">{{ entry.type }}</div>
      <div class="talk-body">
        <div class="talk-conference">
          {% if entry.link %}
            <a href="{{ entry.link }}" target="_blank" rel="noopener">{{ entry.conference }}</a>
          {% else %}
            {{ entry.conference }}
          {% endif %}
        </div>
        {% if entry.title and entry.title != "" %}
          <div class="talk-title">{{ entry.title }}</div>
        {% endif %}
        {% if (entry.location and entry.location != "") or entry.note %}
          <div class="talk-meta">
            {{ entry.location }}
            {% if entry.location != "" and entry.note %} — {% endif %}
            {{ entry.note }}
          </div>
        {% endif %}
      </div>
    </div>
  {% endfor %}
</div>

## Seminars

<div class="talks-list">
  {% for entry in site.data.talks.seminars %}
    <div class="talk-row">
      <div class="talk-date">{{ entry.date }}</div>
      <div class="talk-body">
        <div class="talk-conference">{{ entry.conference }}</div>
        {% if entry.title and entry.title != "" %}
          <div class="talk-title">{{ entry.title }}</div>
        {% endif %}
        {% if entry.location and entry.location != "" %}
          <div class="talk-meta">{{ entry.location }}</div>
        {% endif %}
      </div>
    </div>
  {% endfor %}
</div>

## Proceedings

<div class="publications">
{% bibliography -f proceedings.bib %}
</div>
