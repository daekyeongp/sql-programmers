# 1. 여러 기준으로 정렬하기 (SELECT)
✅ LEVEL1. [여러 기준으로 정렬하기](https://programmers.co.kr/learn/courses/30/lessons/59404)

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
✔ 동물 보호소에 들어온 모든 동물의 `아이디`와 `이름`, `보호 시작일`을 `이름 순으로 조회`하는 `SQL문`을 작성해주세요. 단, **이름이 같은 동물 중에서는 보호를 나중에 시작한 동물을 먼저 보여줘야 합니다.**

4. **작성한 SQL문**
```sql
SELECT ANIMAL_ID, NAME, DATETIME //ANIMAL_ID, NAME, DATETIME 출력
FROM ANIMAL_INS //테이블 선택
ORDER BY NAME ASC, DATETIME DESC; //NAME을 기준으로 오름차순 정렬, DATETIME을 기준으로 내림차순 정렬
```
> ##### ORDER BY 🧐
👉 **왼쪽부터 순차적으로 정렬**되기 때문에 우선 순위가 높은 순서대로 나열해야 한다.

# 2. 상위 n개 레코드 (SELECT)
✅ LEVEL1. [상위 n개 레코드](https://programmers.co.kr/learn/courses/30/lessons/59405)

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
✔ 동물 보호소에 `가장 먼저 들어온 동물의 이름`을 조회하는 `SQL 문`을 작성해주세요.

4. **작성한 SQL문**
```sql
SELECT NAME //NAME 출력
FROM ANIMAL_INS //테이블 선택
ORDER BY DATETIME //DATETIME을 기준으로 오름차순 정렬
LIMIT 1; //1개 출력
```
> ##### LIMIT 🧐
👉 `SELECT`로 데이터를 조회할 때 `LIMIT` 키워드를 사용하면 **출력할 개수를 지정할 수 있다.**
👉 `OFFSET` 키워드를 추가로 사용하면 **가져오고자 하는 행 데이터의 시작 지점을 지정 가능.**

# 3. 최댓값 구하기 (SUM, MAX, MIN)
✅ LEVEL1. [최댓값 구하기](https://programmers.co.kr/learn/courses/30/lessons/59415)

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
✔ 가장 최근에 들어온 동물은 언제 들어왔는지 조회하는 `SQL 문`을 작성해주세요.

4. **작성한 SQL문**
```sql
SELECT DATETIME //DATETIME 출력
FROM ANIMAL_INS //테이블 선택
ORDER BY DATETIME DESC //DATETIME 기준으로 내림차순 정렬
LIMIT 1; //1개 출력
------------------------
SELECT MAX(DATETIME) //DATETIME 필드의 최댓값 출력
FROM ANIMAL_INS; //테이블 선택
```
> ##### MAX 🧐
👉 행의 **최댓값**을 출력한다.
👉 `MAX`는 다른 집계함수들과는 달리 **문자열이나 날짜에도 사용 가능하다.**

# 4. 이름이 없는 동물의 아이디 (IS NULL)
✅ LEVEL1. [이름이 없는 동물의 아이디](https://programmers.co.kr/learn/courses/30/lessons/59039)

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
✔ 동물 보호소에 들어온 동물 중, **이름이 없는 채로 들어온 동물의 ID를 조회**하는 `SQL 문`을 작성해주세요. 단, `ID는 오름차순 정렬`되어야 합니다.

4. **작성한 SQL문**
```sql
SELECT ANIMAL_ID //ANIMAL_ID 출력
FROM ANIMAL_INS //테이블 선택
WHERE NAME IS NULL //NAME 필드의 값이 NULL인 레코드 조회
ORDER BY ANIMAL_ID; //ANIMAL_ID를 기준으로 오름차순 정렬
```
> ##### IS NULL 🧐
👉 `NULL` 값은 0 또는 공백이 포함된 필드와는 다르다.
👉 즉, `NULL` 값이 있는 필드는 **값이 없는 필드이다.**
쉽게 말해서 `NULL`값이 있는 필드는 비어 있는 필드 라고 생각하자.✍

# 5. 이름이 있는 동물의 아이디 (IS NULL)
✅ LEVEL1. [이름이 있는 동물의 아이디](https://programmers.co.kr/learn/courses/30/lessons/59407)

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
✔ 동물 보호소에 들어온 동물 중, **이름이 있는 동물의 ID를 조회**하는 `SQL 문`을 작성해주세요. 단, `ID는 오름차순 정렬`되어야 합니다.

4. **작성한 SQL문**
```sql
SELECT ANIMAL_ID //ANIMAL_ID 출력
FROM ANIMAL_INS //테이블 선택
WHERE NAME IS NOT NULL //NAME 필드의 값이 NULL이 아닌 레코드 조회
ORDER BY ANIMAL_ID; //ANIMAL_ID를 기준으로 오름차순 정렬
```
> ##### IS NOT NULL 🧐
👉 `IS NULL`과 반대로 `IS NOT NULL`은 `NULL`이 아닌 값을 조회하는 연산자이다.
