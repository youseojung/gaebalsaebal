---
layout: post
title:  "HTTP헤더"
date:   2022-05-22
excerpt: "TCP 헤더 구조 "
study: true
comments: true
---




요청과 응답에 모두 사용되는 공통 헤더
---
- Date
> HTTP 메시지가 만들어진 시각입니다. 자동으로 만들어집니다.
- Connection
> 기본적으로 keep-alive로 되어있는데 사실상 아무런 의미도 없습니다. HTTP/2에서는 아예 사라져버렸습니다.
- Content-Length
> 요청과 응답 메시지의 본문 크기를 바이트 단위로 표시
- Content-Type
> 컨텐츠의 타입(MIME)과 문자열 인코딩(utf-8 등등)을 명시
- Content-Language
> * 사용자의 언어를 뜻합니다. 요청이나 응답이 무슨 언어인지와는 관련 없음
> * 한국 사람한테 일본어를 가르치는 사이트일 경우, 페이지 언어는 일본어더라도 Content-Language는 ko-KR일 수 있습니다.
- Content-Encoding
> 컨텐츠 압축된 방식. 응답 컨텐츠를 br, gzip, deflate 등의 알고리즘으로 압축해서 보내면, 브라우저가 알아서 해제해서 사용

요청헤더(Request Header)
---
- Host
> 서버의 도메인 네임이 나타나는 부분입니다(포트 포함). Host 헤더는 반드시 하나가 존재해야 합니다.(http 1.1 은 필수)
- Cookie
> 서버로부터 받은 쿠키를 다시 서버에게 보냄
- User-Agent
> 현재 사용자가 어떤 클라이언트 정보(운영체제와 브라우저버전 같은 것)를 이용해 요청을 보냈는지 나옴 
(핸드폰으로접속?pc로접속? 알 수 있음)
- Accept
> * Accept 헤더는 요청을 보낼 때 서버에 이런 타입(MIME)의 데이터를 보내줬으면 좋겠다고 명시할 때 사용
> * Accept-Encoding, Accept-Charset, Accept-Language 등이 있음
- Authorization
> * 인증 토큰(JWT든, Bearer 토큰이든)을 서버로 보낼 때 사용하는 헤더
> * 예시: Authorization: Bearer XXXXXXXXXXXXX
> * Basic이나 Bearer같은 토큰의 종류를 먼저 알리고 그 다음에 실제 토큰 문자를 적어 보냄
- Origin
> POST같은 요청을 보낼 때, 요청이 어느 주소에서 시작되었는지를 나타냅니다. 여기서 요청을 보낸 주소와 받는 주소가 다르면 CORS 문제가 발생
- Referer
> * 이 페이지 이전의 페이지 주소
> Referer은 오타. Referrer가 표준어인데 실수로 Referer로 만들었다고 함

응답헤더(Response Header)
response의정보 , 서버의 정보 , 클라이언트에 대한 추가정보 요구 
---
-Age
> * 리소스의 지정 경과시간 (캐시서버가 오리진 서버를 언제 마지막으로 확인했는지?)
- Access-Control-Allow-Origin
> * 요청을 보내는 프론트 주소와 받는 백엔드 주소가 다르면 CORS 에러가 발생하는데요. 이 때 서버에서 응답 메시지 Access-Control-Allow-Origin 헤더에 프론트 주소를 적어주어야 에러가 나지 않습니다.
> * Access-Control-Allow-Origin: www.zerocho.com
> * Access-Control-Allow-Origin: *
> * 유사한 헤더로 Access-Control-Request-Method, Access-Control-Request-Headers, Access-Control-Allow-Methods, Access-Control-Allow-Headers 등이 있습니다. Request랑 Allow에서 Method 단수 복수 주의
> * CORS 요청 시에는 미리 OPTIONS 주소로 서버가 CORS를 허용하는지 물어봅니다. 이 때 Access-Control-Request-Method로 실제로 보내고자 하는 메서드를 알리고, Access-Control-Request-Headers로 실제로 보내고자 하는 헤더들을 알립니다. Allow 친구들은 Request에 대응되는 애들로, 서버가 허용하는 메서드와 헤더를 응답하는데 사용됩니다. Request랑 Allow가 일치하면 CORS 요청이 이루어지는 것이죠.
- Allow
> * Allow 헤더는 Access-Control-Allow-Methods랑 비슷하지만, CORS 요청 외에도 적용된다는 데에 차이가 있습니다
>  * 즉 GET www.zerocho.com은 되고, POST www.zerocho.com은 허용하지 않는 경우, 405 Method Not Allowed 에러를 응답하면서 헤더로 Allow: GET 을 보냄
- Content-Disposition
> 응답 본문을 브라우저가 어떻게 표시해야 할지 알려주는 헤더입니다. inline인 경우 웹페이지 화면에 표시되고, attachment인 경우 다운로드
> * Content-Disposition: inline
> * Content-Disposition: attachment; filename='filename.csv'
- Etag
> * 리소스 특정하기 위한 정보 (리소스 갱신 할때 Etag도 갱신됨)
- Location
> * 300번대 응답이나 201 Created 응답일 때 어느 페이지로 이동할지를 알려주는 헤더
> * HTTP/1.1 302 Found Location: / 
> 이런 응답이 왔다면 브라우저는 / 주소로 리다이렉트합니다.
- Content-Security-Policy
> 다른 외부 파일들을 불러오는 경우, 차단할 소스와 불러올 소스를 여기에 명시

쿠키 헤더 필드
유저 식벼로가 상태 관리에 사용하는 쿠키
---
1. Set-Cookie : 서버에서 클라이언트로 쿠키를 포함하여 응답
2. Cookie : 클라이언트가 서버에서 받은 쿠키를 저장하고 http 요청 시 서버로 전달


기타헤더필드
X-XXS-Projection
:크로스 사이트 스크립팅(xss)보호기능 필터 제어




















