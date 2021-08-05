# CREATE 문

## 데이터베이스 생성

```sql
CREATE DATABASE 데이터베이스이름
```

### 데이터베이스 사용

```sql
USE 데이터베이스이름
```

## 테이블 생성

```sql
CREATE TABLE 테이블이름
(
    필드이름1 필드타입1,
    필드이름2 필드타입2,
    ...
)
```

## 제약 조건 (constraint)

데이터의 무결성을 지키기 위해 데이터를 입력받을 때 실행되는 검사 규칙

### NOT NULL

해당 필드는 NULL 값을 저장할 수 없게 된다

### UNIQUE

해당 필드는 서로 다른 값을 가져야만 한다

### PRIMARY KEY

해당 필드가 NOT NULL과 UNIQUE 제약 조건의 특징을 모두 가지게 된다

### FOREIGN KEY

하나의 테이블을 다른 테이블에 의존하게 만든다

### DEFAULT

해당 필드의 기본값을 설정한다