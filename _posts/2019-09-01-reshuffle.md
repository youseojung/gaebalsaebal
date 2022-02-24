---
layout: post
title: "영화 서비스 개편 프로젝트"
date: 2019-09-01
excerpt: "극장 API 연동 및 자사 영화 예매사이트 리뉴얼"
Portfolio: true
comments: true
---



### 프로젝트 소개

멀티플렉스 극장들의 차세대 서비스 전환과 브라우저의 FLASH 서비스 지원 종료 이슈, 영화 서비스 확대 등의 이유로 진행한 개편 프로젝트


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
    <td>IIS,Window,,.NET,MS-SQL,프로시저,JQUERY</td>
  </tr>

  </tbody>
</table>



[TO-BE]
2.1	영화 서비스를 백엔드/프론트로 분리하고 MVC 디자인 패턴으로 리팩토링
2.2	영화 이벤트 유형 템플릿화 하여 관리자 사이트 기능으로 개발
2.3	플래시 소스 제거 후 배너/메인 화면 설정을 관리자 사이트 기능으로 개발
2.4	영화 예매 공통 서비스를 모듈화 하여 극장 API 개발
2.5	극장사에서 추가된 데이터들은 모델링 되어 코드별로 관리되어 별도로 등록절차 없이 적용가능
2.6	로그 내용 및 경로 개선
2.6.1	요청/응답 내역 기록
2.6.2	주문번호만으로 사용자의 서비스 이용경로 파악 가능


[AS-IS]
<ol>
  <li>웹폼 프로젝트로 개발(동일 메서드 중복)</li>
  <li>비슷한 유형의 영화 이벤트도 중복 개발</li>
  <li>플래시 형태로 배치 된 배너/메인 화면 디자인</li>
  <li>좌석도 노출 페이지, 홈페이지 배너 등 사이트의 일부가 FLASH로 개발</li>
  <li>공통 서비스를 제공하는 API나 모듈이 없어 극장사 별로 영화 서비스를 개발해야함</li>
  <li>다양한 극장 좌석도 형태를 구현하지 못함</li>
  <li>변경된 내용이 있는 경우 동일한 기능을 사용하는 곳을 전부 수정해야함</li>
  <li>Iframe 사용으로 보안에 취약 (XSS공격)</li>
  <li>다양해져가는 극장들의 특별관, 특별석에 대한 정보를 고려하여 DB가 설계되어 있지 않음</li>
  <li>영화 예매 서비스의 로그 경로들의 일관성 획득 필요</li>
</ol>

[TO-BE]
<ol>
  <li>영화 서비스를 백엔드/프론트로 분리하고 MVC 디자인 패턴으로 리팩토링</li>
  <li>영화 이벤트 유형 템플릿화 하여 관리자 사이트 기능으로 개발</li>
  <li>플래시 소스 제거 후 배너/메인 화면 설정을 관리자 사이트 기능으로 개발</li>
  <li>영화 예매 공통 서비스를 모듈화 하여 극장 API 개발</li>
  <li>극장사에서 추가된 데이터들은 모델링 되어 코드별로 관리되어 별도로 등록절차 없이 적용가능</li>
  <li>로그 내용 및 경로 개선</li>
  <li>요청/응답 내역 기록</li>
  <li>주문번호만으로 사용자의 서비스 이용경로 파악 가능</li>
</ol>

[사이트 이미지]

<img src="{{ site.url }}/IMG/PortFolio/YES24/sktmobilemoviemain.PNG.PNG">
<img src="{{ site.url }}/IMG/PortFolio/YES24/sktwebmoviemain.PNG">

<img src="{{ site.url }}/IMG/PortFolio/YES24/sktmobilemoviecardlist.PNG.PNG">
<img src="{{ site.url }}/IMG/PortFolio/YES24/sktwebmoviecardlist.PNG">


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
