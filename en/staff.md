---
layout: default
title: "Faculty"
copyright_year: 2020
lang: "en"
ref: "staff"
permalink: /en/staff.html
---

<h1 class="nav2">Faculty</h1>
<section>
  <ul class="staff">
    {% for member in site.data.staff.en %}
      <li>
        <a href="{{ site.baseurl }}/en/staff/{{ member.id }}.html">
          {{ member.title }} <b>{{ member.name }}</b><br>
          <figure><img src="{{ site.baseurl }}/image/{{ member.image }}" alt="{{ member.name }}"></figure>
          {{ member.specialties | join: "/" }}
        </a>
      </li>
    {% endfor %}
  </ul>
</section>
