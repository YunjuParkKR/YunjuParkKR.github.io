---
layout: single
title: "📝 블로그 📝 깃허브 블로그 - 내 블로그를 구글 검색결과에 노출시키기 "
categories: blog
tag: [블로그, 코딩, 깃허브, 깃허브블로그, 구글, 구글검색, 구글검색노출, googlesearch]
toc: true
toc_sticky: true
toc_label: 목차
published: true
---

**[blog]** 깃허브 블로그 구글 검색 노출 방법

내 깃허브 블로그가 구글 검색 시 결과화면에 뜨도록 구글 검색 노출 기능을 추가해보자.


## 구글 검색결과 노출 방법

### 1. _config.yml 파일 url 설정

_config.yml 에 url : https://[github id].github.io/ 가 적혀있어야 한다.

만약 적어주지 않았다면 아래와 같이 적어주기.

![image](https://user-images.githubusercontent.com/112684409/223648468-8ceb795b-3c4a-4249-b543-b8cc32d34d12.png)



## 2. sitemap.xml 

깃허브 블로그 최상위 폴더에 sitemap.xml 파일을 만든 뒤

아래 코드를 복사하여 붙여넣는다.

---
---
layout : null
---
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  {% for post in site.posts %}
    {% unless post.published == false %}
    <url>
      <loc>{{ site.url }}{{ post.url }}.html</loc>
      {% if post.sitemap.lastmod %}
        <lastmod>{{ post.sitemap.lastmod | date: "%Y-%m-%d" }}</lastmod>
      {% elsif post.date %}
        <lastmod>{{ post.date | date_to_xmlschema }}</lastmod>
      {% else %}
        <lastmod>{{ site.time | date_to_xmlschema }}</lastmod>
      {% endif %}
      {% if post.sitemap.changefreq %}
        <changefreq>{{ post.sitemap.changefreq }}</changefreq>
      {% else %}
        <changefreq>monthly</changefreq>
      {% endif %}
      {% if post.sitemap.priority %}
        <priority>{{ post.sitemap.priority }}</priority>
      {% else %}
        <priority>0.5</priority>
      {% endif %}
    </url>
    {% endunless %}
  {% endfor %}
  {% for page in site.pages %}
    {% unless page.sitemap.exclude == "yes" %}
    <url>
      <loc>{{ site.url }}{{ page.url | remove: "index.html" }}</loc>
      {% if page.sitemap.lastmod %}
        <lastmod>{{ page.sitemap.lastmod | date: "%Y-%m-%d" }}</lastmod>
      {% elsif page.date %}
        <lastmod>{{ page.date | date_to_xmlschema }}</lastmod>
      {% else %}
        <lastmod>{{ site.time | date_to_xmlschema }}</lastmod>
      {% endif %}
      {% if page.sitemap.changefreq %}
        <changefreq>{{ page.sitemap.changefreq }}</changefreq>
      {% else %}
        <changefreq>monthly</changefreq>
      {% endif %}
      {% if page.sitemap.priority %}
        <priority>{{ page.sitemap.priority }}</priority>
      {% else %}
        <priority>0.3</priority>
      {% endif %}
    </url>
    {% endunless %}
  {% endfor %}
</urlset>
---

![image](https://user-images.githubusercontent.com/112684409/223649648-25430b43-4cbd-41fd-9d79-0cd774e5aba7.png)



## 3. robots.txt 파일 작성

깃허브 블로그 최상위 폴더에 robots.txt 파일을 만든 뒤

아래 코드를 복사하여 붙여넣는다.


---
User-agent: *
Allow: /

Disallow: /private/
Sitemap: http://[github id].github.io/sitemap.xml
---

![image](https://user-images.githubusercontent.com/112684409/223649522-201c800c-2f7b-4673-95a7-3d46c1fea346.png)



## 4. Google Search Engine 사이트에 sitemap.xml 제출

Google Search Engine 사이트에 sitemap.xml 제출하고 테스트 결과를 확인한다.





-----------------------------------------------


## 



-----------------------------------------------

🙂 내용 중 잘못된 부분이 있을 경우 알려주시면 감사 드리겠습니다. 


