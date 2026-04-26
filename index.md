---
layout: default
title: Головна
lang: uk
---

<section class="hero">
  <div class="container">
    <h1 class="hero__tagline">
      Досліджуємо культуру,<br>
      <em>простір і спільноти</em>
    </h1>
    <div class="hero__meta">
      <div class="hero__stat">
        <span class="hero__stat-number">2015</span>
        <span class="hero__stat-label">Рік заснування</span>
      </div>
      <div class="hero__stat">
        <span class="hero__stat-number">20+</span>
        <span class="hero__stat-label">Проєктів</span>
      </div>
      <div class="hero__stat">
        <span class="hero__stat-number">3</span>
        <span class="hero__stat-label">Міста</span>
      </div>
    </div>
  </div>
</section>

<section class="feed">
  <div class="container">
    <div class="feed__header">
      <span class="mono">Останнє</span>
      <a href="{{ '/proekty/' | relative_url }}" class="mono">Всі проєкти →</a>
    </div>
    <div class="feed__grid">

      {% assign recent_projects = site.projects | sort: 'date' | reverse | limit: 3 %}
      {% for project in recent_projects %}
      <div class="feed__item">
        <p class="feed__item-type">Проєкт</p>
        <h3 class="feed__item-title"><a href="{{ project.url | relative_url }}">{{ project.title }}</a></h3>
        <p class="feed__item-excerpt">{{ project.excerpt | strip_html | truncate: 120 }}</p>
      </div>
      {% endfor %}

      {% assign recent_posts = site.posts | limit: 3 %}
      {% for post in recent_posts %}
      <div class="feed__item {% if post.category == 'photoreport' %}feed__item--photo{% endif %}">
        {% if post.image and post.category == 'photoreport' %}
        <img src="{{ post.image | relative_url }}" alt="{{ post.title }}" class="feed__item-image">
        {% endif %}
        <p class="feed__item-type">{% if post.category == 'photoreport' %}Фотозвіт{% else %}Нотатка{% endif %}</p>
        <h3 class="feed__item-title"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
        <p class="feed__item-excerpt">{{ post.excerpt | strip_html | truncate: 120 }}</p>
      </div>
      {% endfor %}

    </div>
  </div>
</section>

<section class="partners-strip">
  <div class="container">
    <p class="partners-strip__label">Партнери та підтримка</p>
    <ul class="partners-strip__list">
      <li>British Council</li>
      <li>PinchukArtCentre</li>
      <li>Docudays UA</li>
      <li>Ukrainian Cultural Foundation</li>
      <li>Contemporary Art Center Zaporizhzhia</li>
      <li>Dniproprostor</li>
    </ul>
  </div>
</section>
