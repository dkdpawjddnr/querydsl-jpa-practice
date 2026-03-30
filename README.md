실전! Querydsl 학습 프로젝트
Type-Safe한 쿼리 작성부터 실무 최적화까지 인프런 김영한 님의 [실전! Querydsl] 강의를 수강하며, JPQL의 한계를 극복하고 객체지향적인 쿼리 작성 능력을 배양한 프로젝트입니다.

🏗 프로젝트 구조 (Repository Pattern)

Querydsl을 실무에서 사용할 때 가장 권장되는 사용자 정의 리포지토리 구조를 구현했습니다.

MemberRepository: JpaRepository를 상속받아 기본 CRUD 기능을 제공합니다.

MemberRepositoryCustom: Querydsl로 작성할 추상 메서드를 정의합니다.

MemberRepositoryImpl: JPAQueryFactory를 사용하여 실제 복잡한 동적 쿼리를 구현합니다.

🛠️ 핵심 사용 기술

Framework: Spring Boot 3.2.0

Data Access: Spring Data JPA, Querydsl-JPA

Database: H2 (In-memory)

Library: Querydsl-Apt, Lombok, JUnit5, AssertJ

🏗️ 엔티티 설계 (Entity Design)

프로젝트의 핵심 도메인 모델입니다. 양방향 연관관계와 지연 로딩을 고려하여 설계했습니다.

Member: 이름(username), 나이(age), 팀(Team) 정보를 가짐.

Team: 팀명(name), 소속 회원들(List<Member>)을 가짐.

연관관계 전략: @ManyToOne(fetch = FetchType.LAZY)를 통해 불필요한 조인을 방지하고 성능을 최적화했습니다.

🔥 핵심 해결 과제

1. JPQL vs Querydsl
JPQL: 문자열 기반으로 오타 발생 시 런타임에 에러가 발생함.

Querydsl: 자바 코드로 쿼리를 작성하여 컴파일 시점에 문법 오류를 발견하고, IDE의 자동 완성 기능을 100% 활용함.

2. 동적 쿼리 해결 (Dynamic Query)
가장 강력한 기능인 동적 쿼리를 두 가지 방식으로 구현해 보았습니다.

BooleanBuilder 활용

Where 다중 파라미터 사용 (추천): 가독성이 높고 메서드 재사용이 가능함.

3. 성능 최적화 (Projection & Paging)
Projection: 필요한 필드만 선택해서 조회하여 네트워크 부하를 줄임 (@QueryProjection 활용).

Paging: Spring Data JPA의 Pageable과 Querydsl을 연동하고, 카운트 쿼리 최적화(countQuery)를 적용했습니다.
