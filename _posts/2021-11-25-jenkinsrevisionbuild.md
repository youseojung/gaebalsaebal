---
layout: post
title:  "Jenkins 전달받은 파라미터값으로  revision 버전으로 빌드하기."
date:   2021-11-25
excerpt: "revision , tag 버전 별로 빌드하기"
operation: true
tag:
- Jenkins 
comments: true
---



## Jenkins 전달받은 파라미터값으로  revision 버전으로 빌드하기

(jquery.hpi , git-parameter.hpi 플러그인 설치해줘야함)

![jenkins](https://github.com/youseojung/youseojung.github.io/blob/master/IMG/postImg/jenkinsSetting%20%20StringParameter.png)
![jenkins](https://github.com/youseojung/youseojung.github.io/blob/master/IMG/postImg/jenkinsSetting%20%20StringParameter2.png)
유의할점 : String Parmeter 로 세팅하여 매개변수명과  소스코드관리의 Branch Specifier ${매개변수명} 이 같아야함
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

![jenkins](https://raw.githubusercontent.com/youseojung/youseojung.github.io/master/IMG/postImg/jenkinsSettingStringParameter3.png)
![jenkins](https://raw.githubusercontent.com/youseojung/youseojung.github.io/master/IMG/postImg/jenkinsSettingStringParameter4.png)
파라미터 값 안에 리비전번호(커밋번호) / 태그명을 넣으면 해당하는 소스가 빌드된다.


#### 태그 조회하기

우선 git tag 명령으로 (-l, `--list`는 옵션) 이미 만들어진 태그가 있는지 확인할 수 있다.


$ git tag
v0.1
v1.3

$ git tag -l "v1.8.5*"<br>
v1.8.5 <br>
v1.8.5-rc0 <br>
v1.8.5-rc1 <br>
