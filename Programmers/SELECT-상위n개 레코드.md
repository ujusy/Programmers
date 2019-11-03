# SELECT 

## 상위 n개 레코드



+ 문제

![image](https://user-images.githubusercontent.com/49120090/67657929-82ba3800-f99b-11e9-8642-4f493a4f262a.png)



+ 답안

  ~~~sql
  SELECT NAME FROM ANIMAL_INS ORDER BY DATETIME LIMIT 1
  ~~~

+ 풀이

  >가장 먼저 들어온 동물이므로 
  >
  >LIMIT를 사용하여  하나만을 조회한다.
  >
  >ORDER BY DATETIME: DATETIME순으로 정렬 뒤 맨 처음 하나 추출