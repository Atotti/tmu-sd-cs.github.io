---
layout: default
title: "Faculty"
copyright_year: 2020
lang: "en"
ref: "staff"
---

<h1 class="nav2">Faculty</h1>
<section>
  <ul class="staff">
    {% for member in site.data.staff %}
      <li>
        <a href="/en/staff/{{ member.id }}.html">
          <b>{{ member.name }}</b> {{ member.title }}<br>
          <figure><img src="/image/{{ member.image }}" alt="{{ member.name }}"></figure>
          {{ member.specialties | join: "/" }}
        </a>
      </li>
    {% endfor %}
  </ul>
</section>
