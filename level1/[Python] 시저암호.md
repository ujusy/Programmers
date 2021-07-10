#### **문제** 

<details>
  <summary>문제 </summary>
  <div markdown="1">
    
##### 문제 설명
어떤 문장의 각 알파벳을 일정한 거리만큼 밀어서 다른 알파벳으로 바꾸는 암호화 방식을 시저 암호라고 합니다. 예를 들어 "AB"는 1만큼 밀면 "BC"가 되고, 3만큼 밀면 "DE"가 됩니다. "z"는 1만큼 밀면 "a"가 됩니다. 문자열 s와 거리 n을 입력받아 s를 n만큼 민 암호문을 만드는 함수, solution을 완성해 보세요.

##### 제한 조건
- 공백은 아무리 밀어도 공백입니다.
- s는 알파벳 소문자, 대문자, 공백으로만 이루어져 있습니다.
- s의 길이는 8000이하입니다.
- n은 1 이상, 25이하인 자연수입니다.
    
##### 입출력 예
|s|	n|	result|
|--|--|--|    
|"AB"|	1|	"BC"|
|"z"|	1|	"a"|
|"a B z"|	4|	"e F d"|
</div>
</details>

#### **내 풀이**
```python3
def solution(s, n):
    answer = ''
    for i in s:
        if i == ' ':
            answer += i
        else: 
            a = ord(i) + n
            if (a > 122) and (ord(i) > 96) and (ord(i) < 123):
                answer += chr(a-122+96)
            elif a > 90 and ord(i) < 91 and ord(i) >64:
                answer += chr(a-90+64)
            else:
                answer += chr(a)
    return answer
```

아스키 숫자를 이용해서 풀이하였다.

소문자는 `97~122`
대문자는 `65-90` 으로 각각의 범위 내에서 벗어날 경우 차이를 계산해주었다.

다른 사람 풀이로는 아래와 같이 푼 풀이가 깔끔해보였다.
```python3
def caesar(s, n):
    s = list(s)
    for i in range(len(s)):
        if s[i].isupper():
            s[i]=chr((ord(s[i])-ord('A')+ n)%26+ord('A'))
        elif s[i].islower():
            s[i]=chr((ord(s[i])-ord('a')+ n)%26+ord('a'))

    return "".join(s)
```
[출처: programmsers - , - , 김유경]

대문자, 소문자를 구분하여 이동을 계산하여 26으로 나눈 나머지 + ord(첫문자) 를 해주어 더 간단하게 계산해주었다.

`b`라고 하고 2칸 이동하면 d가 나와야하는데 다음과 같이 계산이 가능하다. (98 - 97 + 2 ) %26 + 65 = 68 => chr(68) = d이다.
