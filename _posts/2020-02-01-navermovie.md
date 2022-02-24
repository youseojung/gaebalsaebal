---
layout: post
title: "제휴사(네이버) 영화 서비스 개편"
date: 2020-02-01
excerpt: "극장 API 연동 및 제휴사(네이버) 영화 예매사이트 리뉴얼"
Portfolio: true
comments: true
---



### 프로젝트 소개

멀티플렉스 극장들의 예매 서비스 확대로 제휴사 페이지의 예매 프로세스 변경이 필요하여 네이버 영화 예매서비스를 중점적으로 진행

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
    <td>2019.09 ~ 2020.03</td>
    <td>백앤드 및 프론트 개발</td>
    <td>IIS,Window,웹폼프로젝트,ASP.NET,MS-SQL,프로시저,JQUERY</td>
  </tr>
  </tbody>
</table>


[AS-IS]
<ol>
  <li>공통 서비스를 제공하는 API나 모듈이 없어 극장사와 제휴사 사이의 변경 내역을 별도로 개발하여 불필요한 작업으로 생산성 저하</li>
  <li>영화 예매 서비스 로그 추가와 경로들의 일관성 획득 필요</li>
  <li>웹호출과 관련된 예매 오류 시 문제점 파악의 어려움</li>
  <li>예매내역 정산대사가 상이한 원인 파악의 어려움</li>
</ol>
[Request]
<ol>
  <li>좌석 차등 요금제 스케줄 </li>
  <li>좌석 차등 요금제 요금 예매 서비스</li>
  <li>특수관/특수상영 표기</li>
</ol>
[TO-BE]
<ol>
  <li>영화 서비스 개편으로 개발된 극장 API를 사용하여 개발 구조를 변경하여 제휴사 서비스 개발</li>
  <li>요청/응답 내역 기록으로 정산대사나 예매 오류건 확인 용이</li>
  <li>좌석 차등 요금제 적용 및 특수관/특수상영 정보 표기로 인한 예매 프로세스 변경</li>
</ol>

[사이트 이미지]

<img src="{{ site.url }}/IMG/PortFolio/YES24/메인화면.PNG">
<img src="{{ site.url }}/IMG/PortFolio/YES24/지역별극장.PNG">



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

