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
