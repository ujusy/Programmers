# [PYTHON]삼각형 별찍기

--------

<img width="669" alt="image-20200316004531415" src="https://user-images.githubusercontent.com/49120090/78501956-767fa580-7799-11ea-96df-c9d1acd2456c.png">

[내 풀이]

>for문을 이용한 단순 풀이
>
>```python
>n = int(input().strip())
>for i in range(1,n+1):
>    print('*'*i)
>```

-------------

```*```  연산자에 대해 알아보자. 

```*``` 연산자를 이용하면 [123,456, 123, 456..]과 같이 123 , 456이 n번 반복되는 리스트를 만들 수 있다.

```python
n = 어쩌고
answer= [123, 456]*n
```

