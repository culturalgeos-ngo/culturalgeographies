---
layout: default
title: Публікації
lang: uk
permalink: /publikatsii/
---

<div class="page-header">
  <div class="container">
    <p class="page-header__section">Публікації</p>
    <h1>Публікації</h1>
  </div>
</div>

<div class="page-content">
  <div class="container">

    <div class="publications">
      <div class="pub-type-tabs">
        <button class="pub-tab active" data-tab="notes">Методологічні нотатки</button>
        <button class="pub-tab" data-tab="photos">Фотозвіти</button>
      </div>

      <!-- Methodology notes -->
      <div id="tab-notes" class="tab-content">
        <div class="notes-list">
          {% assign notes = site.posts | where: 'category', 'note' | sort: 'date' | reverse %}
          {% for note in notes %}
          <div class="note-card">
            <p class="note-card__date">{{ note.date | date: '%d.%m.%Y' }}</p>
            <h3 class="note-card__title"><a href="{{ note.url | relative_url }}">{{ note.title }}</a></h3>
            <p class="note-card__excerpt">{{ note.excerpt | strip_html | truncate: 200 }}</p>
          </div>
          {% endfor %}
          {% if notes.size == 0 %}
          <div class="note-card">
            <p class="note-card__excerpt">Нотатки з'являться тут зовсім скоро.</p>
          </div>
          {% endif %}
        </div>
      </div>

      <!-- Photo reports -->
      <div id="tab-photos" class="tab-content" style="display:none">
        <div class="photoreports-grid">
          {% assign reports = site.posts | where: 'category', 'photoreport' | sort: 'date' | reverse %}
          {% for report in reports %}
          <div class="photoreport-card">
            {% if report.image %}
            <a href="{{ report.url | relative_url }}">
              <img src="{{ report.image | relative_url }}" alt="{{ report.title }}" class="photoreport-card__image">
            </a>
            {% endif %}
            <p class="photoreport-card__date">{{ report.date | date: '%d.%m.%Y' }}</p>
            <h3 class="photoreport-card__title"><a href="{{ report.url | relative_url }}">{{ report.title }}</a></h3>
            <p class="photoreport-card__text">{{ report.excerpt | strip_html | truncate: 150 }}</p>
          </div>
          {% endfor %}
          {% if reports.size == 0 %}
          <p class="note-card__excerpt">Фотозвіти з'являться тут зовсім скоро.</p>
          {% endif %}
        </div>
      </div>
    </div>

  </div>
</div>

<script>
document.querySelectorAll('.pub-tab').forEach(tab => {
  tab.addEventListener('click', () => {
    document.querySelectorAll('.pub-tab').forEach(t => t.classList.remove('active'));
    document.querySelectorAll('.tab-content').forEach(c => c.style.display = 'none');
    tab.classList.add('active');
    document.getElementById('tab-' + tab.dataset.tab).style.display = '';
  });
});
</script>