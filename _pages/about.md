---
permalink: /
title: "Chanhyuk Lee"
redirect_from: 
  - /about/
  - /about.html
---

<p class="hero__email"><a href="mailto:{{ site.author.email }}">{{ site.author.email }}</a></p>

<div class="hero">
<div class="hero__text" markdown="1">

I am Chanhyuk (David) Lee, an M.S. student at KAIST School of Computing, supervised by Prof. [Seunghoon Hong](https://maga33.github.io/). Before my graduate studies, I received my Bachelor's degree from KAIST with a double major in Computer Science and Chemistry.

I am broadly interested in generative modeling, including diffusion and flow-based models. I currently work on the foundations of **continuous diffusion language models**, with an emphasis on efficient language generation and reasoning in continuous latent spaces. In particular, I have been developing flow and flow map language models. I am also interested in exploring neural network parameter spaces, particularly for model merging to build generalist models and for weight-space memories in LLMs.

<p class="intro-note"><strong>Note:</strong> I'm applying to PhD programs for Fall 2027.</p>

</div>
<div class="hero__side">
  <img class="hero__photo" src="/images/profile.jpg" alt="Chanhyuk Lee">
  <ul class="hero__links">
    <li class="hero__links-email"><a href="mailto:{{ site.author.email }}" title="Email" aria-label="Email"><i class="fas fa-fw fa-envelope" aria-hidden="true"></i></a></li>
    <li><a href="{{ site.author.googlescholar }}" title="Google Scholar" aria-label="Google Scholar"><i class="ai ai-google-scholar ai-fw" aria-hidden="true"></i></a></li>
    <li><a href="https://github.com/{{ site.author.github }}" title="GitHub" aria-label="GitHub"><i class="fab fa-fw fa-github" aria-hidden="true"></i></a></li>
    <li><a href="https://x.com/{{ site.author.twitter }}" title="X (Twitter)" aria-label="X (Twitter)"><i class="fab fa-fw fa-x-twitter" aria-hidden="true"></i></a></li>
    <li><a href="https://www.linkedin.com/in/{{ site.author.linkedin }}" title="LinkedIn" aria-label="LinkedIn"><i class="fab fa-fw fa-linkedin" aria-hidden="true"></i></a></li>
  </ul>
</div>
</div>

## News

<div class="news-section">
  <div class="news-list">
    {% assign sorted_news = site.news | sort: 'date' | reverse %}
    {% for news in sorted_news limit:5 %}
    <div class="news-item">
      <div class="news-date">
        {{ news.date | date: "%Y.%m" }}
      </div>
      <div class="news-content">
        <div class="news-text">{{ news.content | truncatewords: 20 }}</div>
      </div>
    </div>
    {% endfor %}
  </div>
</div>

{% assign all_publications = site.publications | sort: 'date' | reverse %}
{% assign selected_publications = all_publications | where: "selected", true %}

<h2 class="section-with-link">Selected Publications <a class="section-link" href="/publications/">All publications &rarr;</a></h2>

<div class="publication-list">
  {% for pub in selected_publications %}
    {% include pub-item.html pub=pub %}
  {% endfor %}
</div>

<p class="more-link"><a href="/publications/">See all publications &rarr;</a></p>

{% include pub-scripts.html %}

## Education


<div class="education-section">
  <div class="education-item">
    <div class="education-period">2025 &ndash;</div>
    <div>
      <div class="education-degree">M.S. in Computer Science</div>
      <div class="education-detail">Korea Advanced Institute of Science and Technology (KAIST)</div>
      <div class="education-detail">Advisor: Prof. <a href="https://maga33.github.io/">Seunghoon Hong</a></div>
    </div>
  </div>

  <div class="education-item">
    <div class="education-period">2019 &ndash; 2025</div>
    <div>
      <div class="education-degree">B.S. in Computer Science and Chemistry <em>(Double Major)</em></div>
      <div class="education-detail">Korea Advanced Institute of Science and Technology (KAIST)</div>
    </div>
  </div>

  <div class="education-item">
    <div class="education-period">2016 &ndash; 2019</div>
    <div>
      <div class="education-degree">High School Diploma</div>
      <div class="education-detail">Gyeonggi Science High School for Gifted</div>
    </div>
  </div>
</div>
