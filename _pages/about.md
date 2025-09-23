---
permalink: /
title: "Chanhyuk Lee"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

I am Chanhyuk (David) Lee, M.S student at KAIST School of Computing. I'm currently working in [VL Lab](http://vllab.kaist.ac.kr), which is led by Prof. [Seunghoon Hong](https://maga33.github.io/). Before joining the lab, I received my Bachelor's degree from KAIST in a double major of Computer Science and Chemistry. I'm interested in neural network scaling, particularly developing efficient approaches to build large models with limited resources. My current work focuses on model fusion and parameter alignment, exploring how different networks can be combined while preserving their capabilities.
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

<p class="equal-contribution-note">* denotes equal contributions</p>

<div class="publication-list">
  {% assign conferences = site.publications | sort: 'date' %}
  {% assign journals = site.publications | sort: 'date' %}
  {% assign preprints = site.preprints | sort: 'date' %}
  
  {% comment %} Preprints를 맨 위에, 그 다음 Publications 순으로 정렬 {% endcomment %}
  {% assign sorted_preprints = site.preprints | sort: 'date' | reverse %}
  {% assign sorted_publications = site.publications | sort: 'date' | reverse %}
  
  {% comment %} Preprints 먼저 표시 {% endcomment %}
  {% for pub in sorted_preprints %}
  <div class="publication-item">
    <div class="pub-content">
      <div class="pub-title">
        {% assign preprint_index = 0 %}
        {% for p in preprints %}
          {% assign preprint_index = preprint_index | plus: 1 %}
          {% if p.title == pub.title %}[P{{ preprint_index }}]{% break %}{% endif %}
        {% endfor %}
        {{ pub.title }}
      </div>
      
      {% if pub.authors %}
      <div class="pub-authors">{{ pub.authors }}</div>
      {% elsif pub.author %}
      <div class="pub-authors">{{ pub.author }}</div>
      {% endif %}
      
      {% if pub.venue or pub.date %}
      <div class="pub-venue">
        {% if pub.venue %}{{ pub.venue }}{% endif %}
      </div>
      {% endif %}
      
      {% if pub.arxiv or pub.code or pub.project or pub.paperurl or pub.bibtexurl %}
      <div class="pub-links">
        {% if pub.arxiv %}<a href="{{ pub.arxiv }}">arXiv</a>{% endif %}
        {% if pub.code %}<a href="{{ pub.code }}">Code</a>{% endif %}
        {% if pub.project %}<a href="{{ pub.project }}">Project</a>{% endif %}
        {% if pub.paperurl %}<a href="{{ pub.paperurl }}">Paper</a>{% endif %}
        {% if pub.bibtexurl %}<a href="{{ pub.bibtexurl }}">BibTeX</a>{% endif %}
      </div>
      {% endif %}
      
      {% if pub.content and pub.content != "" %}
      <div class="pub-description">{{ pub.content }}</div>
      {% endif %}
    </div>
  </div>
  {% endfor %}
  
  {% comment %} Publications 다음에 표시 {% endcomment %}
  {% for pub in sorted_publications %}
  <div class="publication-item">
    <div class="pub-content">
      <div class="pub-title">
        {% if pub.venue contains "Journal" or pub.venue contains "journal" or pub.venue contains "IEEE" or pub.venue contains "ACM" %}
          {% assign journal_index = 0 %}
          {% for j in journals %}
            {% assign journal_index = journal_index | plus: 1 %}
            {% if j.title == pub.title %}[J{{ journal_index }}]{% break %}{% endif %}
          {% endfor %}
        {% else %}
          {% assign conf_index = 0 %}
          {% for c in conferences %}
            {% assign conf_index = conf_index | plus: 1 %}
            {% if c.title == pub.title %}[C{{ conf_index }}]{% break %}{% endif %}
          {% endfor %}
        {% endif %}
        {{ pub.title }}
      </div>
      
      {% if pub.authors %}
      <div class="pub-authors">{{ pub.authors }}</div>
      {% elsif pub.author %}
      <div class="pub-authors">{{ pub.author }}</div>
      {% endif %}
      
      {% if pub.venue or pub.date %}
      <div class="pub-venue">
        {% if pub.venue %}{{ pub.venue }}{% endif %}{% assign show_year = true %}{% if pub.venue contains "under review" or pub.venue contains "Under Review" or pub.venue contains "Preprint"%}{% assign show_year = false %}{% endif %}{% if pub.venue and pub.date and show_year %}, {% endif %}{% if pub.date and show_year %}{{ pub.date | date: "%Y" }}{% endif %}
      </div>
      {% endif %}
      
      {% if pub.arxiv or pub.code or pub.project or pub.paperurl or pub.bibtexurl %}
      <div class="pub-links">
        {% if pub.arxiv %}<a href="{{ pub.arxiv }}">arXiv</a>{% endif %}
        {% if pub.code %}<a href="{{ pub.code }}">Code</a>{% endif %}
        {% if pub.project %}<a href="{{ pub.project }}">Project</a>{% endif %}
        {% if pub.paperurl %}<a href="{{ pub.paperurl }}">Paper</a>{% endif %}
        {% if pub.bibtexurl %}<a href="{{ pub.bibtexurl }}">BibTeX</a>{% endif %}
      </div>
      {% endif %}
      
      {% if pub.content and pub.content != "" %}
      <div class="pub-description">{{ pub.content }}</div>
      {% endif %}
    </div>
  </div>
  {% endfor %}
</div>

<script>
document.addEventListener('DOMContentLoaded', function() {
  // 저자 이름 자동 하이라이트
  const myNames = [
    'Chanhyuk Lee',
    'Chanhyuk David Lee', 
    'David Lee',
    'C. Lee',
    'C.H. Lee'
  ];
  
  const authorElements = document.querySelectorAll('.pub-authors');
  
  authorElements.forEach(function(authorElement) {
    let authorHtml = authorElement.innerHTML;
    
    // 1. 내 이름 하이라이트 (별표 포함)
    myNames.forEach(function(name) {
      // 기존 strong 태그 제거
      const strongRegex = new RegExp(`<strong>${name.replace(/[.*+?^${}()|[\]\\]/g, '\\$&')}(\\*)?</strong>`, 'gi');
      authorHtml = authorHtml.replace(strongRegex, function(match) {
        return match.includes('*') ? `${name}*` : name;
      });
      
      // 내 이름 하이라이트 (별표 포함)
      const nameRegex = new RegExp(`\\b${name.replace(/[.*+?^${}()|[\]\\]/g, '\\$&')}(\\*)?\\b`, 'gi');
      authorHtml = authorHtml.replace(nameRegex, function(match) {
        return `<span class="author-highlight">${match}</span>`;
      });
    });
    
    // 2. Equal contribution 표시된 다른 저자들을 링크 스타일로
    authorHtml = authorHtml.replace(/\b([A-Z][a-z]+(?:\s+[A-Z][a-z]+)*\*)\b/g, function(match) {
      // 이미 span으로 감싸져 있지 않은 경우만 처리
      if (!authorHtml.includes(`<span class="author-highlight">${match}</span>`)) {
        return `<span class="author-link">${match}</span>`;
      }
      return match;
    });
    
    authorElement.innerHTML = authorHtml;
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