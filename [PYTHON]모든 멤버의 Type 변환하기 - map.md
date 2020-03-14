# [PYTHON]모든 멤버의 Type 변환하기 - map

--------

>예를 들어서 문자열 배열을 정수형 배열로 교체하고 싶다.

>[내가 접근 했던 방식]
>
>=> for을 이용해 하나하나 type을 바꾸어 주어 list에 append 해주었다
>
>~~~python
>def solution(mylist):
>answer = []
>b =0
>for i in mylist:
>   b = int(i)
>   answer.append(b)
>return answer
>~~~



>[파이썬을 파이썬 답게 풀어보자]
>
>~~~python
>list1 = ['1', '100', '33']
>list2 = list(map(int, list1)
>~~~
>
>**map** 을 이용하면 for문을 사용하지 않고 멤버의 타입을 일괄 변환할 수 있다.