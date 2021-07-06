---
layout: post
title:  "운영이슈 - 서버이전 iis 세팅 동기화하기."
date:   2021-07-06
excerpt: "커맨드로  iis세팅 한번에 하기"
operation: true
tag:
- iis
comments: true
---


    
### 서버 이전으로 iis 세팅 쉽게하기 (cmd이용)

***

이미지 서버 노후화로 교체가 필요해서 
C:\Windows\System32\inetsrv\config\applicationhost.config 를 복사했지만
윈도우  2008 -> 2016 , iis버전은 7.0 -> 10.0 이여서 변경이 안된다ㅜㅜ
이미지 서버 응용프로그래밍풀 설정과 가상디렉터리가 너무 많아서 gui 로 일일히 변경하기 힘들때 사용

appcmd :인터넷정보서비스를 빠르게 제어할수있는 커맨드 


|명칭|지원되는개체유형|
|------|---|
|SITE|가상 사이트 관리|
|APP|응용프로그램 관리|
|APPPOOL|응용프로그램풀 관리|
|VDIR|가상디렉터리 관리|


```cs

c:\windows\system32\inetsrv\appcmd add site /name:"[사이트이름]" /bindings:http://[URL]:80 /physicalPath:"D:\MOVIE\[사이트이름]"
<-- 가상 사이트를 만든다-->

c:\windows\system32\inetsrv\appcmd add apppool /name:[사이트이름] /managedRuntimeVersion:v2.0
<-- 응용프로그램밍 풀의 버전설정-->

c:\windows\system32\inetsrv\appcmd set app "[사이트이름]/" /applicationPool:[사이트이름]
<-- 응용프로그램의 응용프로그램 풀 설정-->

c:\windows\system32\inetsrv\appcmd add app /site.name:"[사이트이름]" /path:/ImageResize /physicalPath:D:\[경로]
<-- 응용프로그램 추가 -->

c:\windows\system32\inetsrv\appcmd set app "[사이트이름]/ImageResize/" /applicationPool:[사이트이름]
<-- 추가된 응용프로그램 설정-->


c:\windows\system32\inetsrv\appcmd set site /site.name:"[사이트이름]" /+bindings.[protocol='http',bindingInformation='*:80:[URL]']
c:\windows\system32\inetsrv\appcmd set site /site.name:"[사이트이름]" /+bindings.[protocol='https',bindingInformation='*:443:[URL]']
<-- 웹 호스팅 설정-->

c:\windows\system32\inetsrv\appcmd add vdir /app.name:"[사이트이름]/" /path:/aaa /physicalPath:\\[IP]\[경로] /userName:"[ID]" /password:"[PW]"
c:\windows\system32\inetsrv\appcmd add vdir /app.name:"[사이트이름]/" /path:/All /physicalPath:\\[IP]\[경로] /userName:"[ID]" /password:"[PW]"
c:\windows\system32\inetsrv\appcmd add vdir /app.name:"[사이트이름]/" /path:/btn /physicalPath:\\[IP]\[경로] /userName:"[ID]" /password:"[PW]""
<-- 가상 디렉토리 설정 -->
```


