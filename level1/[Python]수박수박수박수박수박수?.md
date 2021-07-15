#### **문제** 

<details>
  <summary>문제 </summary>
  <div markdown="1">
    
##### 문제 설명
    
길이가 n이고, "수박수박수박수...."와 같은 패턴을 유지하는 문자열을 리턴하는 함수, solution을 완성하세요. 예를들어 n이 4이면 "수박수박"을 리턴하고 3이라면 "수박수"를 리턴하면 됩니다.

##### 제한 조건
- n은 길이 10,000이하인 자연수입니다.
##### 입출력 예
|n|	return|
|--|--|    
|3|	"수박수"|
|4|	"수박수박"|
</div>
</details>

#### **내 풀이** 
```python3
def solution(n):
    answer = ''
    for i in range(n):
        if i % 2 == 0:
            answer += '수'
        else:
            answer += '박'
    return answer
```

나머지를 이용하여 문자열을 생성해주었다.

다른 사람의 풀이를 보니 더 파이써닉하게 잘 푼것 같아 참고해보았다.

```python3
def water_melon(n):
    s = "수박" * n
    return s[:n]
```
[출처: programmers - , jay , 이준 , Ji Hoon Kim , - 외 28 명]

수박을 `n`번 반복해주고 앞에서 `n`번까지 잘라준다.
