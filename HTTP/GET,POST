# HTTP 메서드 -GET, POST

HTTP메서드는 클라이언트에서 서버로 요청할때 기대하는 행동

## GET
- 리소스 조회
- 서버에 전달하고 싶은 데이터는 query(쿼리 파라미터, 쿼리 스트링)를 통해서 전달
- 메시지 바디를 사용해서 데이터를 전달할 수 있지만, 지원하지 않는 곳이 많아서 권장x 

![4 http-method-17](https://user-images.githubusercontent.com/60098769/119113054-abaf8b80-ba5f-11eb-864e-f75fd4d69e5d.png)

서버에 GET메시지를 받으면 내부의 DB조회후 JSON 형식의(다른 형식도 가능) 데이터 만든다음

![4 http-method-18](https://user-images.githubusercontent.com/60098769/119113063-ace0b880-ba5f-11eb-934e-63767182e72d.png)

응답메시지를 만들어서 client로 보낸다. 


## POST
- 요청 데이터 처리
- ** 메시지 바디를 통해 서버로 요청 데이터 전달
- 서버는 요청 데이터를 처리
- 주로 전달된 데이터로 신규 리소스 등록, 프로세스 처리에 사용

![4 http-method-20](https://user-images.githubusercontent.com/60098769/119114113-cc2c1580-ba60-11eb-82b5-d00a8d33d4c4.png)

![4 http-method-21](https://user-images.githubusercontent.com/60098769/119114118-cd5d4280-ba60-11eb-93b0-8287bb2c8883.png)

서버에서 데이터를 받아서 DB에 등록하고 신규리소스 식별자를 생성해서 

![4 http-method-22](https://user-images.githubusercontent.com/60098769/119114525-33e26080-ba61-11eb-974f-b5020c8df237.png)

- 신규로 자원이 생성되면 보통 201 Created로 응답한다. 
- 그리고 Location에 자원이 생성된 경로를 보여준다.   
- 그리고 등록된 자원에 대한 데이터도 보여준다.

### post 정리
1. 새 리소스 생성(등록)
- 서버가 아직 식별하지 않은 새 리소스 생성
2. 요청 데이터 처리
- 단순히 데이터를 생성하거나, 변경하는 것ㅇ르 넘어서 프로세스를 처리해야 하는 경우
 ex) 주문에서 결제완료 -> 배달시작 -> 배달완료 처럼 단순히 값 변경을 넘어 프로세스의 상태가 변경되는 경우
- POST의 결과로 새로운 리소스가 생성되지 않을 수도 있음
 ex) POST /oders/{orderId}/start-delivery **컨트롤(URI)**
 3. 다른 메서드로 처리하기 애매한 경우
 - JSON으로 조회 데이터를 넘겨야 하는데, GET메서드를 사용하기 어려운 경우
 - 애매하면 POST
