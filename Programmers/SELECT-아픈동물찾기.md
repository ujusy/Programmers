# SELECT

## 아픈 동물 찾기



+ 문제

  ![image](https://user-images.githubusercontent.com/49120090/67656745-02460800-f998-11e9-9dff-45ca3833b171.png)



+ 답안

  ~~~sql
  SELECT ANIMAL_ID,NAME FROM ANIMAL_INS WHERE INTAKE_CONDITION='Sick'
  ~~~

+ 풀이

  >ANIMAL_ID와 NAME 가져온다
  >
  >ANIMAL_INS테이블에서
  >
  >WHERE: 조건
  >
  >INTAKE_CONDITION에서 Sick인 동물들