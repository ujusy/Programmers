#### **문제** 

<details>
  <summary>문제 </summary>
  <div markdown="1">
문제 설명
수포자는 수학을 포기한 사람의 준말입니다. 수포자 삼인방은 모의고사에 수학 문제를 전부 찍으려 합니다. 수포자는 1번 문제부터 마지막 문제까지 다음과 같이 찍습니다.

1번 수포자가 찍는 방식: 1, 2, 3, 4, 5, 1, 2, 3, 4, 5, ...
    
2번 수포자가 찍는 방식: 2, 1, 2, 3, 2, 4, 2, 5, 2, 1, 2, 3, 2, 4, 2, 5, ...
    
3번 수포자가 찍는 방식: 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, ...

1번 문제부터 마지막 문제까지의 정답이 순서대로 들은 배열 answers가 주어졌을 때, 가장 많은 문제를 맞힌 사람이 누구인지 배열에 담아 return 하도록 solution 함수를 작성해주세요.

##### 제한 조건
시험은 최대 10,000 문제로 구성되어있습니다.
    
문제의 정답은 1, 2, 3, 4, 5중 하나입니다.
    
가장 높은 점수를 받은 사람이 여럿일 경우, return하는 값을 오름차순 정렬해주세요.
    
##### 입출력 예
    
|answers|	return|
|--|--|    
|[1,2,3,4,5]|	[1]|
|[1,3,2,4,2]|	[1,2,3]|
    
##### 입출력 예 설명
입출력 예 #1

- 수포자 1은 모든 문제를 맞혔습니다.
- 수포자 2는 모든 문제를 틀렸습니다.
- 수포자 3은 모든 문제를 틀렸습니다.
- 따라서 가장 문제를 많이 맞힌 사람은 수포자 1입니다.

입출력 예 #2

모든 사람이 2문제씩을 맞췄습니다.
</div>
</details>

#### **내 풀이** 

```python3
from itertools import cycle
def solution(answers):
    a_answer = [1,2,3,4,5]
    b_answer = [2,1,2,3,2,4,2,5]
    c_answer = [3,3,1,1,2,2,4,4,5,5]
    a = cycle(a_answer)
    b = cycle(b_answer)
    c = cycle(c_answer)
    a_c, b_c, c_c = 0, 0, 0

    for i in answers:
        if i == next(a):
            a_c +=1
        if i == next(b):
            b_c +=1
        if i == next(c):
            c_c +=1
    result = [a_c, b_c, c_c]
    answer = []
    m = max(result)
    [answer.append(i) for i, v in enumerate(result, start=1) if v==m]
    return answer
```
cycle을 이용해 순회하면서 일치 부를 판별한다. cycle은 리스트를 무한 순회한다.
그리고 난 후 ```enumerate```를 이용해 인덱스를 주고 최대값에 일차하는 인덱스만 리스트에 추가한다.
