# SQL_ADVANCED 2주차 정규 과제 

📌SQL_ADVANCED 정규과제는 매주 정해진 분량의 『*혼자 공부하는 SQL*』 을 읽고 학습하는 것입니다. 이번주는 아래의 **SQL_ADVANCED_2nd_TIL**에 나열된 분량을 읽고 공부하시면 됩니다.

아래의 문제를 풀어보며 학습 내용을 점검하세요. 문제를 해결하는 과정에서 개념을 스스로 정리하고, 필요한 경우 제시된 강의를 참고하여 보완하는 것이 좋습니다.

<!-- 강의 링크는 아래와 같습니다.
https://www.youtube.com/watch?v=_JURyg_KzHE&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=7
https://www.youtube.com/watch?v=6qkPy7RfLqQ&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=8
https://www.youtube.com/watch?v=WWAFAm9op2U&list=PLVsNizTWUw7GCfy5RH27cQL5MeKYnl8Pm&index=9
-->

**교재 실습 예제 파일은 08_SQL_ADVANCED_Template 레포지토리의 src 폴더에 업로드되어 있습니다. market_db 파일도 해당 폴더에 함께 포함되어 있으니 참고하시기 바랍니다.**

**👀(수행 인증샷은 필수입니다.)** 

## SQL_ADVANCED_2nd_TIL

### 3장 SQL 기본 문법
#### 01. 기본 중에 기본 SELECT ~ FROM ~ WHERE
#### 02. 좀 더 깊게 알아보는 SELECT문
#### 03. 데이터 변경을 위한 SQL문


## Study Schedule

| 주차  | 공부 범위     | 완료 여부 |
| ----- | ------------- | --------- |
| 1주차 | p.24~99    | ✅         |
| 2주차 | p.102~155   | ✅         |
| 3주차 | p.158~213  | 🍽️         |
| 4주차 | p.216~271 | 🍽️         |
| 5주차 | p.274~327 | 🍽️         |
| 6주차 | p.330~369 | 🍽️         |
| 7주차 | p.372~407 | 🍽️         |


<br>

<!-- 여기까진 그대로 둬 주세요-->

---

# 1️⃣ 학습 내용 정리

## 1. 기본 중에 기본 SELECT ~ FROM ~ WHERE

SELECT의 가장 기본 형식은 SELECT~FROM~WHERE이다.

한 번 USE를 설정해놓으면 다른 USE를 사용하기 전까지 유지된다.

![실습1](week2_image/실습1.png)
![실습2](week2_image/실습2.png)

> **확인문제: 주소의 지역이 서울, 경기인 회원을 추출하는 SQL 문입니다. 빈칸에 들어갈 수 있는 것을 모두 고르세요.**

```sql
SELECT *
FROM table
WHERE ________;
```

보기는 아래와 같습니다.
```
1. addr IN('서울', '경기')
2. addr BETWEEN '서울' AND '경기'
3. addr = '서울' OR addr = '경기'
4. addr = '서울' AND addr = '경기'
```

```
정답 : 1, 3
1번과 3번 모두 '서울' 또는 '경기'이면 참이라는 의미이다. 
2번은 '서울' 이상 '경기' 이하이면 참이라는 의미로, 가다나 순으로 했을 때 그 사이에 올 수 있는 값이 없어 출력할 수 있는 값이 없다. 
4번은 '서울', '경기' 모두 참이이어야 하지만 주소가 서울과 경기에 모두 해당될 수 없어 출력할 수 있는 값이 없다. 
```


## 2. 좀 더 깊게 알아보는 SELECT문

<!-- ORDER BY절과 GROUP BY절 그리고 HAVING절에 관해 배우게 된 점을 적어주세요. -->

```
ORDER BY절: 결과를 정렬해서 보여주는 것으로,  차례만 바뀐다.
GROUP BY절: 그룹으로 묶어주는 것
HAVING절: GROUP 함수에서 조건을 쓸 때 적용한다
```

> **확인문제: 다음 표는 주요 집계함수를 정리한 것입니다. 각 설명에 해당하는 올바른 함수명을 기호에 맞게 작성하세요.**

| 함수명 | 설명 |
|--------|------|
| SUM() | 합계를 구합니다. |
| (ㄱ) | 평균을 구합니다. |
| (ㄴ) | 최소값을 구합니다. |
| MAX() | 최대값을 구합니다. |
| (ㄷ) | 행의 개수를 셉니다. |
| (ㄹ) | 행의 개수를 셉니다 (중복은 1개만 인정). |

```
여기에 답을 적어주세요!
(ㄱ) AVG()
(ㄴ) MIN()
(ㄷ) COUNT()
(ㄹ) COUNT(DISTINCT)
```


## 3. 데이터 변경을 위한 SQL문

<!-- INSERT문, UPDATE문, DELETE문에 관해 배우게 된 점을 적어주세요. -->

```
INSERT문: 데이터를 입력하는 명령, 기본 형식은 INSERT INTO 테이블 [(열1, ...)] VALUES (값1, ...);
        CREATE TABLE 할 때 AUTO_INCREMENT 사용하면 자동으로 생성된다. PRIMERY KEY로 지정해줘야 한다. -> INSERT할 때 값을 NULL로 비워놓으면 자동으로 채워진다.
        AUTO_INCREMENT=n(n부터 시작)
        SET @@ auto_increment_increment=m(m씩 건너뛰기)
        SELECT와 함께 사용하면 다른 테이블 데이터 가져와서 한 번에 넣을 수 있다. 
UPDATE문: 데이터를 수정하는 명령, 기본 형식은 UPDATE 테이블 SET 열1=값1, ... WHERE 조건;
DELETE문: 데이터를 삭제하는 명령
```


# 2️⃣ 실습과제

다음 SQL 문을 작성하고 실행 결과를 확인 후 인증 사진을 아래에 업로드하세요.(market_db를 그대로 사용합니다.)

1. 모든 그룹 멤버의 정보를 조회하시오.
2. 멤버의 수가 6명 이상인 그룹 정보를 조회하시오.
3. 현재 구매 테이블에 존재하는 서로 다른 상품(prod_name)이 어떤 것이 있는지 조회하시오.
4. 총 구매 금액이 1000미만인 prod_name 중 상위 2개만 조회하시오.

![문제1](week2_image/문제1.png)
![문제2](week2_image/문제2.png)
![문제3](week2_image/문제3.png)
![문제4](week2_image/문제4.png)

### 🎉 수고하셨습니다.