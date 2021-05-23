# 3xx 리다이렉션

## 리다이렉션 이해
- 웹 브라우저는 3xx 응답의 결과에 Location 헤더가 있으면, Location 위치로 자동 이동(리다이렉트)


![6 http-status-14](https://user-images.githubusercontent.com/60098769/119254661-77b89f80-bbf2-11eb-98a7-fc844e61b9ed.png)

- "/event 경로는 안쓰고 /new-event로 바뀌었어" 라고 301코드를 쓰고 클라이언트에게 알려준다.  
- 그럼 웹브라우저는 서버에 다시 /new-event 로 요청한다 
- 그럼 서버는 /new-event에 해당하는 html을 응답한다.

## 리다이렉션 종류
1. 영구 리다이렉션 - 특정 리소스의 URI가 영구적으로 이동
ex)/members -> /users
2. 일시 리다이렉션 - 일시적인 변경
  - 주문 완료 후 주문 내역 화면으로 이동
  - PRG: Post / Redirect / Get
3. 특수 리다이렉션
 - 결과 대신 캐시를 사용
 
 ## 영구 리다이렉션
 - 리소스의 URI가 영구적으로 이동
 - 원래의 URL를 사용X, 검색 엔진 등에서도 변경 인지
 - 301 Moved Permanetly
  - 리다이렉트시 요청 메서드가 GET으로 변하고, 본문이 제거될 수 있음(MAY)
 - 308 Permanent Redirect
  - 301과 기능은 같음
  - 리다이렉트시 요청 메서드와 본문 유지(처음 POST를 보내면 리다이렉트도 POST 유지)
  
  ![image](https://user-images.githubusercontent.com/60098769/119255060-a2a3f300-bbf4-11eb-863e-e034b69ec1c5.png)
  
  ![image](https://user-images.githubusercontent.com/60098769/119255087-c23b1b80-bbf4-11eb-83d5-55797ddb2cd8.png)
-> 301과 다르게 308은 POST유지하고 메시지 본문을 유지한다. 그럼 데이터가 등록된다. // 하지만 실무에서는 GET으로 돌리는게 낫다



 ## 일시적 리다이렉션
 
 - 리소스의 URI가 일시적으로 변경
 - 따라서 검색 엔진 등에서 URL을 변경하면 안됨
 
 - 302 FOUND
  - 리다이렉트시 요청 메서드가 GET으로 변하고, 본문이 제거될 수 있음(MAY)
 - 307 Temporary Redirect
  - 302와 기능은 같음
  - 리다이렉트시 요청 메서드와 본문유지(요청 메서드를 변경하면 안된다. must not)
 - 303 See other
  - 302와 기능은 같은
  - 리다이렉트시 요청 메서드가 GET으로 변경
  
  ![image](https://user-images.githubusercontent.com/60098769/119255512-34146480-bbf7-11eb-9d29-e8f624482113.png)

![image](https://user-images.githubusercontent.com/60098769/119255516-3d053600-bbf7-11eb-8677-d313f0adbdac.png)


## PRG: Post / Redirect / Get
- POST로 주문후에 새로 고침으로 인한 중복 주문 방지
- POST로 주문 후에 주문 결과 화면을 GET메서드로 리다이렉트 (보통은 주문 결과 페이지 조회)
- 새로고침해도 결과 화면을 GET으로 조회
- 중복 주문 대신에 결과 화면만 GET으로 다시 요청
 
 ### PRG 이후 리다이렉트
  - URL이 이미 POST -> GET으로 리다이렉트 됨
  - 새로 고침해도 GET으로 결과 화면만 조회
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
