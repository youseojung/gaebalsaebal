---
layout: post
title:  "Sql - 프로시저 생성시 자주쓰는 구문"
date:   2019-06-12
excerpt: "프로시저 시작할때 등장하는 구문 무슨뜻인지.."
sql: true
---


### 수행한 열 카운트 조회 켜기/끄기
~~~sql
SET NOCOUNT ON;
SET NOCOUNT OFF;
~~~


### 프로시저에 사용되는 구문
~~~sql
SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED; 
-- 트랜잭션이 커밋되지 않아도 READ 가능 , 무결성 보장안됨
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
-- 커밋한 데이터만 조회
~~~

