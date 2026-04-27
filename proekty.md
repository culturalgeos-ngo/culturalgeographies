---
layout: default
title: Проєкти
lang: uk
permalink: /proekty/
---

<div class="page-header">
  <div class="container">
    <p class="page-header__section">Проєкти</p>
    <h1>Проєкти</h1>
  </div>
</div>

<div class="page-content">
  <div class="container">

    <div class="projects-grid">
      <div class="filters">
        <button class="filter-btn active" data-filter="all">Всі</button>
        <button class="filter-btn" data-filter="ngo">Проєкти ГО</button>
        <button class="filter-btn" data-filter="supported">Підтримані нами</button>
        <button class="filter-btn" data-filter="education">Освіта</button>
        <button class="filter-btn" data-filter="art">Мистецтво</button>
        <button class="filter-btn" data-filter="books">Видання</button>
        <button class="filter-btn" data-filter="inclusion">Інклюзія</button>
        <button class="filter-btn" data-filter="research">Дослідження</button>
      </div>

      <div class="projects-list" id="projects-list">
        {% assign sorted_projects = site.projects | sort: 'date' | reverse %}
        {% for project in sorted_projects %}
        <div class="project-card" data-tags="{{ project.tags | join: ' ' }}">
          <div>
            <div class="project-card__meta">
              {% for tag in project.tags %}
              <span class="tag">{{ tag }}</span>
              {% endfor %}
            </div>
            <h3 class="project-card__title">
              <a href="{{ project.url | relative_url }}">{{ project.title }}</a>
            </h3>
            <p class="project-card__desc">{{ project.excerpt | strip_html | truncate: 160 }}</p>
          </div>
          <span class="project-card__year">{{ project.date | date: '%Y' }}</span>
        </div>
        {% endfor %}
      </div>
    </div>

  </div>
</div>

<script>
const filterBtns = document.querySelectorAll('.filter-btn');
const cards = document.querySelectorAll('.project-card');

filterBtns.forEach(btn => {
  btn.addEventListener('click', () => {
    filterBtns.forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    const filter = btn.dataset.filter;
    cards.forEach(card => {
      const tags = card.dataset.tags || '';
      card.style.display = (filter === 'all' || tags.includes(filter)) ? '' : 'none';
    });
  });
});
</script>
