# [PYTHON] 2차원 리스트를 1차원 리스트로 만들기 - from_iterable

----------

<img width="674" alt="image-20200406004646658" src="https://user-images.githubusercontent.com/49120090/78503746-7d131a80-77a3-11ea-8fbc-8085019ed0c7.png">

**[내 풀이]**

for문을 이용해 리스트를 순차적으로 돌면서 answer list에 append 해주었다 . range(1,len(mylist))해준 이유는  answer = mylist[0]으로 선언되어 0의 원소가 들어가 있기 때문에 그 이후로 append해주었다. 

```python
def solution(mylist):
    answer = mylist[0]
    for i in range(1,len(mylist)):
        for j in range(len(mylist[i])):
            answer.append(mylist[i][j]);
    return answer //0.04ms 10.8MB
```

---------------

파이썬 에서는 다양한 기능을 사용하여 for문을 사용하지 않고도 리스트를 이어 붙일 수 있다. 

여러가지 풀이를 통해 공부해 보도록 하겠다. 

1. 하나의 for문만을 이용한 풀이. 

```python
def solution(mylist):
    answer = [];
    for i in mylist:
        answer += i
    return answer  //0.04 ms 10.7MB
```

2.  sum 함수 이용

   ```python
   my_list = [[1, 2], [3, 4], [5, 6]]
   
   answer = sum(my_list, [])
   ```

3. itertoos.chain

   ```python
   import itertools
   list(itertools.chain.from_iterable(my_list))
   ```

4. itertools와 unpacking

   ```python
   import itertools
   list(itertools.chain(*my_list))
   ```

5. reduce 함수 이용1

   ```python
   [element for array in my_list for element in array]
   ```

6. reduce 함수 이용2

   ```python
   from functools import reduce
   list(reduce(lambda x, y: x+y, my_list))
   ```

7. Bumpy 라이브러리 flatten이용

   ```python
   import numpy as np
   np.array(my_list).flatten().tolist()
   ```

