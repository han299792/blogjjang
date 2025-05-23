

언어를 심도 깊게 이해하는 것이란 뭘까....
- **goroutine이 많을 때 메모리가 어떻게 소비되는지**, 병목은 어디서 생기는지 이해한다
    
- **interface와 type embedding**으로 유연하게 추상화해서 팀이 유지보수하기 쉽게 구조를 짠다
    
- **context 패턴**을 사용해 cancel, timeout 처리를 제대로 넣는다
    
- `sync.Mutex`와 `channel`을 언제 어떻게 쓸지 상황에 맞게 선택한다
    
- GC 동작 원리를 알아서, **메모리 누수를 예방**하고 튜닝도 할 수 있다


gin 
golang으로 적힌 웹 프레임워크 
마티니 라이크 api란 뭘까
특징으로는 빠르고, 미들웨어를 잘 지원하며, 다비지 콜렉터랑 json도 잘 된다 
좀 더 자세하게 살펴보면 

왜 빠른가
Radix tree based rounting 을 지원한다. 
Radix tree란? 접두사 트리를 즉 공통 부분을 압축하는 구조
일반 trie보다 더 적은 노드를 사용한다. 
접두사 검색에는 부적합하다. 
r.GET("/user/profile", ...)
r.GET("/user/settings", ...) 이렇게 묶으니까 url 탐색해서 그런거임
go rounter랑 gin를 만들어도 되고 


## **2. Gin 기본 구조 이해를 위한 키워드**

|**목적**|**키워드/라이브러리**|**설명**|
|---|---|---|
|웹 프레임워크|github.com/gin-gonic/gin|REST API 라우팅 담당|
|DB ORM|gorm.io/gorm, gorm.io/driver/sqlite|데이터베이스 연결/쿼리|
|Excel 파싱|github.com/xuri/excelize|.xlsx 파일 읽기|
|환경변수|github.com/joho/godotenv|.env 파일 불러오기|
|Swagger 문서화|github.com/swaggo/gin-swagger|자동 API 문서 생성|
|파일 업로드|"mime/multipart" + Gin|엑셀 파일 업로드 API 구현 시 사용|
## **3. 찾는 법: 검색 키워드 예시**

  
### **🔍 예시 1: 파일 업로드 API 만들고 싶을 때**

  

> **🔍 검색어:** gin upload file example site:github.com

  

- Gin 공식 문서엔 설명 부족함
    
- 하지만 GitHub나 Medium, velog 등에서 c.FormFile() 사용하는 예제 찾기 쉬움
    

  

### **🔍 예시 2: Excel 파싱해서 DB 저장**

  

> **🔍 검색어:** golang excelize insert into gorm

  

- xuri/excelize는 row 읽는 법만 알려줌
    
- GORM을 같이 쓰는 예제는 구글링이 필요


| **계** | **내용**     | **참고**                                                                         |
| ----- | ---------- | ------------------------------------------------------------------------------ |
| 1단계   | Gin 기초 API | [https://github.com/gin-gonic/examples](https://github.com/gin-gonic/examples) |
| 2단계   | GORM 기본    | [https://gorm.io/docs/](https://gorm.io/docs/)                                 |
| 3단계   | Excelize   | [https://xuri.me/excelize/](https://xuri.me/excelize/)                         |
| 4단계   | 실전 프로젝트    | GitHub에서 go gin gorm example 검색                                                |

| **기능**                | **설명**                |
| --------------------- | --------------------- |
| c.Param("id")         | URL 경로 파라미터 받는 법      |
| c.Query("date")       | 쿼리스트링 받는 법            |
| c.BindJSON(&obj)      | POST된 JSON 파싱         |
| c.FormFile("file")    | 파일 업로드 받기             |
| go run main.go vs air | 개발 자동 리로딩 (air 사용 권장) |
![[Pasted image 20250506181318.png]] 

뭐 이런 구조를 사용한다. 