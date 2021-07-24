#### **문제** 

<details>
  <summary>문제 </summary>
  <div markdown="1">
    
##### 문제 설명
    
문자열 s는 한 개 이상의 단어로 구성되어 있습니다.

각 단어는 하나 이상의 공백문자로 구분되어 있습니다.

각 단어의 짝수번째 알파벳은 대문자로, 홀수번째 알파벳은 소문자로 바꾼 문자열을 리턴하는 함수, solution을 완성하세요.

##### 제한 사항
- 문자열 전체의 짝/홀수 인덱스가 아니라, 단어(공백을 기준)별로 짝/홀수 인덱스를 판단해야합니다.
- 첫 번째 글자는 0번째 인덱스로 보아 짝수번째 알파벳으로 처리해야 합니다.
    
##### 입출력 예
|s|	return|
|"try hello world"|	"TrY HeLlO WoRlD"|
##### 입출력 예 설명
"try hello world"는 세 단어 "try", "hello", "world"로 구성되어 있습니다.
    
각 단어의 짝수번째 문자를 대문자로, 홀수번째 문자를 소문자로 바꾸면 "TrY", "HeLlO", "WoRlD"입니다. 따라서 "TrY HeLlO WoRlD" 를 리턴합니다.
</div>
</details>

#### **내 풀이** 
```python3
def solution(s):
    answer = ''
    tmp, t = list(), list()
    for i in s:
        if i == ' ':
            tmp.append(t)
            t = []
        else: t.append(i)
    tmp.append(t)
    for i in tmp:
        for j in range(len(i)):
            if j %2 == 0:
                i[j]=i[j].upper()
            elif j%2 != 0:
                i[j]=i[j].lower()
    answer = ''.join(tmp[0])
    for i in range(1,len(tmp)):
        answer = answer +' '+''.join(tmp[i])
    return answer
```

다른 사람의 풀이보고 .. 많이 부족하구나 느꼈다 ,,

`enumerate` 를 사용해서 index 값을 바로 접근해주었다. `lambda` 를 이용해서 `map`의 인자로 넣어주었다. 이를 이용해서 먼저 나누어진 문자열을 합쳐주고 합쳐진 문자열 사이에 공백을 추가하여 `join` 해주었다.

```python3
def toWeirdCase(s):
    return " ".join(map(lambda x: "".join([a.lower() if i % 2 else a.upper() for i, a in enumerate(x)]), s.split(" ")))
```
[출처: programmers rhdudals0659 풀이]

좀 더 파이서닉하게 풀어보고 문제를 보고 바로 코드를 작성하는게 아닌 구체적으로 어떻게 접근할지 생각해보고 코드를 짜도록 해야겠다.
