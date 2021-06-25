#### **문제** 

<details>
  <summary>문제 </summary>
  <div markdown="1">
문제 설명
정수 배열 numbers가 주어집니다. numbers에서 서로 다른 인덱스에 있는 두 개의 수를 뽑아 더해서 만들 수 있는 모든 수를 배열에 오름차순으로 담아 return 하도록 solution 함수를 완성해주세요.

##### 제한사항
- numbers의 길이는 2 이상 100 이하입니다.
- numbers의 모든 수는 0 이상 100 이하입니다.
    
##### 입출력 예
|numbers|	result|
|[2,1,3,4,1]|	[2,3,4,5,6,7]|
|[5,0,2,7]|	[2,5,7,9,12]|
입출력 예 설명
입출력 예 #1

2 = 1 + 1 입니다. (1이 numbers에 두 개 있습니다.)
    
3 = 2 + 1 입니다.
    
4 = 1 + 3 입니다.
    
5 = 1 + 4 = 2 + 3 입니다.
    
6 = 2 + 4 입니다.
    
7 = 3 + 4 입니다.
    
따라서 [2,3,4,5,6,7] 을 return 해야 합니다.
    
입출력 예 #2

2 = 0 + 2 입니다.
    
5 = 5 + 0 입니다.
    
7 = 0 + 7 = 5 + 2 입니다.
    
9 = 2 + 7 입니다.
    
12 = 5 + 7 입니다.
    
따라서 [2,5,7,9,12] 를 return 해야 합니다.
</div>
</details>

#### **내 풀이** 
```python3
from itertools import combinations
def solution(numbers):
    comb = list(combinations(numbers, 2))
    ans = sorted(list(set(list(map(sum ,comb)))))
    return ans
```

`combinations`을 사용하여 2개의 조합을 만들었다. 

그 후 sum을 통해 각각의 튜플들의 합을 리스트로 만들어주었고 중복된 값을 `set`을 통해 제거해 주었다. 

오름차순으로 정렬하므로 `sorted`로 정렬해주었다.

다른 사람들의 풀이를 보면 이중 for문을 사용을 사용하여 조합의 합을 만들어주었다.
