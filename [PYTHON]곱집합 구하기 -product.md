# [PYTHON] 곱집합 (Cartesian product) 구하기 - product

-----------

만약 ABCD 와 xy의 곱집합은 Ax Ay Bx By Cx Cy Dx Dy 이다.

일반적으로 사람들은

```python
iterable1 = 'ABCD'
iterable2 = 'xy'
iterable3 = '1234'

for i in iterable1:
    for j in iterable2:
        for k in iterable3:
            print(i+j+k)
```

for문을 이용해 순차적으로 곱해 나간다. 

```itertools.product``` 를 이용하여 for문을 사용하지 않고 곱집합 구할 수 있다. 

```python
import itertools

iterable1 = 'ABCD'
iterable2 = 'xy'
iterable3 = '1234'
itertools.product(iterable1, iterable2, iterable3)
```

