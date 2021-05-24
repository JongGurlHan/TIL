# 쿠키

![image](https://user-images.githubusercontent.com/60098769/119359098-36082180-bce4-11eb-91ef-bb24d46c5d0d.png)

-> 웹브라우저 내에는 쿠키 저장소가 있어서 서버가 로그인에 성공하면 응답해서 만든 user=홍길동을 저장한다.

![image](https://user-images.githubusercontent.com/60098769/119359258-66e85680-bce4-11eb-8eb1-6e61d4c2e47f.png)

-> 로그인이후 웹브라우저가 welcome페이지 들어가며 웹브라우저는 자동으로 서버에 요청을 보낼때 마다 쿠키를 뒤져서 쿠기값을 꺼내서 
    Cookie: user=홍길동 이라는 헤더를 만들어서 서버에 보낸다.

![image](https://user-images.githubusercontent.com/60098769/119359601-c34b7600-bce4-11eb-8935-bb21d7a90bb8.png)


## 쿠키
• 예) set-cookie: sessionId=abcde1234; expires=Sat, 26-Dec-2020 00:00:00 GMT; path=/; domain=.google.com; Secure
• 사용처
• 사용자 로그인 세션 관리
• 광고 정보 트래킹
• 쿠키 정보는 항상 서버에 전송됨
• 네트워크 트래픽 추가 유발
• 최소한의 정보만 사용(세션 id, 인증 토큰)
• 서버에 전송하지 않고, 웹 브라우저 내부에 데이터를 저장하고 싶으면 웹 스토리지 (localStorage, sessionStorage) 참고
• 주의!
• 보안에 민감한 데이터는 저장하면 안됨(주민번호, 신용카드 번호 등등)

### 쿠키 - 생명주기
• Set-Cookie: expires=Sat, 26-Dec-2020 04:39:21 GMT
• 만료일이 되면 쿠키 삭제
• Set-Cookie: max-age=3600 (3600초)
• 0이나 음수를 지정하면 쿠키 삭제
• 세션 쿠키: 만료 날짜를 생략하면 브라우저 종료시 까지만 유지
• 영속 쿠키: 만료 날짜를 입력하면 해당 날짜까지 유지
