#### **문제** 

<details>
  <summary>문제 </summary>
  <div markdown="1">
    
##### 문제 설명
    
JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다. 문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.

##### 제한 조건
- s는 길이 1 이상인 문자열입니다.
- s는 알파벳과 공백문자(" ")로 이루어져 있습니다.
- 첫 문자가 영문이 아닐때에는 이어지는 영문은 소문자로 씁니다. ( 첫번째 입출력 예 참고 )
    
##### 입출력 예
|s|	return|
|"3people unFollowed me"|	"3people Unfollowed Me"|
|"for the last week"|	"For The Last Week"|
</div>
</details>

#### **내 풀이** 
```python3
def solution(s):
    answer = []
    s = s.split(' ')
    for i in s:
        if len(i) > 0:
            answer.append(i[0].upper() + i[1:].lower())
        else: answer.append(i)
    return ' '.join(answer)
```

공백이 여러개로 들어올 경우를 생각해주어야한다.
ex. '    a' -> '    A'

`split` 사용하면 위의 예시에서 ['', '', '', 'a'] 가 된다.

이를 돌면서 '' 일 경우는 그냥 `append` 시켜주고 문자일 경우에만 적용시켜준다.

' '.join 사용할 시 ''는 ' ' 공백으로 연결된다.
