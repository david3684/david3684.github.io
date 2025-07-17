---
permalink: /
title: "Chanhyuk Lee"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

I am Chanhyuk *David* Lee (이찬혁), a Master's student at KAIST School of Computing. I'm currently working in [VL Lab](http://vllab.kaist.ac.kr), which is led by Prof. [Seunghoon Hong](https://maga33.github.io/). Before joining the lab, I received my Bachelor's degree from KAIST in a double major of Computer Science and Chemistry.

I'm interested in neural network scaling, particularly developing efficient approaches to build large models with limited resources. My current work focuses on model fusion and parameter alignment, exploring how different networks can be combined while preserving their capabilities.
For these practical approaches, I am deeply interested in theoretical developments such as infinite-size network frameworks like Neural Tangent Kernel and loss landscape theories like mode connectivity.

## Education


<div class="education-section">
  <div class="education-item">
    <div class="education-institution">KAIST</div>
    <div class="education-degree">
      M.S. in Computer Science 
      <span class="education-period">(Mar. 2025 -)</span>
    </div>
    <div class="education-advisor">Advisor: Prof. <a href="https://maga33.github.io/">Seunghoon Hong</a></div>
  </div>
  
  <div class="education-item">
    <div class="education-institution">KAIST</div>
    <div class="education-degree">
      B.S. in Computer Science & Chemistry <em>(Double Major)</em>
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

## Publications

<div class="publication-list">
  {% assign sorted_publications = site.publications | sort: 'date' | reverse %}
  {% for pub in sorted_publications %}
  <div class="publication-item">
    {% if pub.image %}
    <div class="pub-thumbnail">
      <img src="{{ pub.image }}" alt="{{ pub.title }}" />
    </div>
    {% endif %}
    
    <div class="pub-content">
      <div class="pub-title">{{ pub.title }}</div>
      
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
  // 이미지 높이 조정
  const items = document.querySelectorAll('.publication-item');
  
  items.forEach(function(item) {
    const content = item.querySelector('.pub-content');
    const thumbnail = item.querySelector('.pub-thumbnail img');
    
    if (content && thumbnail) {
      const contentHeight = content.offsetHeight;
      thumbnail.style.height = contentHeight + 'px';
    }
  });
  
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
    
    myNames.forEach(function(name) {
      // 이미 <strong> 태그가 있는 경우 제거하고 새로운 스타일 적용
      const strongRegex = new RegExp(`<strong>${name}</strong>`, 'gi');
      const plainRegex = new RegExp(`\\b${name}\\b`, 'gi');
      
      // 기존 strong 태그 제거
      authorHtml = authorHtml.replace(strongRegex, name);
      
      // 새로운 하이라이트 클래스 적용
      authorHtml = authorHtml.replace(plainRegex, `<span class="author-highlight">${name}</span>`);
    });
    
    authorElement.innerHTML = authorHtml;
  });
});
</script>

