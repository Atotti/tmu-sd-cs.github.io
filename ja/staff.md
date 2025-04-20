---
layout: default
title: "教員紹介"
copyright_year: 2020
lang: "ja"
ref: "staff"
permalink: /ja/staff.html
---

<h1 class="nav2">教員紹介</h1>
<section>
  <ul class="staff">
    {% for member in site.data.staff.ja %}
      <li>
        <a href="{{ site.baseurl }}/staff/{{ member.id }}.html">
          <b>{{ member.name }}</b> {{ member.title }}<br>
          <figure><img src="{{ site.baseurl }}/image/{{ member.image }}" alt="{{ member.name }}"></figure>
          {{ member.specialties | join: "/" }}
        </a>
      </li>
    {% endfor %}
  </ul>
</section>
