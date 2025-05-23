# 💥JPA vs MyBatis

## JPA (ORM)
ORM 기술로, 객체와 관계형 데이터베이스 간의 매핑을 담당. JPA를 사용하면 SQL을 작성할 필요 없이, 객체 지향적인 방식으로 데이터베이스와 상호작용

## MyBatis (SQL Mapper)
SQL Mapper로, 개발자가 SQL을 직접 작성하여 매핑하는 방식의 데이터베이스 연동 기술

## JPA vs MyBatis

|          | JPA                            | MyBatis                       |
| :------: | :----------------------------- | :---------------------------- |
| SQL 작성 | 자동 작성                      | 직접 작성                     |
| SQL 관리 | 추상화되어 관리됨(높은 추상화) | SQL이 직접 노출됨             |
|   성능   | 성능 최적화가 어려울 수 있음   | 성능 최적화가 가능하고 효율적 |
| 유지보수 | 테이블 변경 시, 수정이 적음    | SQL을 직접 수정해야 됨        |