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

운영업무중 이니시스 스테이징 결제 모듈 테스트중 아래와 같은 오류 발견

<pre><code>

[2022-01-05 17:07:16-Inicis 승인요청 payObj.AuthURL [PC] : ] https://stgstdpay.inicis.com/api/payAuth
[2022-01-05 17:07:16-Inicis 결제승인정보 PC : ] {"Tid":null,"ResultCode":"01","ResultMsg":"예외발생 : System.Net.WebException: 기본 연결이 닫혔습니다. 받기에서 예기치 않은 오류가 발생했습니다. 
---> System.ComponentModel.Win32Exception: 클라이언트 및 서버에 공용 알고리즘이 없기 때문에 통신할 수 없습니다
위치: System.Net.SSPIWrapper.AcquireCredentialsHandle(SSPIInterface SecModule, String package, CredentialUse intent, SecureCredential scc)\r\n 
위치: System.Net.Security.SecureChannel.AcquireCredentialsHandle(CredentialUse credUsage, SecureCredential& secureCredential)\r\n  
위치: System.Net.Security.SecureChannel.AcquireClientCredentials(Byte[]& thumbPrint)\r\n  
위치: System.Net.Security.SecureChannel.GenerateToken(Byte[] input, Int32 offset, Int32 count, Byte[]& output)\r\n  
위치: System.Net.Security.SecureChannel.NextMessage(Byte[] incoming, Int32 offset, Int32 count)\r\n  
위치: System.Net.Security.SslState.StartSendBlob(Byte[] incoming, Int32 count, AsyncProtocolRequest asyncRequest)\r\n  
위치: System.Net.Security.SslState.ForceAuthentication(Boolean receiveFirst, Byte[] buffer, AsyncProtocolRequest asyncRequest)\r\n  
위치: System.Net.Security.SslState.ProcessAuthentication(LazyAsyncResult lazyResult)\r\n  
위치: System.Threading.ExecutionContext.RunInternal(ExecutionContext executionContext, ContextCallback callback, Object state, Boolean preserveSyncCtx)\r\n  
위치: System.Threading.ExecutionContext.Run(ExecutionContext executionContext, ContextCallback callback, Object state, Boolean preserveSyncCtx)\r\n  
위치: System.Threading.ExecutionContext.Run(ExecutionContext executionContext, ContextCallback callback, Object state)\r\n  
위치: System.Net.TlsStream.ProcessAuthentication(LazyAsyncResult result)\r\n   위치: System.Net.TlsStream.Write(Byte[] buffer, Int32 offset, Int32 size)\r\n  
위치: System.Net.PooledStream.Write(Byte[] buffer, Int32 offset, Int32 size)\r\n   위치: System.Net.ConnectStream.WriteHeaders(Boolean async)\r\n  
--- 내부 예외 스택 추적의 끝 ---\r\n   위치: System.Net.HttpWebRequest.GetRequestStream(TransportContext& context)\r\n  

</code></pre>

MID도 정상이고 보내기 전 JSON데이터를 검열해봐도 문제가 없었는데 위와 같이 에러가남
기본연결이 닫혔을 경우 TLS 설정 생각해볼것.. 
현재 운영서버는 TLS 1.0 , 1.1 를 막고 1.2 만 Enable한 상태라서
이니시스 스테이징은 1.2 아래버전만 접근 가능 한 것 같다
그래서 설정 바꿔줌

레즈스트리 편집기에서
HKEY_LOCAL_MACHINE/SYSTEM/CurrentControlSet/Control/SecurityProviders/SCHANNEL/protocols
TLS 1.0 1.1 Client enable 값을 1 로 바꿔줌 (이니시스에 전달 할 정보만 1.0 / 1.1 로 바꿀꺼라서 server는 안바꿈)

후에 정상적으로 response받음



### SSL TLS 는 무엇인가?
SSL (Secure Socket Layers)과 TLS (Transport Layer Security)의 차이점
SSL은 TLS의 이전의 프로토콜
TLS(Transport Layer Security)는 SSL 3.0을 기초로 해서 IETF가 만든 프로토콜로 이는 SSL3.0을 보다 
안전하게 하고 프로토콜의 스펙을 더 정확하고 안정성을 높이는 목적으로 고안

SSL: 보안 소켓 계층(Secure Sockets Layer, SSL)
SSL은 웹사이트와 브라우저(혹은, 두 서버) 사이에 전송된 데이터를 암호화하여 인터넷 연결을 보안을 유지하는 표준 기술입니다. 
이는 해커가 개인 정보 및 금융 정보를 포함한 전송되는 모든 정보를 열람하거나 훔치는 것을 방지합니다.


TLS: 전송 계층 보안(Transport Layer Security, TLS)
TLS는 가장 최신 기술로 더 강력한 버전의 SSL입니다. 그러나 SSL이 더 일반적으로 사용되는 용어이기에, 여전히 보안 인증서는 SSL이라 불립니다. 


HTTPS: 하이퍼 텍스트 프로토콜 보안(Hyper Text Protocol Secure, HTTPS)
HTTPS는 웹사이트를 SSL/TLS 인증서로 보안하는 경우 URL 창에 표시됩니다. 
사용자는 브라우저 바의 잠금 기호를 클릭하여 인증서 발행, 


HTTP2 관련 참고 링크
<https://developers.google.com/web/fundamentals/performance/http2?hl=ko>

페이지 로드 시간(PLT)을 50% 줄입니다.
HTTP/2 주요목표
- 전체요청을 통해 지연 시간 줄여줌
- 응답 다중화
- HTTP 헤더 필드의 효율접 압축 -> 프로토콜 오버헤드 최소화

페이지 로드 시간(PLT)이 단축되는 효과를 볼 수 있다.


Qualys SSL Labs Service  안전한 상태인지 점검해주는 사이트 : <https://www.qualys.com>

운영하고 있는 서버를 조회하면 아래와 같이 등급이 표시되고
![TLSSSL](/IMG/postImg/sslreportbyQualys.PNG)
해당 프로토콜이 막아져있는지 아닌지 확인 할 수 있다.
![TLSSSL](/IMG/postImg/sslreportbyQualysprotocol.PNG)


TLS 핸드셰이크

전송 계층 보안(SSL 또는 TLS) 연결이 시작되면 레코드는 핸드셰이크 메시징 프로토콜(콘텐츠 타입 22)인 "control" 프로토콜을 감싼다. 
이 프로토콜을 사용하여 TLS에 의한 실제 애플리케이션 데이터 교환을 위해 양측에 필요한 모든 정보를 교환한다.
이 프로토콜은 세션의 보안 특성을 협상하기 위해 사용된다.
![TLSSSL](/IMG/postImg/TLSSSL_SAT.PNG)

![TLSSSL](/IMG/postImg/TLS_통신.PNG)




***
