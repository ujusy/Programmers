# 가장 많이 등장하는 알파벳 찾기

--------

<img width="670" alt="image-20200515045417310" src="https://user-images.githubusercontent.com/49120090/81982992-9befb100-966d-11ea-9f38-c506d1636f22.png">

배운점: ```from collections import Counter``` 을 import하여 ```Counter``사용.

 			Counter을 사용하면 어떤 알파벳이 얼만큼 사용되었는지 알 수 있다. 

​			```Counter.values()``` 로 튜플내의 값들을 가져올 수있다. 

​			정수형 리스트로 바꾸고 싶다면 : ```list(map(int,my_list.values()))```

​			문자열 배열을 문자열로 : ```''.join(result)``` 

```python
from collections import Counter 
my_str = input().strip()
my_str = list(my_str)
my_list = Counter(my_str)
list2= list(map(int,my_list.values()))
list2.sort(reverse=True) #values에서 제일 큰 값 뽑아오기..
a = list2[0]
result = []
for key in my_list:
    if a == my_list[key]:
        result.append(key)
    else:
        continue
result.sort()
print(''.join(result))
```

시행 착오를 겪었는데 그 이유가 a에 가장 큰 값을 넣어주지 않고 list2[0]로만 해줘서 실패하다가 list2를 내림차순으로 정렬 후 적용하였더니 통과했다. 

Counter 예시

>```python
>import collections
>my_list = [1, 2, 3, 4, 5, 6, 7, 8, 7, 9, 1, 2, 3, 3, 5, 2, 6, 8, 9, 0, 1, 1, 4, 7, 0]
>answer = collections.Counter(my_list)
>
>print(answer[1]) # = 4
>print(answer[3])  # = 3
>print(answer[100]) # = 0
>```