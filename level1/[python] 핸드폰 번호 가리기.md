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
def solution(phone_number):
    answer = ''
    ph = phone_number[:-4]
    for _ in ph:
        answer += '*'
    return answer + phone_number[-4:]
```

 `phone_number[:-4]` 를 하면 뒤에서 4자리를 제외한 문자열이 추출된다. 이를 모두 `*`로 만드는 반복문을 수행한다.
 
 `*`로 된 문자열과 나머지 `phone_numver[-4:]`를 이어붙여서 출력한다.
