# 1. 입양 시각 구하기(1) (GROUP BY)
✅ LEVEL2. [입양 시각 구하기(1)](https://programmers.co.kr/learn/courses/30/lessons/59412)

### 문제 요약
1. 테이블 정보
✔ `ANIMAL_OUTS`: 동물 보호소에서 입양 보낸 동물의 정보를 담은 테이블

2. 필드 정보
✔ `ANIMAL_ID`: 동물의 아이디
✔ `ANIMAL_TYPE`: 생물 종
✔ `DATETIME`: 입양일
✔ `NAME`: 이름
✔ `SEX_UPON_INTAKE`: 성별 및 중성화 여부

3. 문제
✔ 보호소에서는 몇 시에 입양이 가장 활발하게 일어나는지 알아보려 합니다. **09:00부터 19:59까지**, `각 시간대별`로 **입양이 몇 건이나 발생했는지 조회**하는 `SQL문`을 작성해주세요. 이때 **결과는 시간대 순으로 정렬**해야 합니다.

4. **작성한 SQL문**
```sql
SELECT HOUR(DATETIME) AS HOUR, COUNT(*) AS COUNT //HOUR, COUNT 출력
FROM ANIMAL_OUTS //테이블 선택
GROUP BY HOUR //HOUR 별로 그룹 생성
HAVING HOUR >= 9 AND HOUR <=19 //HOUR이 9 이상 19 이하 값만 추출
ORDER BY HOUR //HOUR 기준으로 오름차순 정렬
```
> ##### HOUR(DATETIME) 🧐
👉 `HOUR(DATETIME)`를 하면 **시간**만 추출해낼 수 있다.
👉 추가로 `YEAR`, `MONTH`, `DAY`, `MINUTE`, `SECOND`가 있다.

# 2. 루시와 엘라 찾기 (String, Date)
✅ LEVEL2. [루시와 엘라 찾기](https://programmers.co.kr/learn/courses/30/lessons/59046)

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
✔ 동물 보호소에 들어온 동물 중 이름이 **Lucy, Ella, Pickle, Rogan, Sabrina, Mitty인 동물**의 `아이디`와 `이름`, `성별` 및 `중성화 여부`를 조회하는 `SQL 문`을 작성해주세요.

4. **작성한 SQL문**
```sql
SELECT ANIMAL_ID, NAME, SEX_UPON_INTAKE //ANIMAL_ID, NAME, SEX_UPON_INTAKE 출력
FROM ANIMAL_INS //테이블 선택
WHERE NAME in ('Lucy', 'Ella', 'Pickle', 'Rogan', "Sabrina", 'Mitty') //NAME에 'Lucy', 'Ella', 'Pickle', 'Rogan', "Sabrina", 'Mitty'값인 데이터 출력
```

# 3. 이름에 el이 들어가는 동물 찾기 (String, Date)
✅ LEVEL2. [이름에 el이 들어가는 동물 찾기](https://programmers.co.kr/learn/courses/30/lessons/59047)

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
✔ 보호소에 돌아가신 할머니가 기르던 개를 찾는 사람이 찾아왔습니다. 이 사람이 말하길 할머니가 기르던 개는 **이름에 'el'이 들어간다고** 합니다. 동물 보호소에 들어온 `동물 이름 중`, 이름에 `"EL"`이 들어가는 개의 **아이디와 이름**을 조회하는 `SQL문`을 작성해주세요. 이때 결과는 **이름 순으로 조회**해주세요. 단, 이름의 대소문자는 구분하지 않습니다.

4. **작성한 SQL문**
```sql
SELECT ANIMAL_ID, NAME //ANIMAL_ID, NAME 출력
FROM ANIMAL_INS //테이블 선택
WHERE upper(NAME) LIKE '%el%' AND ANIMAL_TYPE = 'Dog' //NAME을 소문자로 변환하고 이름에 'el'이 들어가야하며, ANIMAL_TYPE이 'Dog'인 것 출력
ORDER BY NAME; //NAME 순으로 오름차순 정렬
```

# 4. 중성화 여부 파악하기 (String, Date)
✅ LEVEL2. [중성화 여부 파악하기](https://programmers.co.kr/learn/courses/30/lessons/59409)

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
✔ 보호소의 동물이 중성화되었는지 아닌지 파악하려 합니다. 중성화된 동물은 `SEX_UPON_INTAKE 컬럼`에 `'Neutered'` 또는 `'Spayed'`라는 단어가 들어있습니다. 동물의 `아이디`와 `이름`, `중성화 여부`를 `아이디 순`으로 조회하는 `SQL문`을 작성해주세요. 이때 **중성화가 되어있다면 'O', 아니라면 'X'라고 표시해주세요.**

4. **작성한 SQL문**
```sql
SELECT ANIMAL_ID, NAME, CASE WHEN SEX_UPON_INTAKE LIKE '%Neutered%' OR SEX_UPON_INTAKE LIKE '%Spayed%' THEN 'O' ELSE 'X' END AS '중성화' // ANIMAL_ID, NAME 출력 및 SEX_UPON_INTAKE를 조건에 따라 출력
FROM ANIMAL_INS //테이블 선택
ORDER BY ANIMAL_ID; //ANIMAL_ID 기준으로 오름차순 정렬
```

> ##### CASE WHEN 🧐
👉 기본 형태
```sql
CASE [필드명] 
   WHEN [필드값1] THEN 1
   WHEN [필드값2] THEN 2
   ELSE 3
END
```

# 5. DATETIME에서 DATE로 형 변환 (String, Date)
✅ LEVEL2. [DATETIME에서 DATE로 형 변환](https://programmers.co.kr/learn/courses/30/lessons/59414)

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
✔ ANIMAL_INS 테이블에 등록된 모든 레코드에 대해, 각 동물의 `아이디`와 `이름`, `들어온 날짜`를 조회하는 `SQL문`을 작성해주세요. 이때 결과는 **아이디 순으로 조회**해야 합니다.
👉 시각(시-분-초)을 제외한 날짜(년-월-일)만 보여주세요.

4. **작성한 SQL문**
```sql
SELECT ANIMAL_ID, NAME, DATE_FORMAT(DATETIME, '%Y-%m-%d') //ANIMAL_ID, NAME, DATETIME 출력
FROM ANIMAL_INS //테이블 선택
```

# 6. NULL 처리하기 (IS NULL)
✅ LEVEL2. [DATETIME에서 DATE로 형 변환](https://programmers.co.kr/learn/courses/30/lessons/59410)

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
✔ 입양 게시판에 동물 정보를 게시하려 합니다. 동물의 `생물 종`, `이름`, `성별` 및 `중성화 여부`를 **아이디 순으로 조회**하는 `SQL문`을 작성해주세요. 이때 프로그래밍을 모르는 사람들은 NULL이라는 기호를 모르기 때문에, **이름이 없는 동물의 이름은 "No name"으로 표시해 주세요.**

4. **작성한 SQL문**
```sql
SELECT ANIMAL_TYPE, IFNULL(NAME, 'No name') AS NAME, SEX_UPON_INTAKE //ANIMAL_TYPE, NAME, SEX_UPON_INTAKE 출력
FROM ANIMAL_INS //테이블 선택
ORDER BY ANIMAL_ID; //ANIMAL_ID 순으로 오름차순 정렬
```
