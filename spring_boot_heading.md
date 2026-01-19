# 4. REST API


### API란?
- Application Programming Interface
- 내부 구현 로직을 알지 못해도 정의되어 있는 기능을 쉽게 사용할 수 있음
- API 명세서


### REST란?
- Representational State Transfer
- 자원의 이름으로 구분하여 해당 자원의 상태를 교환하는 것을 의미
- 서버와 클라이언트의 통신 방식 중 하나임
- HTTP URL를 통해 자원을 명시하고 HTTP Method를 통해 자원을 교환함
- HTTP Method(CRUD): Create / Read / Update / Delete


### REST 특징
- Server-Client 구조
  - 자원이 있는 쪽이 Server, 요청하는 쪽이 Client
  - 클라이언트와 서버가 독립적으로 분리되어 있어야 함

- Stateless
  - 요청 간에 클라이언트 정보가 서버에 저장되지 않음
  - 서버는 각각의 요청을 완전히 별개의 것으로 인식하고 처리

- Cacheable
  - HTTP 프로토콜을 그대로 사용하기 때문에 HTTP의 특징인 캐싱 기능을 적용
  - 대량의 요청을 효율적으로 처리하기 위해 캐시를 사용

- 계층화(Layered System)
  - 클라이언트는 서버의 구성과 상관 없이 REST API 서버로 요청
  - 서버는 다중 계층으로 구성될 수 있음(로드밸런싱, 보안 요소, 캐시 등)

- Code on Demand(Optional)
  - 요청을 받으면 서버에서 클라이언트로 코드 또는 스크립트(로직)을 전달하여 클라이언트 기능 확장

- 인터페이스 일관성(Uniform Interface)
  - 정보가 표준 형식으로 전송되기 위해 구성 요소간 통합 인터페이스를 제공
  - HTTP 프로토콜을 따르는 모든 플랫폼에서 사용 가능하게끔 설계


### REST의 장점
- HTTP 표준 프로토콜을 사용하는 모든 플랫폼에서 호환 가능
- 서버와 클라이언트의 역할을 명확하게 분리
- 여러 서비스 설계에서 생길 수 있는 문제를 최소화


### REST API 특징
- REST 기반으로 시스템을 분산하여 확장성과 재사용성을 높임
- HTTP 표준을 따르고 있어 여러 프로그래밍 언어로 구현할 수 있음


### REST API 설계 규칙
- URL을 통해 자원을 표현해야함
- 자원에 대한 조작은 HEADER를 통해 표현해야 함
- 메세지를 통한 리소스 조작 content-type (HTML / XML / JSON)
- URL에는 소문자를 사용
- Resource의 이름이나 URL이 길어질 경우 -을 통해 가독성을 높일 수 있음
- _는 사용하지 않음
- 파일 확장자를 표현하지 않음



---
# 5. pom.xml 설정하기


### pom.xml
- Maven 프로젝트를 생성하면 루트 디렉토리에 생성되는 파일
- Project Object Model 정보를 담고 있음
- 주요 설정 정보
  - 프로젝트 정보: 프로젝트 이름, 개발자 목록, 라이센스 등
  - 빌드 설정 정보: 소스, 리소스, 라이프 사이클 등 실행할 플러그인 등
  - POM 연관 정보: 의존 프로젝트(모듈), 상위 프로젝트, 하위 모듈 등


### 프로젝트 기본 정보
- <name>: 프로젝트 명
- <url>: 프로젝트 사이트 URL
- <description>: 프로젝트에 대한 간단한 설명
- <organization>: 프로젝트를 관리하는 단체 설명


### 프로젝트 연관 정보
- <groupId>: 프로젝트의 그룹 ID 설정
- <artifactId>: 프로젝트 아티팩트 ID 설정
- <version>: 프로젝트 버전
- <packaging>: 패키징 타입 설정
  - jar: 자바 프로젝트 압출 파일
  - war: 웹 어플리케이션을 위한 패키징 방식


### 프로젝트 의존 설정
- <dependencies>: 라이브러리 의존성 정보를 가지고 있는 dependency 태그를 묶은 태그
- <dependency>: 각 라이브러리의 정보를 담는 태그
- <groupId>: 의존성 라이브러리의 group ID
- <artifactId>: 의존성 라이브러리의 아티팩트 ID
- <version>: 의존성 라이브러리의 버전
- <scope>: 해당 라이브러리의 이용 범위를 지정
  - compile (default)
  - provided: 배포 시에는 빠짐
  - runtime: 컴파일 시에는 사용하지 않고, 실행 상황에서만 사용됨
  - test: 테스트 사용에서만 사용되는 라이브러리
  - system: provide와 유사하지만 직접 관리하는 JAR를 추가
  
- <optional>: 다른 프로젝트에서 이 프로젝트를 의존성 설정을 할 경우 사용할지 결정



---
# 6. MVC 패턴


### MVC(Model View Controller)
- 디자인 패턴 중 하나인 MVC 패턴은 어플리케이션을 구성할 때 세가지 역할로 구분한 패턴을 의미
- 사용자 인터페이스로부터 비즈니스 로직을 분리하여 서로 영향 없이 쉽게 고칠 수 있는 설계가 가능
- View <-> Controller -> Model -> View


### Controller
- Model과 View 사이에서 브릿지 역할을 수행
- 앱의 사용자로부터 입력에 대한 응답으로 모델 및 뷰를 업데이트하는 로직을 포함
- 사용자의 요청은 모두 컨트롤러를 통해 진행되어야함
- 컨트롤러로 들어온 요청은 어떻게 처리할지 결정하여 모델로 요청을 전달함
- ex. 상품 검색 시, 키워드를 컨트롤러가 받아 모델과 뷰에 적절하게 입력을 처리하여 전달함
         

### Model
- 데이터를 처리하는 영역
- 데이터베이스와 연동을 위한 DAO(Data Access Object)와 데이터 구조를 표현하는 DO(Data Object)로 구성됨
- ex. 검색을 위한 키워드가 넘어오면 데이터베이스에서 관련된 상품의 데이터를 받아 뷰에 전달


### View
- 데이터를 보여주는 화면 자체의 영역을 뜻함
- 사용자 인터페이스 요소들이 여기에 포함되며, 데이터를 각 요소에 배치함
- 뷰에서는 별도의 데이터를 보관하지 않음
- ex. 검색 결과를 보여주기 위해 모델에서 결과 상품 리스트 데이터를 받음


### MVC 패텅의 특징
- 서로 간의 의존성이 낮아짐
- 분업 및 협업이 원활해짐
- 한 영역을 업데이트 하더라도 다른 곳에 영향을 주지 않음

- 단점: 기능이 많아질수록 컨트롤러의 역할이 너무 많아짐
  - 이것을 분담해주어야함: MVVM / MVP 모델 등등



---
# 7. Hello World 응답하기


### @RestController
- Spring Framework 4 버전부터 사용가능한 어노테이션
- @Controller + @ResponseBody가 결합된 어노테이션
- 컨트롤러 클래스 하위 메소드에 @ResponseBody 어노테이션을 붙이지 않아도 문자열과 JSON 등을 전송할 수 있음
- View를 거치지 않고 HTTP ResponseBody에 직접 Return 값을 담아 보내게 됨


### @RequestMapping
- MVC의 핸들러 매핑을 위해서 DefaultAnnotaionMapping을 사용
- DefaultAnnotationHandlerMapping 매핑 정보로 @RequestMapping 어노테이션을 활용
- 클래스와 메소드의 RequestMapping을 통해 URL을 매핑하여 경로를 설정하여 해당 메소드에서 처리
  - value: url 설정
  - method: GET, POST, DELETE, PUT, PATCH 등

- 스프링 4.3버전 부터 메소드를 지정하는 방식보다 간단하게 사용할 수 있는 어노테이션을 사용할 수 있음
  - @GetMapping
  - @PostMapping
  - @DeleteMapping
  - @PutMapping
  - @PatchMapping



---
# 8. GET API


### @RequestMapping
- value와 method로 정의하여 API를 개발하는 방식
- 이제는 고전적인 방법으로 사용하지 않음
```java
@RequestMapping(value="/hello", method=RequestMethod.GET)
public String getHello() {
    return "Hello World";
}
```


### @GetMapping
- 별도의 파라미터 없이 GET API를 호출하는 경우 사용되는 방법
```java
@GetMapping(value="/name")
public String getName() {
    return "Flature";
}
```


### @PathVariable
- GET 형식의 요청에서 파라미터를 전달하기 위해 URL에 값을 담아 요청하는 방법
- 아래 방식은 @GetMapping에서 사용된 {변수}의 이름과 메소드의 매개변수와 일치시켜야함
```java
@GetMapping(value="/variable1/{variable}")
public String getVariable1(@PathVariable String variable) {
    return variable;
}
```

- {변수}의 이름과 메소드의 매개변수를 일치시켜줄 수 없는 경우
```java
@GetMapping(value="/variable1/{variable}")
public String getVariable1(@PathVariable("varibale") String var) {
    return var;
}
```


### @RequestParam
- GET 형식의 요청에서 쿼리 문자열을 전달하기 위해 사용되는 방법
- '?'를 기준으로 우측에 {키}={값}의 형태로 전달되며, 복수 형태로 전달할 경우 &를 사용함
- /request1?name=flature&email=thinkground@gmail.com&organization=thinkground
```java
@GetMapping(value="/request1")
public String getRequestParam1(
    @RequestParam String name,
    @RequestParam String email,
    @RequestParam String organization
) {
    return name + " " + email + "" + organization;
}
```

- 어떤 요청 값이 들어올지 모를 경우 사용하는 방식
```java
@GetMapping(value="/request2")
public String getRequestParam2(@RequestParam Map<String, String> param) {
    StringBuilder sb = new StringBuilder();

    param.entrySet().forEach(map -> {
        sb.append(map.getKey() + ":" + map.getValue() + "\n");
    });

    return sb.toString();
}
```


### Path vs Request 사용처
- Path는 어떤 데이터인가를 정의할 때 적합
    - /book/123 -> 123번이라는 식별자를 가진 책

- Request: 어떻게 데이터를 보여줄 것인가에 적합
    - 책 목록 중에 소설 장르만, 최신순으로


### DTO 사용
- GET 형식의 요청에서 쿼리 문자열을 전달하기 위해 사용되는 방법
- key와 value가 정해져있지만, 받아야할 파라미터가 많을 경우 DTO 객체를 사용한 방식
- getter / setter가 반드시 있어야함 (필드 접근 제어자 상관없이!!)
- private - getter/setter가 구조를 많이 사용함
```java
@GetMapping(value="/request3")
public String getRequestParam3(MemberDTO memberDTO) {
    // return memberDTO.getName() + " " + memberDTO.getEmail() + " " + memberDTO.getOrganization();
    return memberDTO.toString();
}

public class MemberDTO {
    @BindParam("name") 
    private String user_name; // ?key=value의 key와 변수명을 일치시킬 수 없는 경우
    private String email;
    private String organization;

    // ... Getter / Setter
}
```



---
# 9. MariaDB 설치



---
# 10. POST API


### POST API
- 리소스를 추가하기 위해 사용되는 API
- @PostMapping: POST API를 제작하기 위해 사용되는 어노테이션(Annotation)
  - @RequestMapping + POST Method의 조합

- 일반적으로 추가하고자 하는 리소스를 http body에 추가하여 서버에 요청
- 그렇기 때문에 @RequestBody를 이용하여 body에 담겨있는 값을 받아야함
```java
@PostMapping(value="/member")
public String postMember(@RequestBody Map<String, Object> posData) {
  StringBuilder sb = new StringBuilder();

  postData.entrySet().forEach(map -> {
    sb.append(map.getKey() + " : " + map.getValue() + "\n");
  });

  return sb.toString();
}
```


### DTO 사용
- key와 value가 정해져있지만, 받아야할 파라미터가 많을 경우 DTO 객체를 사용한 방식
- @RequestBody를 반드시 붙여줘야함
```java
@PostMapping(value="/member2")
public String postMemberDto(@RequestBody MemberDTO memberDTO) {
  return memberDTO.toString();
}
```


### @RequestBody
- content-type: application/json
- Jackson 라이브러리가 처리함 - Getter가 있어야함
- HTTP 요청시 Body는 단 한 번만 읽음 / 한나의 컨트롤러 메서드에서 @RequestBody는 단 한 번만 사용할 수 있음
- vs @ModelAttribute
  - Query String 또는 Form Data
  - 주로 GET / POST(Form)


### 스프링 프레임워크의 기본 인자 처리 규칙
- 컨트롤러의 파라미터에 어노테이션이 없을 때, 내부적으로 다음과 같은 규칙에 따라 타입을 판단함
  - 생략 가능 규칙
    - String, int, long, boolean, Date: @RequestParam
    - 사용자가 정의한 MemberDTO, List, Map: @ModelAttribute
      - 근데 Map 같은 경우 아무 어노테이션도 안 붙이면 이를 @ModelAttribute로 취급하려고 함
      - DTO처럼 필드가 정해진게 아니여서 못 담을 수도 있음
      - @RequestParam을 붙여주는 것이 좋음



---
# 11. Swagger


### Swagger
- 협업을 위해 필요한 라이브러리
  - 클라이언트 개발자 A <- API 소개: 출금 API를 만들었으니 참고하세요 -> 서버 개발자 B
  - 엑셀 워드로 API 스펙을 작성해서 보내주었음
  - 만약 수정되면 이걸 다시 만들어서 보내서 주기가 쉽지 않음 => Swagger 라이브러리


### Swagger란?
- 서버로 요청되는 API 리스트를 HTML 화면으로 문서화하여 테스트 할 수 있는 라이브러리
- 서버가 가동되면서 @RestController를 읽어 API를 분석하여 HTML 문서를 작성함
- 이 강의에서는 2.9.2 버전을 사용할 예정


### Swagger가 필요한 이유
- REST API의 스펙을 문서화 하는 것은 매우 중요
- API를 변경할 때마다 Reference 문서를 계속 바꿔야하는 불편함이 있음


### Swagger 설정 방법
- @Configuration: 
  - 어노테이션 기반의 환경 구성을 돕는 어노테이션
  - IoC Container에게 해당 클래스를 Bean 구성 Class 임을 알려줌

- @Bean
  - 개발자가 직접 제어가 불가능한 외부 라이브러리 등을 Bean으로 만들 경우에 사용


### 실제 설정
```java
// root/config/SwaggerConfiguration.java
package studio.thinkground.testproject.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

import springfox.documentation.builders.ApiInfoBuilder;
import springfox.documentation.builders.PathSelectors;
import springfox.documentation.builders.RequestHandlerSelectors;
import springfox.documentation.service.ApiInfo;
import springfox.documentation.spi.DocumentationType;
import springfox.documentation.spring.web.plugins.Docket;
import springfox.documentation.swagger2.annotations.EnableSwagger2;

@Configuration
@EnableSwagger2
public class SwaggerConfiguration {
    
    @Bean
    public Docket api() {
        return new Docket(DocumentationType.SWAGGER_2)
            .apiInfo(apiInfo())
            .select()
            .apis(RequestHandlerSelectors.basePackage("studio.thinkground.testproject")) // 스캔 범위
            .paths(PathSelectors.any())
            .build(); // 이걸 해주어야 적용됨
    }

    private ApiInfo apiInfo() {
        return new ApiInfoBuilder()
            .title("Around Hub Open API Test with Swagger")
            .description("설명 부분")
            .version("1.0.0")
            .build(); // 이걸 해주어야 적용됨
    }
    
}
```


### Swagger 확인
- root_address/swagger-ui.html


### Spring Boot 3.x OpenAPI Swagger 사용법 (최신 버전 적용)
```xml
// pom.xml
<dependency>
  <groupId>org.springdoc</groupId>
  <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
  <version>2.3.0</version>
</dependency>
```

```java
// root/config/SwaggerConfiguration.java
package studio.thinkground.testproject.config;

import io.swagger.v3.oas.models.OpenAPI;
import io.swagger.v3.oas.models.info.Info;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class SwaggerConfiguration {

    @Bean
    public OpenAPI openAPI() {
        return new OpenAPI()
                .info(new Info()
                        .title("Around Hub Open API Test")
                        .description("Spring Boot 3.x 환경에서의 Swagger 테스트")
                        .version("1.0"));
    }
    
}
```



---
# 12. PUT API / DELETE API


### PUT API
- 해당 리소스가 존재하면 **갱신**하고, 리소스가 없을 경우에는 새로 생성해주는 API
- 업데이트를 위한 메소드
- 기본적인 동작 방식은 POST API와 동일
  - POST API는 완전히 새로 만들어버림


### POST vs PUT
- 리소스 생성 vs 리소스 업데이트 또는 생성
- 호출할 때마다 결과가 달라짐 vs 여러 번 호출해도 결과가 같음
- 서버가 URL을 결정(/members) vs 클라이언트가 결정(/members/1)
- 새로운 데이터를 추가해줘 vs 이 경로에 데이터를 이걸러 바꿔줘


### PUT vs PATCH
- PUT: 리소스의 전체를 교체함 (보내지 않은 필드는 NULL이 될 수도 있음)
- PATCH: 리소스의 일부만 수정함 (이름만 바꾸고 싶을 때 사용)


### DELETE API
- 서버를 통해 리소스를 사제 하기 위해 사용되는 API
- 일반적으로 @PathVariable을 통해 리소스 ID 등을 받아 처리


### ResponseEntity
- Spring Framework에서 제공하는 클래스 중 HttpEntity라는 클래스를 상속받아 사용하는 클래스
- 사용자의 HttpRequest에 대한 응답 데이터를 포함
- 포함하는 클래스
  - HttpStatus
  - HttpHeaders
  - HttpBody


### 예제
- controller/PutController.java
- controller/DeleteController.java


### ResponseEntity
```java
@PutMapping(value="/member3")
    public ResponseEntity<MemberDTO> postMemberDto3(@RequestBody MemberDTO memberDTO) {
        return ResponseEntity.status(HttpStatus.ACCEPTED).body(memberDTO);
    }
```
- ResponseEntity
  - status(HttpStatus.ACCEPTED): HTTP Status 202: 비동기 작업(요청은 받았으나 처리는 나중에 됨)
    - 이거 들어가서 보면 몇 번에고 뭐가 있는지 볼 수 있음
    - HttpStatus.class
  - body(memberDTO): response body에 담길 값


### 주의할점
- HTTP Method는 결국 약속일 뿐
- 내부 코드를 이상하게 짜면 안됨
  - HTTP Method를 보고 그 약속에 맞게 내부 로직을 작성해야함
  - POST인데 멱등성을 보장하면 안되고, PUT인데 멱등성을 보장하지 않으면 안됨
  - 멱등성: 어떤 연산을 여러 번 반복해도 처음 한 번 적용했을 때와 동일하게 유지되는 성질


### POST vs PUT vs PATCH
- POST: 새로운 리소스를 생성 멱등성 X
- PUT: 해당 리소스를 통째로 교체 없으면 새로 생성 멱등성 O
- PATCH: 해당 리소스 부분 업데이트 멱등성 O



---
# 13. Lombok



### Lombok이란?
- 반복되는 메소드를 Annotaion을 사용하여 자동으로 작성해주는 라이브러리
- 일반적으로 VO, DTO, Model, Entity 등 데이터 클래스에서 주로 사용됨
- 대표적으로 많이 사용되는 Annotaion
  - @Getter
  - @Setter
  - @NoArgConstructor
  - @AllArgConstructor
  - @Data
  - @ToString


### Lombok 라이브러 의존성 설정
```xml
<dependency>
  <groupId>org.projectlombok</groupId>
  <artifactId>lombok</artifactId>
  <optional>true</optional>
</dependency>
```


### @Getter / @Setter
- 해당 클래스에 선언되어 있는 필드를 기반으로 getField, setField와 같은 식으로 자동으로 메소드를 생성
```java
@Getter
@Setter
public class MemberDTO {
  private String name;
  private String email;
  private String organization;
}
```


### @NoArgsContructor / @AllArgsConstructor / @RequiredArgsConstructor
- @NoArgsContructor: 파라미터가 없는 생성자를 생성
- @AllArgsConstructor: 모든 필드값을 파라미터로 갖는 생성자를 생성
- @RequiredArgsConstructor: 필드값 중 final이나 @NotNull인 값을 같는 생성자를 생성
```java
@NoArgsConstructor
@RequiredArgsConstructor
@AllArgsConstructor
public class MemberDTO {
  private String name;
  private String email;
  private String organization;
}
```


### @ToSTring
- toString 메소드를 자동으로 생성해주는 기능
- @ToString 어노테이션에 exclude 속성을 사용하여 특정 필드를 toString에서 제외시킬 수 있음
```java
@ToString
public class MemberDTO {
  private String name;
  private String email;
  private String organization;
}


@ToString(exclude="email")
public class MemberDTO {
  private String name;
  private String email;
  private String organization;
}

@Override
public String toString() {
  return this.name + " " + this.email + " " + this.organization;
}
```
- "MemberDTO(id=" + this.id + ", name=" + this.name + ", email=" + this.email + ")" 이 형식으로 작성됨


### @EqualsAndHashCode
- equals, hashCode 메소드를 자동으로 생성
- equals: 두 객체가 내용이 같은지 동등성(equality)을 비교하는 연산자
- hashCode: 두 객체가 완전히 같은 객체인지 동일성(identity)를 비교하는 연산자
- callSuper 속성을 통해 메소드 생성시 부모 클래스의 필드까지 고려할지 여부 설정 가능
  - callSuper = true => 부모 클래스 필드 값들도 동일한지 체크!!!


### @Data
- 해당 어노테이션을 사용하면, 앞서 나온 기능들을 한 번에 추가해줌
  - @Getter
  - @Setter
  - @RequiredArgsConstructor
  - @ToString
  - @EqualsAndHashCode
  - ...
  - 불필요한 메소드가 추가될 수 있어서 기피하려는 경향이 있음


### 주의할점
- Lombok을 추가함으로써 특정 기능에 영향을 주는 경우가 있음!!!
- PM 등의 성향에 따라 다름
- 정답은 아님


### Delombok
- 어노테이션을 없애고 해당 기능을 코드로 작성해주는 기능
- Refactor/delombok


### @Builder
- 생성자 파라미터가 많아질 때, 어떤 값이 어떤 필드인지 헷갈리는 것을 방지(Builder Pattern)
- MemberDTO.builder().name("홍길동").email("test@gmail.com").build();


---
# 14. Entity, DAO, Repository, DTO (데이터베이스 적용하기)


### Spring Boot 서비스 구조
- Client <- DTO -> Controller <- DTO -> Service <- Entity -> DAO(Repository) <- Entity -> DB
- DTO를 받아서 내용을 추가 혹은 삭제해서 Entity라는 객체를 만듦
- Repository(DAO)에서 Entity를 가지고 통신함
- 이후 DTO를 통해 Client - Controller - Service간에 통신

- Service / DAO(Repository)
  - 이 두 개는 인터페이스로 구현함
  - 상속받은 Impl가 실제 로직을 갖게됨


### Entity(Domain)
- 데이터베이스에 쓰일 컬럼과 여러 엔티티 간의 연관관계를 정의
- 데이터베이스의 테이블을 하나의 엔티티로 생각해도 무방함
- 실제 데이터베이스의 테이블과 1:1로 매핑됨
- 이 클래스의 필드는 각 테이블 내부의 컬럼을 의미


### Repository
- Entity에 의해 생성된 데이터베이스에 접근하는 메소드를 사용하기 위한 인터페이스
- Service와 DB를 연결하는 고리의 역할을 수행
- 데이터베이스에 적용하고자하는 CRUD를 정의하는 영역


### DAO(Data Access Object)
- 데이터베이스에 접근하는 객체를 의미(Persistance Layer)
- Service가 DB에 연결할 수 있게 해주는 역할
- DB를 사용하여 데이터를 조회하거나 조작하는 기능을 전담
- Repository의 메소드를 가지고 활용함


### DTO(Data Transfer Object)
- DTO는 VO(Value Object)로 불리기도 하며, 계층간 데이터 교환을 위한 객체를 의미
- VO의 경우 **Read Only**의 개념을 가지고 있음
- Entity는 DB와 동일하게 만들어져있는 클래스르 의미
- DTO는 Entity랑 같은 필드값만을 가지고 있을 수도 있지만, 없거나 추가된 사항을 가지고 있을 수도 있음
- 엄밀히 말하면 DTO는 전송용 / VO는 값 자체를 표현하는 용(불변성)


### Spring Boot Data JPA
- 의존성 추가
```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
```
- @Entity
- @Table(name = "product"): 테이블을 자동으로 생성해줄 때 테이블 이름
- @Id


### 이번 강의에서는 알려주지 않은 설정이 많음
- 이런 것도 필요한 법!! 오히려 좋아!! 해보자!!


### 설정
- MARIADB 데이터베이스 aronud_hub_shop 만들기

- pom.xml 의존성 추가
```xml
<dependency>
  <groupId>org.mariadb.jdbc</groupId>
  <artifactId>mariadb-java-client</artifactId>
</dependency>
```

- application.properties 설정
```
# MariaDB 연결 설정
spring.datasource.driver-class-name=org.mariadb.jdbc.Driver
# localhost:3306 뒤의 'shop'은 미리 생성한 데이터베이스(Schema) 이름이어야 합니다.
spring.datasource.url=jdbc:mariadb://localhost:3306/around_hub_shop
spring.datasource.username=root
spring.datasource.password=비밀번호

# JPA/Hibernate 설정
spring.jpa.show-sql=true
spring.jpa.hibernate.ddl-auto=update // 이 설정이 있으면 엔티티 클래스와 DB 테이블을 비교 후 없으면 만들고, 변경된 부분이 있으면 추가해줌
# MariaDB에 최적화된 SQL을 생성하기 위한 Dialect 설정
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MariaDB103Dialect
```

- ProductController 만들기
  - 이건 다음 강의에서 함



--- 
# 15. ORM, JPA, Spring Data JPA 적용하기


### ORM이란?
- Object Relational Mapping
- 어플리케이션의 객체와 관계형 데이터베이스를 자동으로 매핑해주는 것을 의미
  - Java의 데이터 클래스와 관계형 데이터베이스의 테이블을 매핑
- 객체지향 프로그래밍과 관계형 데이터베이스의 차이로 발생하는 제약사항을 해결해주는 역할을 수행
- 대표적으로 JPA, Hibernate 등이 있음 (PErsistent API)

- Spring Boot Application
  - String name
  - String email
  - String organization

- ORM Mapping

- Database
  - name
  - email
  - organization


### ORM의 장점
- SQL 쿼리가 아닌 직관적인 코드로 데이터를 조작할 수 있음
  - 개발자가 보다 비즈니스 로직에 집중할 수 있음

- 재사용 및 유지보수 편리
  - ORM은 독립적으로 작성되어 있어 재사용 가능
  - 매핑 정보를 명확하게 설계하기 때문에 따로 데이터베이스를 볼 필요가 없음

- DBMS에 대한 종속성이 줄어듬
  - DBMS를 교체하는 작업은 비교적 적은 리스크로 수행 가능


### ORM의 단점
- 복잡성이 커질 경우 ORM만으로 구현하기 어려움
  - 직접 쿼리를 구현하지 않아 복잡한 설계가 어려움

- 잘못 구현할 경우 속도 저하 발생
  - 코드를 쿼리로 변환하는데도 속도 저하가 발생할 수 있음

- 대형 쿼리는 별도의 튜닝이 필요할 수 있음


### JPA란?
- Java Persistance API의 줄임말이며, ORM과 관련된 인터페이스의 모음
- Java 진영에서 표준 ORM으로 채택되어 있음
- ORM이 큰 개념이라고 하면, JAP는 더 구체화 시킨 스펙을 포함하고 있음


### Hibernate
- ORM Framework 중 하나
- JPA의 실제 구현체 중 하나이며, 현재 JPA 구현체 중 가장 많이 사용됨
  - EclipseLink
  - Hibernate
  - DataNucleus


### Spring Data JPA
- Spring Framework에서 JPA를 편리하게 사용할 수 있게 지원하는 라이브러리
  - CRUD 처리용 인터페이스 제공
  - Repository 개발 시 **인터페이스만 작성하면** 구현 객체를 동적으로 생성해서 주입
  - 데이터 접근 계층 개발시 인터페이스만 작성해도 됨

- Hibernate에서 자주 사용되는 기능을 조금 더 쉽게 사용할 수 있게 구현
  - Spring Boot Application - Hibernate(Spring Data JPA) - Database

- 실제 흐름
  - Spring Boot Application -> Spring Data JPA -> JPA -> Hibernate -> JDBC -> DB


### 로직 순서 확인
- Service <- DTO -> DataHandler <- Entity -> DAO <- Entity -> Repository <- Entity -> Database


### AutoWired
- Bean 객체 주입
  - @Service
    - 이게 만약 구현체가 두 개면?
      - 1. @Primary: 이걸 먼저 사용해라 - 구현체에 명시 
      - 2. @Qualifier("subHandler"): 이거 써라 명시 - 구현체/사용체에 명시


### AOP
- 나중에 공부할 AOP에서 특정 어노테이션이 붙은 클래스에만 공통 로직을 적용하게 할 수 있음
- 그리고 @Controller @Service @Repository에는 모두 @Component가 붙어있음



