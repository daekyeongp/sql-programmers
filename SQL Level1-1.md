# 1. 모든 레코드 조회하기 (SELECT)
✅ LEVEL1. [모든 레코드 조회하기](https://programmers.co.kr/learn/courses/30/lessons/59034)

### 문제 요약
1. 테이블 정보
✔ `ANIMAL_INS`: 동물 보호소에 들어온 동물의 정보를 담은 테이블

2. 필드 정보
✔ `ANIMAL_ID`: 동물의 아이디
✔ `ANIMAL_TYPE`: 생물 종
✔ `DATETIME`: 보호 시작일
✔ `INTAKE_CONDITION`: 보호 시작 시 상태
✔ `NAME`: 이름
✔ `SEX_UPON_INTAKE`: 성별 및 중성화 여부

3. 문제
✔ 동물 보호소에 들어온 `모든 동물의 정보`를 `ANIMAL_ID`순으로 조회하는 **SQL문을 작성해주세요.**

4. **작성한 SQL문**
```sql
SELECT * //모든 필드를 출력하라.
FROM ANIMAL_INS //테이블 선택
ORDER BY ANIMAL_ID; //ANIMAL_ID를 기준으로 오름차순으로 정렬하라.
```
> ##### ORDER BY 🧐
👉 `오름차순(ASC)`, `내림차순(DESC)`의 두 가지 기준이 있는데, `default`는 **오름차순이다.**

# 2. 역순 정렬하기 (SELECT)
✅ LEVEL1. [역순 정렬하기](https://programmers.co.kr/learn/courses/30/lessons/59035)

### 문제 요약
1. 테이블 정보
✔ `ANIMAL_INS`: 동물 보호소에 들어온 동물의 정보를 담은 테이블

2. 필드 정보
✔ `ANIMAL_ID`: 동물의 아이디
✔ `ANIMAL_TYPE`: 생물 종
✔ `DATETIME`: 보호 시작일
✔ `INTAKE_CONDITION`: 보호 시작 시 상태
✔ `NAME`: 이름
✔ `SEX_UPON_INTAKE`: 성별 및 중성화 여부

3. 문제
✔ 동물 보호소에 들어온 `모든 동물의 이름`과 `보호 시작일을 조회`하는 `SQL문`을 작성해주세요. 이때 결과는 `ANIMAL_ID 역순`으로 보여주세요.

4. **작성한 SQL문**
```sql
SELECT NAME, DATETIME //NAME, DATETIME 필드 출력
FROM ANIMAL_INS //테이블 선택
ORDER BY ANIMAL_ID DESC; //ANIMAL_ID를 기준으로 내림차순 정렬
```

# 3. 아픈 동물 찾기 (SELECT)
✅ LEVEL1. [아픈 동물 찾기](https://programmers.co.kr/learn/courses/30/lessons/59036)

### 문제 요약
1. 테이블 정보
✔ `ANIMAL_INS`: 동물 보호소에 들어온 동물의 정보를 담은 테이블

2. 필드 정보
✔ `ANIMAL_ID`: 동물의 아이디
✔ `ANIMAL_TYPE`: 생물 종
✔ `DATETIME`: 보호 시작일
✔ `INTAKE_CONDITION`: 보호 시작 시 상태
✔ `NAME`: 이름
✔ `SEX_UPON_INTAKE`: 성별 및 중성화 여부

3. 문제
✔ 동물 보호소에 들어온 **동물 중 아픈 동물**의 `아이디`와 `이름`을 조회하는 `SQL 문`을 작성해주세요. 이때 결과는 `아이디 순으로 조회`해주세요.
👉 아픈 동물은 `INTAKE_CONDITION`이 `Sick` 인 경우를 뜻함

4. **작성한 SQL문**
```sql
SELECT ANIMAL_ID, NAME //ANIMAL_ID, NAME 출력
FROM ANIMAL_INS //테이블 선택
WHERE INTAKE_CONDITION = 'Sick' //INTAKE_CONDITION 값이 Sick인 데이터 선택
ORDER BY ANIMAL_ID; //ANIMAL_ID 기준으로 오름차순 정렬
```

# 4. 어린 동물 찾기 (SELECT)
✅ LEVEL1. [어린 동물 찾기](https://programmers.co.kr/learn/courses/30/lessons/59037)

### 문제 요약
1. 테이블 정보
✔ `ANIMAL_INS`: 동물 보호소에 들어온 동물의 정보를 담은 테이블

2. 필드 정보
✔ `ANIMAL_ID`: 동물의 아이디
✔ `ANIMAL_TYPE`: 생물 종
✔ `DATETIME`: 보호 시작일
✔ `INTAKE_CONDITION`: 보호 시작 시 상태
✔ `NAME`: 이름
✔ `SEX_UPON_INTAKE`: 성별 및 중성화 여부

3. 문제
✔ 동물 보호소에 들어온 **동물 중 젊은 동물**의 `아이디`와 `이름`을 조회하는 `SQL 문`을 작성해주세요. 이때 결과는 `아이디 순으로 조회`해주세요.
👉 젊은 동물은 `INTAKE_CONDITION`이 `Aged`가 아닌 경우를 뜻함

4. **작성한 SQL문**
```sql
SELECT ANIMAL_ID, NAME //ANIMAL_ID, NAME 출력
FROM ANIMAL_INS //테이블 선택
WHERE INTAKE_CONDITION != 'Aged' //INTAKE_CONDITION 값이 Aged가 아닌 데이터 선택
ORDER BY ANIMAL_ID; //ANIMAL_ID 기준으로 오름차순 정렬
```

# 5. 동물의 아이디와 이름 (SELECT)
✅ LEVEL1. [동물의 아이디와 이름](https://programmers.co.kr/learn/courses/30/lessons/59403)

### 문제 요약
1. 테이블 정보
✔ `ANIMAL_INS`: 동물 보호소에 들어온 동물의 정보를 담은 테이블

2. 필드 정보
✔ `ANIMAL_ID`: 동물의 아이디
✔ `ANIMAL_TYPE`: 생물 종
✔ `DATETIME`: 보호 시작일
✔ `INTAKE_CONDITION`: 보호 시작 시 상태
✔ `NAME`: 이름
✔ `SEX_UPON_INTAKE`: 성별 및 중성화 여부

3. 문제
✔ 동물 보호소에 들어온 모든 동물의 `아이디`와 `이름`을 `ANIMAL_ID순`으로 조회하는 SQL문을 작성해주세요.

4. **작성한 SQL문**
```sql
SELECT ANIMAL_ID, NAME //ANIMAL_ID, NAME 출력
FROM ANIMAL_INS //테이블 선택
ORDER BY ANIMAL_ID; //ANIMAL_ID 기준으로 오름차순 정렬
```
