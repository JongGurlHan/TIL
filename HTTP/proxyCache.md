## 프록시 캐시
이미지를 제공하는 원 소스가 있는 서버를 원 서버라고 한다.
원소스에 직접 접근하면 시간이 오래 걸릴 수 있다. 

![proxy1](https://user-images.githubusercontent.com/60098769/119478606-e7619280-bd8a-11eb-8e1a-7956ac59e685.JPG)

그래서 프록시 캐시 서버를 도입한다. 
한국 어딘가에 프록시 캐시 서버를 설치하면 
웹 브라우저가 프록시 캐시 서버에 접근하게 된다.

![proxy2](https://user-images.githubusercontent.com/60098769/119478612-e7fa2900-bd8a-11eb-86c2-251a0cbf91ee.JPG)

응답시간이 기존보다 훨씬 빨라진다.
그래서 글로벌 서비스(ex 유튜브)는 cdn서비스를 이용한다.
첫번째 요청은 느리지만 한 번 다운받으면 다음 유저부턴 빠르게 조회할 수 있다.
