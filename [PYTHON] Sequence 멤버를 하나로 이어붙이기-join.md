# [PYTHON] Sequence 멤버를 하나로 이어붙이기-join

------------

<img width="678" alt="image-20200316001952328" src="https://user-images.githubusercontent.com/49120090/76704595-638b2f80-671d-11ea-9a1d-e14e20de24f4.png">

[내 풀이]

```python
def solution(mylist):
    answer = ''
    for i in mylist:
        answer += i
    return answer
```

-----------

**join을 이용해보자!**

```python
my_list = ['1', '100', '33']
answer = ''.join(my_list)
```

