---
layout: page
title: "Football Schedule - Today's Matches & Fixtures"
description: "Complete football schedule with match times, TV channels, and streaming info"
breadcrumb:
  - name: Home
    url: /
  - name: Schedule
    url: /schedule
permalink: /schedule
---

## Today's Football Matches

{% include schedule-table.html %}

<!-- Dynamic content using Liquid -->
{% assign today = site.time | date: '%Y-%m-%d' %}
{% assign matches = site.data.matches | where: "date", today %}

{% if matches.size > 0 %}
<div class="matches-list">
    {% for match in matches %}
    <div class="match-item">
        <div class="match-time">{{ match.time }}</div>
        <div class="match-teams">
            <span class="home-team">{{ match.home }}</span> vs 
            <span class="away-team">{{ match.away }}</span>
        </div>
        <div class="match-league">{{ match.league }}</div>
        <div class="match-channel">{{ match.channel }}</div>
    </div>
    {% endfor %}
</div>
{% else %}
<p>No matches scheduled for today. Check back tomorrow!</p>
{% endif %}
