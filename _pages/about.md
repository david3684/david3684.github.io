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
// 페이지별 고유 처리를 위한 플래그
if (typeof window.authorProcessedAbout === 'undefined') {
  window.authorProcessedAbout = false;
}

function processAuthorsAbout() {
  if (window.authorProcessedAbout) return;
  
  console.log('Processing authors on about page');
  
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

  // 저자 이름과 홈페이지 링크 매칭 데이터베이스
  const authorLinks = {
    'Seunghoon Hong': 'https://maga33.github.io/',
    'Jinwoo Shin': 'https://alinlab.kaist.ac.kr/shin.html',
    'Sungroh Yoon': 'https://datalab.snu.ac.kr/~srh/',
    'Jaesik Park': 'https://jaesik.info/',
    'Bohyung Han': 'https://cv.snu.ac.kr/index.php/~bhhan/',
    'Joonseok Lee': 'https://www.joonseok.net/',
    'Gunhee Kim': 'https://vision.snu.ac.kr/gunhee/',
    'Kyomin Jung': 'http://milab.snu.ac.kr/kjung/',
    'Hyunwoo J. Kim': 'https://hyunwoojkim.github.io/',
    'Taesup Moon': 'https://mindlab-skku.github.io/',
    'Sanghyuk Chun': 'https://sanghyukchun.github.io/home/',
    'Dongyoon Han': 'https://sites.google.com/site/dyhan0920/',
    'Sangdoo Yun': 'https://sangdooyun.github.io/',
    'Junsuk Choe': 'https://sites.google.com/view/junsukchoe',
    'Hunjae Lee': 'https://scholar.google.com/citations?user=example',
    'Donggyun Kim': 'https://sites.google.com/view/donggyun-kim/home',
    'Donghoon Lee': 'https://movinghoon.github.io/',
    'Kiet T. Nguyen': 'https://sites.google.com/view/kietngt/home',
    'Jiho Choi': 'https://www.linkedin.com/in/jiho-choi-883197234',
    'Chanryeol Lee': 'https://github.com/cusasak'
  };
  
  // 내 이름 하이라이트용
  const myNames = [
    'Chanhyuk Lee',
    'Chanhyuk David Lee', 
    'David Lee',
    'C. Lee',
    'C.H. Lee'
  ];
  
  const authorElements = document.querySelectorAll('.pub-authors');
  console.log('Found author elements:', authorElements.length);
  
  authorElements.forEach(function(authorElement, index) {
    let authorHtml = authorElement.innerHTML;
    console.log(`Processing element ${index}:`, authorHtml);
    
    // 1. 내 이름 하이라이트 (별표 포함) - 먼저 처리
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
    
    // 2. 다른 저자들에게 링크 적용
    Object.keys(authorLinks).forEach(function(authorName) {
      const authorUrl = authorLinks[authorName];
      const regex = new RegExp(`\\b${authorName.replace(/[.*+?^${}()|[\]\\]/g, '\\$&')}(\\*)?\\b`, 'gi');
      
      // 이미 링크가 걸려있지 않고 하이라이트도 되어있지 않은 경우만 링크 추가
      if (!authorHtml.includes(`href="${authorUrl}"`) && !authorHtml.includes(`class="author-highlight">${authorName}`)) {
        authorHtml = authorHtml.replace(regex, function(match) {
          return `<a href="${authorUrl}" target="_blank" class="author-link">${match}</a>`;
        });
      }
    });
    
    // 3. Equal contribution 표시된 다른 저자들을 링크 스타일로
    authorHtml = authorHtml.replace(/\b([A-Z][a-z]+(?:\s+[A-Z][a-z]+)*\*)\b/g, function(match) {
      // 이미 처리된 경우 제외
      if (authorHtml.includes(`<span class="author-highlight">${match}</span>`) || 
          authorHtml.includes(`<a href=`) && authorHtml.includes(match)) {
        return match;
      }
      return `<span class="author-link">${match}</span>`;
    });
    
    console.log(`After processing element ${index}:`, authorHtml);
    authorElement.innerHTML = authorHtml;
  });
  
  window.authorProcessedAbout = true;
}

// 여러 이벤트에서 실행하여 안정성 확보
document.addEventListener('DOMContentLoaded', processAuthorsAbout);
window.addEventListener('load', processAuthorsAbout);

// 페이지가 완전히 로드된 후 한 번 더 실행 (GitHub Pages 환경을 위해)
setTimeout(processAuthorsAbout, 500);
setTimeout(processAuthorsAbout, 2000);
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