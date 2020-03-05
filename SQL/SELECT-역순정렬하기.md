# SELECT

## 역순 정렬하기



+ 문제

  ![image](https://user-images.githubusercontent.com/49120090/67656511-543a5e00-f997-11e9-8bdd-de28c776ab51.png)

+ 답안

  ~~~sql
  SELECT NAME,DATETIME FROM ANIMAL_INS ORDER BY ANIMAL_ID DESC
  ~~~
  
  

+ 풀이

  >NAME과 DATETIME 뽑아야하므로 SELECT NAME,DATETIME
  >
  >FROM ANIMAL_INS (ANIMAL_INS테이블로 부터)
  >
  >ORDER BY ANIMAL_ID 로 정렬
  >
  >DESC:역순으로