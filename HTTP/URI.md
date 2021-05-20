# URI
Uniform Resource Identifier

![url2](https://user-images.githubusercontent.com/60098769/118999042-e57f8400-b9c4-11eb-8659-a93b20f9af82.png)

URI는 자원을 식별하는데 크게 2가지로 나눌 수 있다. 

1. URL: 리소스의 위치
2. URN: 리소스의 이름

이름을 부여하면 리소스를 찾기가 힘들다 그래서 보통 URL를 쓴다.

![url3](https://user-images.githubusercontent.com/60098769/118999018-e1536680-b9c4-11eb-9700-ac22a932b6ad.png)

![url4](https://user-images.githubusercontent.com/60098769/118998977-da2c5880-b9c4-11eb-819d-220dbd80890f.png)

- 스키마에 주로 프로토콜 정보들어간다
- userinfo@ : url에 사용자 정보 포함해서 인증, 거의 안씀
- host: 도메인명 또는 IP 주소를 직접 사용가능
- PORT: 포트, 일반적으로 생략, 생략시 http는 80, https는 443
- path: 리소스가 있는 경로, 계층적 구조로 되어있다.
  ex) /hoem/file1.jpg
- query: key=value 형태, ?로 시작, &로 추가가능 , query parameter, query string 등으로 불림.
- fragment: html 내부 북마크 등에 사용, 서버에 전송하는 정보 아님
