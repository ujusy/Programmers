# SELECT

## 어린 동물 찾기



+ 문제

  <img width="642" alt="image-20191028153619656" src="https://user-images.githubusercontent.com/49120090/67657608-9d3fe180-f99a-11e9-83ca-91abb1b4d417.png">



+ 답안

~~~sql
SELECT ANIMAL_ID,NAME FROM ANIMAL_INS WHERE INTAKE_CONDITION != 'Aged'
~~~



+ 풀이

>ANIMAL_ID와 NAME을 가져온다.
>
>ANIMAL_INS 테이블에서
>
>WHERE(조건)
>
>INTAKE_CONODITION이 늙지 않은 동물
>
>!='Aged'

