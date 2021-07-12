#### **문제** 

<details>
  <summary>문제 </summary>
  <div markdown="1">
    
##### 문제 설명
    
프로그래머스 모바일은 개인정보 보호를 위해 고지서를 보낼 때 고객들의 전화번호의 일부를 가립니다.
    
전화번호가 문자열 phone_number로 주어졌을 때, 전화번호의 뒷 4자리를 제외한 나머지 숫자를 전부 *으로 가린 문자열을 리턴하는 함수, solution을 완성해주세요.

##### 제한 조건
- s는 길이 4 이상, 20이하인 문자열입니다.
    
##### 입출력 예
|phone_number|	return|
|--|--|    
|"01033334444"|	"*******4444"|
|"027778888"|	"*****8888"|
</div>
</details>


#### **내 풀이**
```python3
def solution(s):
    answer = []
    word = {'zero': '0', 'one': '1', 'two':'2', 'three': '3', 'four': '4', 'five':'5', 'six':'6', 'seven': '7', 'eight': '8', 'nine': '9'}
    tmp = ''
    for i in s:
        if i.isdigit():
            answer.append(str(i))
        else:
            tmp += i
            if tmp in word:
                answer.append(word[tmp])
                tmp = ''
    return int(''.join(answer))
```

`word`라는 딕셔너리를 생성하고 s를 순회하면서 숫자면 answer에 바로 붙여준다.
 
 숫자가 아니라면 tmp 문자열에 계속 추가해주고 추가된 문자열이 `word`에 `key`가 존재할 때 해당 `key`의 `value`를 `answer`에 붙여준다.
 
 다른 사람들이 풀이한 것을 보니
 ```python3
 num_dic = {"zero":"0", "one":"1", "two":"2", "three":"3", "four":"4", "five":"5", "six":"6", "seven":"7", "eight":"8", "nine":"9"}

def solution(s):
    answer = s
    for key, value in num_dic.items():
        answer = answer.replace(key, value)
    return int(answer)
 ```
 
 [출처: programmers  dannyldj]
 
s에서 `num_dic`의 `key`와 일치하는 것들을 모두 교체해주었다.
