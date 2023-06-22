# Springboot-learn
Spring-boot Study

방문 횟수 조회 서비스
- 환영 인사와 몇 번째 방문인지를 알려주는 간단 웹 애플리케이션


기능목록
- http://localhost:8080/hello 요청 시 HelloWorld 문구를 출력
- http://localhost:8080/hello?name={user} 요청 시 Hello {user} n번째 방문입니다 문구 출력


/hello 요청 후 응답
http://localhost:8080/hello 요청 시 HelloWorld 문구를 출력하는 부분 구현
HelloController.java 파일을 생성하여 코드를 작성
@RestController을 통해 요청을 처리할 클래스임을 지정
@GetMapping("/hello")을 통해 /hello 요청을 처리할 메서드를 지정


테이블 정의
요청 이력을 저장할 테이블의 스키마 정의
resources/schema.sql

create table hello(
    id bigint auto_increment,
    name varchar(255) not null,
    primary key(id)
);


Dao 작성
쿼리를 메서드에 매핑하여 메서드를 통해 DB에 접근


Controller에서 Dao 사용하기
HelloDao 객체를 개발자가 직접 생성하지 않고 스프링 컨테이너로 관리하기 위해 HelloController에 HelloDao 의존을 주입
의존성 주입은 생성자 주입 방법을 추천


컨트롤러 기능 수정
name 값이 없으면 그냥 HelloWorld를 화면에 표시
name 값이 있으면 몇번째 방문인지 알려줌
