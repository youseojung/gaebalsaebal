---
layout: post
title:  "ssl과 HTTP/2 공부하자"
date:   2022-01-06
excerpt: "이니시스 스테이징 결제 하다가 발견한 http2"
operation: true
tag:
- ssl
- HTTP/2
comments: true
---


    
### SSL TLS 는 무엇인가?
SSL (Secure Socket Layers)과 TLS (Transport Layer Security)의 차이점
SSL은 TLS의 이전의 프로토콜입니다.

, TLS(Transport Layer Security)는 SSL 3.0을 기초로 해서 IETF가 만든 프로토콜로 이는 SSL3.0을 보다 
안전하게 하고 프로토콜의 스펙을 더 정확하고 안정성을 높이는 목적으로 고안되었습니다.

SSL: 보안 소켓 계층(Secure Sockets Layer, SSL)
SSL은 웹사이트와 브라우저(혹은, 두 서버) 사이에 전송된 데이터를 암호화하여 인터넷 연결을 보안을 유지하는 표준 기술입니다. 
이는 해커가 개인 정보 및 금융 정보를 포함한 전송되는 모든 정보를 열람하거나 훔치는 것을 방지합니다.


TLS: 전송 계층 보안(Transport Layer Security, TLS)
TLS는 가장 최신 기술로 더 강력한 버전의 SSL입니다. 그러나 SSL이 더 일반적으로 사용되는 용어이기에, 여전히 보안 인증서는 SSL이라 불립니다. 


HTTPS: 하이퍼 텍스트 프로토콜 보안(Hyper Text Protocol Secure, HTTPS)
HTTPS는 웹사이트를 SSL/TLS 인증서로 보안하는 경우 URL 창에 표시됩니다. 
사용자는 브라우저 바의 잠금 기호를 클릭하여 인증서 발행, 


HTTP2 관련 
https://developers.google.com/web/fundamentals/performance/http2?hl=ko

페이지 로드 시간(PLT)을 50% 줄입니다.


Qualys SSL Labs Service  안전한 상태인지 점검해주는 사이트 
https://www.qualys.com/

![TLSSSL](/IMG/postImg/TLSSSL_SAT.PNG)


***
