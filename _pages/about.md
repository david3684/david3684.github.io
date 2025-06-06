---
permalink: /
title: "Chanhyuk Lee"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

I am Chanhyuk *David* Lee, a Master's student at KAIST School of Computing. I'm currently working in [VL Lab](http://vllab.kaist.ac.kr), which is led by Prof. [Seunghoon Hong](https://maga33.github.io/). Before joining the lab, I received my Bachelor's degree from KAIST in a double major of Computer Science and Chemistry.

I'm widely interested in how complex model can interact with the real world. I'm currently working on model fusion via aligning parameters and representation. Ultimate goal of the work is building large models in bottom-up way with limited resources. Tasks for this goal includes works such as model fusion, knowledge transfer and multi-task learning.



## Education

<style>
.page__content > p {
  font-size: 0.95em;
  line-height: 1.6;
}

.page__content > p a {
  color: var(--global-link-color);
  text-decoration: none;
}

.page__content > p a:hover {
  color: var(--global-link-color-hover);
  text-decoration: underline;
}
.education-section {
  margin: 30px 0;
}

.education-item {
  margin-bottom: 25px;
  border-radius: 0 5px 5px 0;
}

.education-institution {
  font-size: 1.0em;
  font-weight: 550;
  margin-bottom: 8px;
}

.education-degree {
  font-size: 0.9em;
  font-weight: 500;
  margin-bottom: 5px;
  color: var(--global-text-color);
}

.education-period {
  color: var(--global-text-color-light);
  font-style: italic;
  margin-left: 10px;
}

.education-advisor {
  font-size: 0.8em;
  margin-top: 5px;
}

.education-advisor a {
  color: var(--global-link-color);
  text-decoration: none;
}

.education-advisor a:hover {
  color: var(--global-link-color-hover);
  text-decoration: underline;
}

.publication-list {
  list-style: none;
  padding: 0;
  margin: 20px 0;
}

.publication-item {
  display: flex;
  margin-bottom: 30px;
  border-bottom: 1px solid var(--global-border-color);
  padding-bottom: 20px;
  align-items: flex-start;
}

.publication-item:last-child {
  border-bottom: none;
}

.pub-thumbnail {
  flex-shrink: 0;
  width: 200px;
  margin-right: 15px;
  border-radius: 4px;
}

.pub-thumbnail img {
  width: 100%;
  object-fit: contain;
  border-radius: 4px;
}

.pub-content {
  flex: 1;
}

.pub-title {
  font-size: 0.95em;
  font-weight: 550;
  margin-bottom: 5px;
  line-height: 1.3;
  color: var(--global-text-color);
}

.pub-authors {
  margin-bottom: 5px;
  font-size: 0.8em;
  color: var(--global-text-color);
}

.pub-venue {
  margin-bottom: 4px;
  font-style: italic;
  color: var(--global-text-color-light);
  font-size: 0.8em;
}

.pub-links {
  margin-bottom: 4px;
}

.pub-links a {
  color: var(--global-link-color);
  text-decoration: none;
  margin-right: 10px;
  font-size: 0.8em;
}

.pub-links a:hover {
  text-decoration: underline;
  color: var(--global-link-color-hover);
}

.pub-description {
  font-size: 0.95em;
  line-height: 1.4;
  color: var(--global-text-color);
}

.author-highlight {
  font-weight: bold;
  text-decoration: underline;
}
</style>

<div class="education-section">
  <div class="education-item">
    <div class="education-institution">KAIST</div>
    <div class="education-degree">
      M.S. in Computer Science 
      <span class="education-period">(2025.03 -)</span>
    </div>
    <div class="education-advisor">Advisor: Prof. <a href="https://maga33.github.io/">Seunghoon Hong</a></div>
  </div>
  
  <div class="education-item">
    <div class="education-institution">KAIST</div>
    <div class="education-degree">
      B.S. in Computer Science & Chemistry <em>(Double Major)</em>
      <span class="education-period">(2019.03 - 2025.02)</span>
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

