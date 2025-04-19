---
layout: default
title: "教員紹介"
copyright_year: 2020
---

<h1 class="nav2">教員紹介</h1>
<section>
  <ul class="staff">
    {% for member in site.data.staff.ja %}
      <li>
        <a href="/staff/{{ member.id }}.html">
          <b>{{ member.name }}</b> {{ member.title }}<br>
          <figure><img src="image/{{ member.image }}" alt="{{ member.name }}"></figure>
          {{ member.specialties | join: "/" }}
        </a>
      </li>
    {% endfor %}
  </ul>
</section>
