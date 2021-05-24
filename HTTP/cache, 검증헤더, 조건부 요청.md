# 캐시

![image](https://user-images.githubusercontent.com/60098769/119363560-e6782480-bce8-11eb-90d2-3f7d9df56298.png)

![image](https://user-images.githubusercontent.com/60098769/119363589-ee37c900-bce8-11eb-80f2-1fd971f4443c.png)


### 캐시가 없을 때 
• 데이터가 변경되지 않아도 계속 네트워크를 통해서 데이터를 다운로드 받아야 한다.
• 인터넷 네트워크는 매우 느리고 비싸다.
• 브라우저 로딩 속도가 느리다.
• 느린 사용자 경험

![image](https://user-images.githubusercontent.com/60098769/119363764-24754880-bce9-11eb-9ff1-668abb7f789c.png)

-> 캐시를 적용하면 cahce-control(캐시가 유효한 시간)을 헤더에 넣어준다
  max-age=60 : 60초
  
![image](https://user-images.githubusercontent.com/60098769/119363927-54bce700-bce9-11eb-8600-8b28c8c8adfc.png)

![image](https://user-images.githubusercontent.com/60098769/119364013-6dc59800-bce9-11eb-918a-d65623f7e2f0.png)

두번째 요청할땐 일단 캐시를 뒤진다. 
캐시가 60초 유효한다면 네트워크를 탈 필요없이 바로 캐시에서 조회한다.

### 캐시가 있을 때
• 캐시 덕분에 캐시 가능 시간동안 네트워크를 사용하지 않아도 된다.
• 비싼 네트워크 사용량을 줄일 수 있다.
• 브라우저 로딩 속도가 매우 빠르다.
• 빠른 사용자 경험

![image](https://user-images.githubusercontent.com/60098769/119364173-99488280-bce9-11eb-8248-cbd2cdc2aefc.png)

![image](https://user-images.githubusercontent.com/60098769/119364337-be3cf580-bce9-11eb-82c8-3e2da51c7ae6.png)

캐시 유효 시간이 초과하면, 서버를 통해 데이터를 다시 조회하고, 캐시를 갱신한다.
이때 다시 네트워크 다운로드가 발생한다.

**만약 캐시가 만료되었고 클라이언트가 서버에 요청하는 데이터가 같다면? 1M가 되는 데이터를 다시 받아야 할까?

## 검증 헤더와 조건부 요청

![image](https://user-images.githubusercontent.com/60098769/119364791-3c999780-bcea-11eb-81ed-4619d4e74e6a.png)

캐시 시간 초과
• 캐시 만료후에도 서버에서 데이터를 변경하지 않음
• 생각해보면 데이터를 전송하는 대신에 저장해 두었던 캐시를 재사용 할 수 있다.
• 단 클라이언트의 데이터와 서버의 데이터가 같다는 사실을 확인할 수 있는 방법 필요

![image](https://user-images.githubusercontent.com/60098769/119365323-c6e1fb80-bcea-11eb-8ab0-5636a930defc.png)
-> Last-Modified: 데이터가 마지막에 수정된 시간

![image](https://user-images.githubusercontent.com/60098769/119365484-ee38c880-bcea-11eb-8b84-8278da46953c.png)

![image](https://user-images.githubusercontent.com/60098769/119365576-0577b600-bceb-11eb-87fa-55343ebcd7a8.png)

만약 60초가 지나면 웹브라우저가 서버에 요청을 보낼 때 **if-modified-since :2020년 11월 10일 10:10:10** 라는 요청헤더를 붙인고 요청하면
서버는 서버에서 데이터 수정 여부를 검증한다. 검증했을때 날짜가 같은지 판단하고 같다면 

![image](https://user-images.githubusercontent.com/60098769/119365976-74eda580-bceb-11eb-8988-9926c950490b.png)
![image](https://user-images.githubusercontent.com/60098769/119365998-7a4af000-bceb-11eb-99a5-28e7a86628ef.png)

**304 not modified 붙여서 응답한다. 이때 http바디가 없다.**
기존에는 1.1m만 전송했지만 이번엔은 헤더만 전송하므로 훨씬 가벼워진다.

![image](https://user-images.githubusercontent.com/60098769/119366949-71a6e980-bcec-11eb-88cd-708a1fd6d099.png)
그렇게 초기화된 캐시를 다시 가져와서 쓴다.


### 검증 헤더와 조건부 요청
검증헤더:last modified~~ 
조건부 요청: if-modified-since:~~~
정리
• 캐시 유효 시간이 초과해도, 서버의 데이터가 갱신되지 않으면
• 304 Not Modified + 헤더 메타 정보만 응답(바디X)
• 클라이언트는 서버가 보낸 응답 헤더 정보로 캐시의 메타 정보를 갱신
• 클라이언트는 캐시에 저장되어 있는 데이터 재활용
• 결과적으로 네트워크 다운로드가 발생하지만 용량이 적은 헤더 정보만 다운로드
• 매우 실용적인 해결책

### 검증 헤더와 조건부 요청2
• 검증 헤더
  • 캐시 데이터와 서버 데이터가 같은지 검증하는 데이터
  • Last-Modified , ETag
• 조건부 요청 헤더
  • 검증 헤더로 조건에 따른 분기
  • If-Modified-Since: Last-Modified 사용
  • If-None-Match: ETag 사용
  • 조건이 만족하면 200 OK
  • 조건이 만족하지 않으면 304 Not Modified
  
  
 • If-Modified-Since: 이후에 데이터가 수정되었으면?
  • 데이터 미변경 예시
    • 캐시: 2020년 11월 10일 10:00:00 vs 서버: 2020년 11월 10일 10:00:00
    • 304 Not Modified, 헤더 데이터만 전송(BODY 미포함)
    • 전송 용량 0.1M (헤더 0.1M, 바디 1.0M)
• 데이터 변경 예시
  • 캐시: 2020년 11월 10일 10:00:00 vs 서버: 2020년 11월 10일 11:00:00
  • 200 OK, 모든 데이터 전송(BODY 포함)
  • 전송 용량 1.1M (헤더 0.1M, 바디 1.0M)

### Last-Modified, If Modified-Since 단점
• 1초 미만(0.x초) 단위로 캐시 조정이 불가능
• 날짜 기반의 로직 사용
• 데이터를 수정해서 날짜가 다르지만, 같은 데이터를 수정해서 데이터 결과가 똑같은 경우(ex a-> b 에서 다시 b -> a)
• 서버에서 별도의 캐시 로직을 관리하고 싶은 경우
  • 예) 스페이스나 주석처럼 크게 영향이 없는 변경에서 캐시를 유지하고 싶은 경우
  
**이것의 단점을 보완한것이 Etag!

### ETag, If-None-Match
• ETag(Entity Tag)
• 캐시용 데이터에 임의의 고유한 버전 이름을 달아둠
• 예) ETag: "v1.0", ETag: "a2jiodwjekjl3"
• 데이터가 변경되면 이 이름을 바꾸어서 변경함(Hash를 다시 생성)
• 예) ETag: "aaaaa" -> ETag: "bbbbb"
• 진짜 단순하게 ETag만 보내서 같으면 유지, 다르면 다시 받기!

![image](https://user-images.githubusercontent.com/60098769/119370470-42927700-bcf0-11eb-8ca0-306832e8314a.png)

![image](https://user-images.githubusercontent.com/60098769/119370525-5342ed00-bcf0-11eb-97ed-20458e5628a0.png)

![image](https://user-images.githubusercontent.com/60098769/119370549-59d16480-bcf0-11eb-96f4-01a985c37d50.png)

![image](https://user-images.githubusercontent.com/60098769/119370564-5d64eb80-bcf0-11eb-8228-fca446d1f68c.png)

![image](https://user-images.githubusercontent.com/60098769/119370598-6c4b9e00-bcf0-11eb-859f-544d1ea82d8c.png)

![image](https://user-images.githubusercontent.com/60098769/119370636-77063300-bcf0-11eb-9961-5590db60bfdf.png)

![image](https://user-images.githubusercontent.com/60098769/119370653-7a99ba00-bcf0-11eb-95fc-2399eef86f36.png)

![image](https://user-images.githubusercontent.com/60098769/119370668-7f5e6e00-bcf0-11eb-9230-34f83448742f.png)

### Etag, If-None-Match 정리
• 진짜 단순하게 ETag만 서버에 보내서 같으면 유지, 다르면 다시 받기!
• 캐시 제어 로직을 서버에서 완전히 관리
• 클라이언트는 단순히 이 값을 서버에 제공(클라이언트는 캐시 메커니즘을 모름)
• 예)
• 서버는 배타 오픈 기간인 3일 동안 파일이 변경되어도 ETag를 동일하게 유지
• 애플리케이션 배포 주기에 맞추어 ETag 모두 갱신



