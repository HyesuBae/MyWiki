#JPQL (Java Persistence Query Language)

JPA는 테이블이 아닌 엔티티 객체를 중심으로 데이터를 검색해야함.   
테이블이 아닌 엔티티 객체를 대상으로 검색하려면 DB의 모든 데이터를 앱으로 불러와서 엔티티 객체로 변경한 다음 검색해야 한다. 이는 사실상 불가능함. 결국 필요한 데이터만 DB에서 앱으로 불러오려면 검색 조건이 포함된 SQL을 사용해야 한다.    
JPA는 JPQL이라는 쿼리 언어로 이 문제를 해결함.

## JPQL과 SQL의 차이

JPQ은 엔티티 객체를 대상으로 쿼리한다. 즉 클래스와 필드를 대상으로 쿼리.    
SQL은 데이터베이스 테이블을 대상으로 쿼리.

````java
List<Member> members = entityManager.createQuery("select m from Member m", Member.class).getResultList();
````

여기에서 "select m from Member m"이 JPQL. (대소문자를 구별함)    
여기서 Member는 Member 엔티티 객체를 말하는 것이지 MEMBER 테이블이 아니다.    
JPQL은 데이터베이스 테이블을 전혀 알지 못한다.    
    
    
JPA는 JPQL을 분석해서 다음과 같은 적절한 SQL을 만들어서 DB에서 데이터를 조회한다.
> SELECT M.ID, M.NAME, M.AGE FROM MEMBER M
    
    

Ref: 자바 ORM 표준 JPA 프로그래밍(김영한)
