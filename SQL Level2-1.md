# 1. 최솟값 구하기 (SUM, MAX, MIN)
✅ LEVEL2. [최솟값 구하기](https://programmers.co.kr/learn/courses/30/lessons/59038)

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
✔ 동물 보호소에 **가장 먼저 들어온 동물**은 언제 들어왔는지 조회하는 `SQL 문`을 작성해주세요.

4. **작성한 SQL문**
```sql
SELECT MIN(DATETIME) //DATETIME 필드의 최솟값 출력
FROM ANIMAL_INS //테이블 선택
```
> ##### MIN 🧐
👉 행의 **최솟값을 출력**한다.

# 2. 동물 수 구하기 (SUM, MAX, MIN)
✅ LEVEL2. [동물 수 구하기](https://programmers.co.kr/learn/courses/30/lessons/59406)

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
✔ 동물 보호소에 동물이 **몇 마리 들어왔는지 조회**하는 `SQL 문`을 작성해주세요.

4. **작성한 SQL문**
```sql
SELECT COUNT(*) //모든 필드의 개수 출력
FROM ANIMAL_INS //테이블 선택
```
> ##### COUNT 🧐
👉 **행의 개수를 세는** 집계 함수.
👉 필드명에 **\*을 넣으면 모든 행의 개수를 출력**하라는 말이다. 이렇게 \*을 파라미터로 받을 수 있는 집계 함수는 `COUNT`가 유일함.
👉 `COUNT`를 비롯한 집계 함수들은 **기본적으로 NULL값을 제외하고 카운트.**

# 3. 중복 제거하기 (SUM, MAX, MIN)
✅ LEVEL2. [중복 제거하기](https://programmers.co.kr/learn/courses/30/lessons/59408)

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
✔ 동물 보호소에 들어온 동물의 이름은 몇 개인지 조회하는 `SQL 문`을 작성해주세요. 이때 이름이 NULL인 경우는 집계하지 않으며 **중복되는 이름은 하나로 칩니다.**

4. **작성한 SQL문**
```sql
SELECT COUNT(DISTINCT(NAME)) //NAME 필드의 중복을 제거한 레코드 총 개수
FROM ANIMAL_INS //테이블 선택
```
> ##### DISTINCT 🧐
👉 `DISTINCT` 뒤에 나오는 열들에 대하여 같은 값을 가진 **중복된 행을 제외**한다.

# 4. 고양이와 개는 몇 마리 있을까 (GROUP BY)
✅ LEVEL2. [고양이와 개는 몇 마리 있을까](https://programmers.co.kr/learn/courses/30/lessons/59040)

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
✔ 동물 보호소에 들어온 동물 중 **고양이와 개가 각각 몇 마리인지 조회**하는 `SQL문`을 작성해주세요. 이때 **고양이를 개보다 먼저 조회**해주세요.

4. **작성한 SQL문**
```sql
SELECT ANIMAL_TYPE, COUNT(ANIMAL_TYPE) AS count //ANIMAL_TYPE, COUNT 출력
FROM ANIMAL_INS //테이블 선택
GROUP BY ANIMAL_TYPE //ANIMAL_TYPE 별로 그룹 생성
ORDER BY ANIMAL_TYPE //CAT이 DOG보다 먼저 나와야 하기 때문에 오름차순 정렬
```
> ##### GROUP BY 🧐
👉 `MySQL`에서 **유형별로 개수를 가져오고 싶을 때** 사용한다. 단순히 `COUNT` 함수로 데이터를 조회하면 전체 개수만 가져옴.

# 5. 동명 동물 수 찾기 (GROUP BY)
✅ LEVEL2. [동명 동물 수 찾기](https://programmers.co.kr/learn/courses/30/lessons/59041)

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
✔ 동물 보호소에 들어온 동물 이름 중 **두 번 이상 쓰인 이름**과 **해당 이름이 쓰인 횟수**를 조회하는 `SQL문`을 작성해주세요. 이때 결과는 **이름이 없는 동물은 집계에서 제외**하며, 결과는 **이름 순으로 조회**해주세요.

4. **작성한 SQL문**
```sql
SELECT NAME, COUNT(NAME) AS COUNT //NAME, COUNT 출력
FROM ANIMAL_INS //테이블 선택
GROUP BY NAME //NAME 별로 그룹 생성
HAVING COUNT >= 2 //NAME이 2번 이상 중복된 것만 조회
ORDER BY NAME; //NAME을 기준으로 오름차순 정렬
```
> ##### HAVING 🧐
👉 특정 컬럼을 **그룹화한 결과에 조건을 거는** 키워드
쉽게 말해서, `WHERE`는 **그룹화 하기 전**에 조건을 거는 것이고, `HAVING`은 **그룹화한 후에** 조건을 걸어 사용한다.
