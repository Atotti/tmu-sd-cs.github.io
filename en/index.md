---
layout: default
title: "Home"
copyright_year: 2020
lang: "en"
ref: "index"
permalink: /en/index.html
---

<section id="news">
  <h2>News &amp; Topics</h2>
  <ul>
    {% for news_item in site.en_news reversed %}
      <li>
        <span class="date">{{ news_item.date | date: "%Y.%-m.%-d" }}</span><br>
        {{ news_item.content }}
      </li>
    {% endfor %}
  </ul>
</section>
<!---
<section id="twitter">
  <a class="twitter-timeline" href="https://twitter.com/CsTmu?ref_src=twsrc%5Etfw">Tweets by CsTmu</a> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
</section>
--->
