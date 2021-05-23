# http 헤더 일반정보

• From: 유저 에이전트의 이메일 정보
• Referer: 이전 웹 페이지 주소
• User-Agent: 유저 에이전트 애플리케이션 정보
• Server: 요청을 처리하는 오리진 서버의 소프트웨어 정보
• Date: 메시지가 생성된 날짜

## Referer
이전 웹 페이지 주소
• 현재 요청된 페이지의 이전 웹 페이지 주소
• A -> B로 이동하는 경우 B를 요청할 때 Referer: A 를 포함해서 요청
• Referer를 사용해서 유입 경로 분석 가능
• 요청에서 사용
• 참고: referer는 단어 referrer의 오타

## User-Agent
유저 에이전트 애플리케이션 정보
• user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/
537.36 (KHTML, like Gecko) Chrome/86.0.4240.183 Safari/537.36
• 클라이언트의 애플리케이션 정보(웹 브라우저 정보, 등등)
• 통계 정보
• 어떤 종류의 브라우저에서 장애가 발생하는지 파악 가능
• 요청에서 사용

## Server
요청을 처리하는 ORIGIN 서버의 소프트웨어 정보
• Server: Apache/2.2.22 (Debian)
• server: nginx
• 응답에서 사용

##Date
메시지가 발생한 날짜와 시간
• Date: Tue, 15 Nov 1994 08:12:31 GMT
• 응답에서 사용


# http 헤더 특별정보
• Host: 요청한 호스트 정보(도메인)
• Location: 페이지 리다이렉션
• Allow: 허용 가능한 HTTP 메서드
• Retry-After: 유저 에이전트가 다음 요청을 하기까지 기다려야 하는 시간

## Host
요청한 호스트 정보(도메인)
• 요청에서 사용
• 필수
• 하나의 서버가 여러 도메인을 처리해야 할 때
• 하나의 IP 주소에 여러 도메인이 적용되어 있을 때

![image](https://user-images.githubusercontent.com/60098769/119266727-e0ba0a80-bc26-11eb-9457-c97c18079142.png)

한 서버에 여러 애플리케이션이 구동될 수 있다. 

![image](https://user-images.githubusercontent.com/60098769/119266774-0e9f4f00-bc27-11eb-823e-4011a7084356.png)
근데 만약에 호스트가 없으면 /hello 라고 요청을 보냈을때 서버입장에서 어떤 어플리케이션에 요청이 들어가야할지 알 수 가 없다.(ip로만 통신하기 때문)

![image](https://user-images.githubusercontent.com/60098769/119266813-31316800-bc27-11eb-81c2-a473727c450d.png)
->호스트 헤더가 있기 때문에 서버에서 어플리케이션을 찾아서 요청을 보낼 수 있다. 따라서 host 정보는 필수다!


## Location
페이지 리다이렉션
• 웹 브라우저는 3xx 응답의 결과에 Location 헤더가 있으면, Location 위치로 자동 이동
(리다이렉트)
• 응답코드 3xx에서 설명
• 201 (Created): Location 값은 요청에 의해 생성된 리소스 URI
• 3xx (Redirection): Location 값은 요청을 자동으로 리디렉션하기 위한 대상 리소스를
가리킴

## Allow
허용 가능한 HTTP 메서드
• 405 (Method Not Allowed) 에서 응답에 포함해야함
• Allow: GET, HEAD, PUT


# 인증
• Authorization: 클라이언트 인증 정보를 서버에 전달
• WWW-Authenticate: 리소스 접근시 필요한 인증 방법 정의

## Authorization
클라이언트 인증 정보를 서버에 전달
• Authorization: Basic xxxxxxxxxxxxxxxx

## WWW-Authenticate
리소스 접근시 필요한 인증 방법 정의
• 리소스 접근시 필요한 인증 방법 정의
• 401 Unauthorized 응답과 함께 사용
• WWW-Authenticate: Newauth realm="apps", type=1,
title="Login to \"apps\"", Basic realm="simple"
