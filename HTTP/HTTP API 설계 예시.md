
# HTTP API 설계 예시

## 파일 관리 시스템
- 파일 목록 /files -> GET
- 파일 조회 /files/{filename} -> GET
- 파일 등록 /files/{filename} -> PUT
- 파일 삭제 /files/{filename} -> DELETE
- 파일 대량 등록 /files -> POST

	### PUT - 신규 자원 등록 특징
- 클라이언트가 리소스 URI를 알고 있어야 한다.
	-- 파일등록 /files/{filename} -> PUT
	-- PUT /files/star.jpg
- 클라이언트가 직접 리소스의 URI를 지정한다.
- 스토어(Store)
	-- 클라이어너트가 관리하는 리소스 저장소
	-- 클라이언트가 리소스의 URI를 알고 관리
	-- 여기에서 스토어는/files
	
	### POST - 신규 자원 등록 특징 (대부분 POST를 쓴다)
	- 클라이언트는 등록될 리소스의 URI를 모른다.
		- 회원 등록 /members -> POST
		- POST /members
	- 서버가 새로 등록된 리소스 URI를 생성해준다.
		- HTTP/1.1 201 Created
		  Location: /members/100
	- 컬렉션(Collection)
		- 서버가 관리하는 리소스 디렉토리
		- 서버가 리소스의 URI를 생성하고 관리
		- 여기서 컬렉션은 /members

![image](https://user-images.githubusercontent.com/60098769/119212977-eb758200-baf6-11eb-832a-e462b0899d3c.png)

![image](https://user-images.githubusercontent.com/60098769/119212979-ef090900-baf6-11eb-9057-9b19a2829317.png)


