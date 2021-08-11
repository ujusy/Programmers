#### **문제** 

<details>
  <summary>문제 </summary>
  <div markdown="1">
    
##### 문제 설명
    
2차원 행렬 arr1과 arr2를 입력받아, arr1에 arr2를 곱한 결과를 반환하는 함수, solution을 완성해주세요.

##### 제한 조건
- 행렬 arr1, arr2의 행과 열의 길이는 2 이상 100 이하입니다.
- 행렬 arr1, arr2의 원소는 -10 이상 20 이하인 자연수입니다.
- 곱할 수 있는 배열만 주어집니다.
    
##### 입출력 예
|arr1|	arr2|	return|
|--|--|--|    
|[[1, 4], [3, 2], [4, 1]]|	[[3, 3], [3, 3]]|	[[15, 15], [15, 15], [15, 15]]|
|[[2, 3, 2], [4, 2, 4], [3, 1, 4]]|	[[5, 4, 3], [2, 4, 1], [3, 1, 1]]|	[[22, 22, 11], [36, 28, 18], [29, 20, 14]]|
</div>
</details>

#### **내 풀이** 
```python3
def solution(arr1, arr2):
    answer = []
    arr2 = list(zip(*arr2))
    tmp = []
    t =0
    for i in arr1:
        for j in arr2:
            for a in range(len(i)):
                t += i[a]*j[a]
            tmp.append(t)
            t=0
        answer.append(tmp)
        tmp = []
            
    return answer
```

행렬의 곱셈 nxm mxz => n행 x열 행렬 

곱해지는 mz 행렬을 `zip(*)` 을 이용하여 행과 열을 바꿔주었다.

그렇게 리스트별로 곱해주면서 append 시켜주어 출력하였다.

다른 사람 풀이로 아래와 같은 풀이를 보았는데 훨씬 깔끔하다.

`sum(a*b for a, b in zip(A_row,B_col))` 이 부분을 내가 쓴 풀이를 축약하여 적어 훨씬 보기 깔끔한것같다.
```python
def productMatrix(A, B):
    return [[sum(a*b for a, b in zip(A_row,B_col)) for B_col in zip(*B)] for A_row in A]
```
[출처: programmers - , - , - , 이도형 , Ezechiel_Kim 외 1 명]
