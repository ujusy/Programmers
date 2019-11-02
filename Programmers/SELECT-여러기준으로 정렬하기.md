# SELECT

## 여러 기준으로 정렬하기



+ 문제

  ![image](https://user-images.githubusercontent.com/49120090/67657747-06bff000-f99b-11e9-9be9-e3e25eb488ee.png)



+ 답안

~~~sql
SELECT ANIMAL_ID,NAME,DATETIME FROM ANIMAL_INS ORDER BY NAME, DATETIME DESC
~~~



+ 풀이

  >ANIMAL_ID, NAME,DATETIME 추출
  >
  >테이블 ANIMAL_INS로 부터
  >
  >먼저 NAME으로 정렬하고 난 뒤 같은 이름은
  >
  >DATETIME이 나중에 시작한 동물을 먼저 보여줘
  >
  >DATETIME DESC사용하여 나중에 시작한 것 부터 정렬