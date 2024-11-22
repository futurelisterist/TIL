# PIVOT

- 행을 열로 변환하는 기능
- 오라클 11g부터 PIVOT 기능 제공

## PIVOT의 기본 구조
```ruby
SELECT * FROM (
    원본 데이터
)
PIVOT (
    집계함수(집계 대상 컬럼) ex.MAX, SUM
    FOR 피벗 컬럼
    IN (피벗 대상 값들) == 피벗 칼럼 값
)
```

### 구성 요소 설명
- 원본 데이터: PIVOT을 적용할 테이블 또는 서브쿼리
- 집계 함수: 피벗할 데이터를 집계하는 함수 (예: SUM, MAX, COUNT 등)
- 피벗 컬럼: 행 데이터를 열로 변환할 기준이 되는 컬럼
- 피벗 대상 값들: 열로 변환될 값들을 명시

## 예시
```ruby
-- 판매 데이터에서 상품별, 월별 판매량
CREATE TABLE sales (
    product VARCHAR2(50),
    month VARCHAR2(10),
    amount NUMBER
);


-- 데이터 입력
INSERT ALL
    INTO sales (product, month, amount) VALUES ('Product A', 'Jan', 100)
    INTO sales (product, month, amount) VALUES ('Product A', 'Jan', 200)
    INTO sales (product, month, amount) VALUES ('Product A', 'Feb', 200)
    INTO sales (product, month, amount) VALUES ('Product A', 'Mar', 150)
    INTO sales (product, month, amount) VALUES ('Product A', 'Apr', 300)
    INTO sales (product, month, amount) VALUES ('Product B', 'Jan', 120)
    INTO sales (product, month, amount) VALUES ('Product B', 'Feb', 250)
    INTO sales (product, month, amount) VALUES ('Product B', 'Mar', 180)
    INTO sales (product, month, amount) VALUES ('Product B', 'Apr', 350)
    INTO sales (product, month, amount) VALUES ('Product C', 'Jan', 90)
    INTO sales (product, month, amount) VALUES ('Product C', 'Feb', 110)
    INTO sales (product, month, amount) VALUES ('Product C', 'Mar', 130)
    INTO sales (product, month, amount) VALUES ('Product C', 'Apr', 160)
SELECT * FROM DUAL;


-- PIVOT으로 변환
SELECT * FROM (
    SELECT product, month, amount 
    FROM sales
)
PIVOT (
    SUM(amount)
    FOR month 
    IN ('Jan', 'Feb', 'Mar', 'Apr')
)
```