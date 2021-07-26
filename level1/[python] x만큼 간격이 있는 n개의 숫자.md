#### **문제** 

<details>
  <summary>문제 </summary>
  <div markdown="1">
    
##### 문제 설명
    
함수 solution은 정수 x와 자연수 n을 입력 받아, x부터 시작해 x씩 증가하는 숫자를 n개 지니는 리스트를 리턴해야 합니다. 다음 제한 조건을 보고, 조건을 만족하는 함수, solution을 완성해주세요.

##### 제한 조건
- x는 -10000000 이상, 10000000 이하인 정수입니다.
- n은 1000 이하인 자연수입니다.
#### 입출력 예
|x|	n|	answer|
|--|--|--|    
|2|	5|	[2,4,6,8,10]|
|4|	3|	[4,8,12]|
|-4|	2|	[-4, -8]|
</div>
</details>

#### **내 풀이** 
```python3
def solution(x, n):
    answer = [x]
    for _ in range(n-1):
        answer.append((answer[-1] + x))
    return answer
```

`for`문을 더 잘 쓴 풀이 , `for`의 가운데는 건너뛰는 만큼을 작성해주는데 `x*`를 하여 음수의 경우 또한 처리하였다.
```python3
def solution(x, n):
    ans=list(range(x, x*(n+1) ,x))
    return ans
```
