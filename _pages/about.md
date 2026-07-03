---
permalink: /
title: "Chanhyuk Lee"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

I am Chanhyuk (David) Lee, M.S student at KAIST School of Computing. I'm currently working in [VL Lab](http://vllab.kaist.ac.kr), which is led by Prof. [Seunghoon Hong](https://maga33.github.io/). Before joining the lab, I received my Bachelor's degree from KAIST in a double major of Computer Science and Chemistry. 

My research focuses on building fast and efficient generative models.
Broadly, my work spans model merging and few-shot learning for generative models.
Currently, I am working on non-autoregressive text generation through diffusion models,
enabling parallel decoding of language. In particular, I am interested in
continuous representations of text for diffusion language models,
which make various techniques from the image domain, such as flow map distillation, directly transferable. I also worked on model merging ans few-shot learning, including studies on the parameter space geometries of neural networks.
<!-- For these practical approaches, I am deeply interested in theoretical developments such as infinite-size network frameworks like Neural Tangent Kernel and loss landscape theories like mode connectivity. -->
{: .intro-section}

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





## Publications


<div class="publication-list">
  {% assign conferences = site.publications | sort: 'date' %}
  {% assign journals = site.publications | sort: 'date' %}
  {% assign preprints = site.preprints | sort: 'date' %}
  
  {% comment %} Publications 먼저, 그 다음 Preprints 순으로 정렬 {% endcomment %}
  {% assign sorted_preprints = site.preprints | sort: 'date' | reverse %}
  {% assign sorted_publications = site.publications | sort: 'date' | reverse %}
  
  {% comment %} Publications 먼저 표시 {% endcomment %}
  {% for pub in sorted_publications %}
  <div class="publication-item" {% if pub.arxiv_id %}data-arxiv-id="{{ pub.arxiv_id }}"{% endif %}>
    <div class="pub-content">
      <div class="pub-title">{{ pub.title }}</div>

      {% if pub.authors %}
      <div class="pub-authors">{{ pub.authors | replace: '†', '<sup>†</sup>' | replace: '*', '<sup>*</sup>' }}</div>
      {% elsif pub.author %}
      <div class="pub-authors">{{ pub.author | replace: '†', '<sup>†</sup>' | replace: '*', '<sup>*</sup>' }}</div>
      {% endif %}

      {% if pub.note or pub.collaboration %}
      <div class="pub-note">{{ pub.note | default: pub.collaboration }}</div>
      {% endif %}

      {% if pub.venue or pub.venue_full or pub.venue_abbr or pub.date %}
      <div class="pub-venue">
        {% capture venue_text %}{% if pub.venue_full or pub.venue_abbr %}{% if pub.venue_full %}{{ pub.venue_full }}{% endif %}{% if pub.venue_abbr %} (<span class="pub-venue-abbr">{{ pub.venue_abbr }}</span>){% endif %}{% elsif pub.venue %}{{ pub.venue }}{% endif %}{% endcapture %}{{ venue_text | strip }}{% assign show_year = true %}{% if pub.venue contains "under review" or pub.venue contains "Under Review" or pub.venue contains "Preprint"%}{% assign show_year = false %}{% endif %}{% if pub.date and show_year %}, {{ pub.date | date: "%Y" }}{% endif %}
      </div>
      {% endif %}

      <div class="pub-links">
        {% if pub.arxiv %}<a href="{{ pub.arxiv }}">arXiv</a>{% endif %}
        {% if pub.code %}<a href="{{ pub.code }}">Code</a>{% endif %}
        {% if pub.project %}<a href="{{ pub.project }}">Project</a>{% endif %}
        {% if pub.paperurl %}<a href="{{ pub.paperurl }}">Paper</a>{% endif %}
        {% if pub.bibtexurl %}<a href="{{ pub.bibtexurl }}">BibTeX</a>{% endif %}
        {% if pub.abstract %}<button class="abstract-toggle" onclick="toggleAbstract(this)" aria-expanded="false">Abstract</button>{% endif %}
        {% if pub.arxiv_id %}
          {% assign cite_count = site.data.citations.citations[pub.arxiv_id] %}
          {% if cite_count %}
          <span class="citation-badge {% if cite_count == 0 %}cite-zero{% endif %}" title="{{ cite_count }} citations (Semantic Scholar)">
            <svg class="cite-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M2 3h6a4 4 0 0 1 4 4v14a3 3 0 0 0-3-3H2z"/><path d="M22 3h-6a4 4 0 0 0-4 4v14a3 3 0 0 1 3-3h7z"/></svg>
            <span class="cite-count">{{ cite_count }}</span>
          </span>
          {% endif %}
        {% endif %}
      </div>

      {% if pub.abstract %}
      <div class="pub-abstract" hidden><p>{{ pub.abstract }}</p></div>
      {% endif %}

      {% if pub.content and pub.content != "" %}
      <div class="pub-description">{{ pub.content }}</div>
      {% endif %}
    </div>
  </div>
  {% endfor %}

  {% comment %} Preprints 다음에 표시 {% endcomment %}
  {% for pub in sorted_preprints %}
  <div class="publication-item" {% if pub.arxiv_id %}data-arxiv-id="{{ pub.arxiv_id }}"{% endif %}>
    <div class="pub-content">
      <div class="pub-title">{{ pub.title }}</div>

      {% if pub.authors %}
      <div class="pub-authors">{{ pub.authors | replace: '†', '<sup>†</sup>' | replace: '*', '<sup>*</sup>' }}</div>
      {% elsif pub.author %}
      <div class="pub-authors">{{ pub.author | replace: '†', '<sup>†</sup>' | replace: '*', '<sup>*</sup>' }}</div>
      {% endif %}

      {% if pub.note or pub.collaboration %}
      <div class="pub-note">{{ pub.note | default: pub.collaboration }}</div>
      {% endif %}

      {% if pub.venue or pub.venue_full or pub.venue_abbr or pub.date %}
      <div class="pub-venue">
        {% capture venue_text %}{% if pub.venue_full or pub.venue_abbr %}{% if pub.venue_full %}{{ pub.venue_full }}{% endif %}{% if pub.venue_abbr %} (<span class="pub-venue-abbr">{{ pub.venue_abbr }}</span>){% endif %}{% elsif pub.venue %}{{ pub.venue }}{% endif %}{% endcapture %}{{ venue_text | strip }}
      </div>
      {% endif %}

      <div class="pub-links">
        {% if pub.arxiv %}<a href="{{ pub.arxiv }}">arXiv</a>{% endif %}
        {% if pub.code %}<a href="{{ pub.code }}">Code</a>{% endif %}
        {% if pub.project %}<a href="{{ pub.project }}">Project</a>{% endif %}
        {% if pub.paperurl %}<a href="{{ pub.paperurl }}">Paper</a>{% endif %}
        {% if pub.bibtexurl %}<a href="{{ pub.bibtexurl }}">BibTeX</a>{% endif %}
        {% if pub.abstract %}<button class="abstract-toggle" onclick="toggleAbstract(this)" aria-expanded="false">Abstract</button>{% endif %}
        {% if pub.arxiv_id %}
          {% assign cite_count = site.data.citations.citations[pub.arxiv_id] %}
          {% if cite_count %}
          <span class="citation-badge {% if cite_count == 0 %}cite-zero{% endif %}" title="{{ cite_count }} citations (Semantic Scholar)">
            <svg class="cite-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M2 3h6a4 4 0 0 1 4 4v14a3 3 0 0 0-3-3H2z"/><path d="M22 3h-6a4 4 0 0 0-4 4v14a3 3 0 0 1 3-3h7z"/></svg>
            <span class="cite-count">{{ cite_count }}</span>
          </span>
          {% endif %}
        {% endif %}
      </div>

      {% if pub.abstract %}
      <div class="pub-abstract" hidden><p>{{ pub.abstract }}</p></div>
      {% endif %}

      {% if pub.content and pub.content != "" %}
      <div class="pub-description">{{ pub.content }}</div>
      {% endif %}
    </div>
  </div>
  {% endfor %}
</div>

<script>
function toggleAbstract(btn) {
  var abstract = btn.closest('.pub-links').nextElementSibling;
  if (!abstract || !abstract.classList.contains('pub-abstract')) return;
  var expanded = btn.getAttribute('aria-expanded') === 'true';
  if (expanded) {
    abstract.hidden = true;
    btn.setAttribute('aria-expanded', 'false');
    btn.classList.remove('active');
  } else {
    abstract.hidden = false;
    btn.setAttribute('aria-expanded', 'true');
    btn.classList.add('active');
  }
}

document.addEventListener('DOMContentLoaded', function() {
  var myNames = ['Chanhyuk Lee', 'Chanhyuk David Lee', 'David Lee', 'C. Lee', 'C.H. Lee'];
  document.querySelectorAll('.pub-authors').forEach(function(el) {
    var html = el.innerHTML;
    myNames.forEach(function(name) {
      var re = new RegExp('\\b' + name.replace(/[.*+?^${}()|[\]\\]/g, '\\$&') + '(\\*)?\\b', 'gi');
      html = html.replace(re, function(m) { return '<span class="author-highlight">' + m + '</span>'; });
    });
    html = html.replace(/\b([A-Z][a-z]+(?:\s+[A-Z][a-z]+)*\*)\b/g, function(m) {
      if (!html.includes('<span class="author-highlight">' + m + '</span>')) {
        return '<span class="author-link">' + m + '</span>';
      }
      return m;
    });
    el.innerHTML = html;
  });
});
</script>

## Education


<div class="education-section">
  <div class="education-item">
    <div class="education-institution">M.S. in Computer Science </div>
    <div class="education-degree">
      Korea Advanced Institue of Science and Technology (KAIST)
      <span class="education-period">(Mar. 2025 -)</span>
    </div>
    <div class="education-advisor">Advisor: Prof. <a href="https://maga33.github.io/">Seunghoon Hong</a></div>
  </div>
  
  <div class="education-item">
    <div class="education-institution">B.S. in Computer Science and Chemistry <em>(Double Major)</em></div>
    <div class="education-degree">
      Korea Advanced Institue of Science and Technology (KAIST)
      <span class="education-period">(Mar. 2019 - Feb. 2025)</span>
    </div>
  </div>

  <div class="education-item">
    <div class="education-institution">Gyeonggi Science High School for Gifted</div>
    <div class="education-degree">
      <span class="education-period">(Mar. 2016 - Feb. 2019)</span>
    </div>
  </div>
</div>