#### **문제** 

<details>
  <summary>문제 </summary>
  <div markdown="1">
    
##### 문제 설명

전화번호부에 적힌 전화번호 중, 한 번호가 다른 번호의 접두어인 경우가 있는지 확인하려 합니다.
    
전화번호가 다음과 같을 경우, 구조대 전화번호는 영석이의 전화번호의 접두사입니다.

- 구조대 : 119
- 박준영 : 97 674 223
- 지영석 : 11 9552 4421
    
전화번호부에 적힌 전화번호를 담은 배열 phone_book 이 solution 함수의 매개변수로 주어질 때, 어떤 번호가 다른 번호의 접두어인 경우가 있으면 false를 그렇지 않으면 true를 return 하도록 solution 함수를 작성해주세요.

##### 제한 사항
- phone_book의 길이는 1 이상 1,000,000 이하입니다.
- 각 전화번호의 길이는 1 이상 20 이하입니다.
- 같은 전화번호가 중복해서 들어있지 않습니다.
    
##### 입출력 예제
|phone_book|	return|
|--|--|    
|["119", "97674223", "1195524421"]|	false|
|["123","456","789"]|	true|
|["12","123","1235","567","88"]	|false|
    
##### 입출력 예 설명
입출력 예 #1
앞에서 설명한 예와 같습니다.

입출력 예 #2
한 번호가 다른 번호의 접두사인 경우가 없으므로, 답은 true입니다.

입출력 예 #3
첫 번째 전화번호, “12”가 두 번째 전화번호 “123”의 접두사입니다. 따라서 답은 false입니다.
</div>
</details>

#### **내 풀이** 
```python3
def checkDuplicate(str1, strList, index):
    for i in range(index+1,len(strList)):
        if str1 == strList[i][:len(str1)]:
            return False
        return True

def solution(p):
    p = sorted(p)
    for i in range(len(p)):
        re = checkDuplicate(p[i],p,i)
        if re == False:
            return False
    return True
```

처음에 `copy` 를 사용하여 깊은 복사를 하여 checkDuplicate에 인자로 넘겨주어 자신을 제외한 나머지 모두를 비교하는 식으로 했다. 

그렇게 하니 정확성은 통과했으나 효율성 두 가지를 통과하지 못했다..ㅜ

효율성을 통과하기 위해어 먼저 들어온 리스트를 `sort` 해주었다. 문자열을 정렬해주면 동일한 접두어 순서대로 정렬되게된다.

그렇게 되면 비교하려는 접두사가 그 다음 요소에 존재하지 않을 시 그 이후의 문자열의 접두사일 수 없는 것이다. 

따라서 `checkDuplicate` 에서 들어온 문자 이후로만 체크하고 해당 문자의 다음 문자와 체크했을시 접두사가 아니면 True를 바로 리턴하도록 해주었다..

##### 다른 사람 풀이
```python3
def solution(phoneBook):
    phoneBook = sorted(phoneBook)

    for p1, p2 in zip(phoneBook, phoneBook[1:]):
        if p2.startswith(p1):
            return False
    return True
```

[출처: 프로그래머스 Ryan , - , - , Dolpario , - 외 311 명]

`sorted` 를 해서 동일한 접두사를 가진 문자열 순서대로 만들어준다.

이후 `zip`을 사용해서 병렬로 처리해준다.

`startwith` 라는 메서드를 활용해주어 접두사인지를 판단한다. 해당 메서드를 사용해 주어 훨씬 깔끔하게 코드를 작성해주었다.
