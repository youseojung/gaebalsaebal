---
layout: post
title: "영화 어드민 사이트 개편"
date: 2019-04-01
excerpt: "영화 어드민 사이트 개편"
Portfolio: true
comments: true
---

    <style>
  /* 2way헤더와 라인포인트*/
  table {
      border-collapse: collapse;
      text-align: left;
      line-height: 1.5;
  }
  table thead th {
      text-align: center;
      padding: 10px;
      font-weight: bold;
      vertical-align: top;
      color: #4E2E5A;
      border-top: 2px solid #4E2E5A;
      border-bottom: 2px solid #4E2E5A;
  }
  table tbody th {
      padding: 10px 15px;
      font-weight: bold;
      vertical-align: top;
      border-bottom: 1px solid #ccc;
      background: #f3f6f7;
  }
  table td {
      padding: 10px 15px;
      vertical-align: top;
      border-bottom: 1px solid #ccc;
  }
</style>



### 프로젝트 소개

웹브라우저의 FLASH 기능 지원종료로 인하여 신규 관리자 사이트로 이전하며 대용량 통계 데이터를 다운받고 라이브러리의 속도개선과 경량화에 초점을 맞추어 개발한 개편 프로젝트

| 기간 | 담당부분 | 개발환경 |
|---|:---:|---:|
| `2019.04 ~ 2020.03` | 백앤드 및 프론트 개발 | `Window``.Net``C#``MS-SQL``프로시저``JQUERY``MVC``GIT``Jquery` |

[AS-IS]
<ol>
    <li>플래시로 개발 되어 있어 유지보수 어려움</li>
    <li>사용되지 않는 기능 혼재</li>
    <li>보안에 취약하며 웹 접근성이 떨어짐</li>
 
</ol>
[TO-BE]
<ol>
    <li>백엔드/프론트로 분리하고 MVC 디자인 패턴으로 리팩토링</li>
    <li>WebApi 명세화, 문서화 하기위하여 Swagger 세팅</li>
</ol>


{% capture images %}

!(https://raw.githubusercontent.com/youseojung/youseojung.github.io/master/IMG/PortFolio/YES24/sktmobilemoviecardlist.PNG.PNG "SKT T MEMBERSHIP VIP 모바일 메인 이미지")
!(https://raw.githubusercontent.com/youseojung/youseojung.github.io/master/IMG/PortFolio/YES24/sktwebmoviemain.PNG "SKT T MEMBERSHIP VIP PC 메인 이미지")


!(https://raw.githubusercontent.com/youseojung/youseojung.github.io/master/IMG/PortFolio/YES24/sktwebmoviecardlist.PNG  "SKT T MEMBERSHIP VIP PC이미지")
!(https://raw.githubusercontent.com/youseojung/youseojung.github.io/master/IMG/PortFolio/YES24/sktmobilemoviecardlist.PNG.PNG "SKT T MEMBERSHIP VIP 모바일 카드 이미지")


{% endcapture %}
{% include gallery images=images caption="Test images" cols=3 %}
