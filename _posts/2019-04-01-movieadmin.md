---
layout: post
title: "영화 어드민 사이트 개편"
date: 2019-04-01
excerpt: "FLASH로 개발된 구어드민 사이트 고도화"
Portfolio: true
comments: true
---


### 프로젝트 소개

웹브라우저의 FLASH 기능 지원종료로 인하여 신규 관리자 사이트로 이전하며 대용량 통계 데이터를 다운받고 라이브러리의 속도개선과 경량화에 초점을 맞추어 개발한 개편 프로젝트

<table class="type09">
  <thead>
  <tr>
    <th scope="cols">기간</th>
    <th scope="cols">담당부분</th>
    <th scope="cols">개발환경</th>
  </tr>
  </thead>
  <tbody>
  <tr>
    <td>2019.04 ~ 2020.03</td>
    <td>백앤드 및 프론트 개발</td>
    <td>IIS,Window,.NET,C#,MS-SQL,프로시저,JQUERY,Git</td>
  </tr>
  </tbody>
</table>


<a href="{{ site.url }}/FILE/YES24 영화 개편_관리자_V.1.1.pptx" target="_blank"><button type="button" class="btn btn-outline-secondary btn-sm"></button></a>

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



[사이트 이미지]

<img src="{{ site.url }}/IMG/PortFolio/YES24/movieadmin.png">
<img src="{{ site.url }}/IMG/PortFolio/YES24/movieadmin2.png">
<img src="{{ site.url }}/IMG/PortFolio/YES24/movieadmin3.png">
<img src="{{ site.url }}/IMG/PortFolio/YES24/movieadmin5.png">


<style>
table.type09 {
  border-collapse: collapse;
  text-align: left;
  line-height: 1.5;

}
table.type09 thead th {
  padding: 10px;
  font-weight: bold;
  vertical-align: top;
  color: #6a6e73;
  border-bottom: 3px solid #7f8183;
}
table.type09 tbody th {
  width: 150px;
  padding: 10px;
  font-weight: bold;
  vertical-align: top;
  border-bottom: 1px solid #ccc;
  background: #f3f6f7;
}
table.type09 td {
  width: 350px;
  padding: 10px;
  vertical-align: top;
  border-bottom: 1px solid #ccc;
}
</style>
