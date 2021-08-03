#### **문제** 

<details>
  <summary>문제 </summary>
  <div markdown="1">
    
##### 문제 설명
한자리 숫자가 적힌 종이 조각이 흩어져있습니다. 흩어진 종이 조각을 붙여 소수를 몇 개 만들 수 있는지 알아내려 합니다.

각 종이 조각에 적힌 숫자가 적힌 문자열 numbers가 주어졌을 때, 종이 조각으로 만들 수 있는 소수가 몇 개인지 return 하도록 solution 함수를 완성해주세요.

##### 제한사항
- numbers는 길이 1 이상 7 이하인 문자열입니다.
- numbers는 0~9까지 숫자만으로 이루어져 있습니다.
- "013"은 0, 1, 3 숫자가 적힌 종이 조각이 흩어져있다는 의미입니다.
    
##### 입출력 예
|numbers|	return|
|--|--|    
|"17"|	3|
|"011"|	2|
    
##### 입출력 예 설명
예제 #1
[1, 7]으로는 소수 [7, 17, 71]를 만들 수 있습니다.

예제 #2
[0, 1, 1]으로는 소수 [11, 101]를 만들 수 있습니다.

11과 011은 같은 숫자로 취급합니다.
</div>
</details>

#### **내 풀이** 
```python3
from itertools import permutations

def prime(n):
    for i in range(2, int(n**(0.5))+1):
        if n%i ==0:
            return False
    return True

def solution(numbers):
    answer = 0
    count = 0
    tmp = []
    for a in range(len(numbers)):
        for i in permutations(numbers,a+1):
            num = int(''.join(i))
            if num==0 or num==1:
                continue
            tmp.append(int(''.join(i)))
    tmp = list(set(tmp))
    
    for i in tmp:
        if prime(i) == True:
            answer +=1
    return answer
```

`prime` 함수를 소수를 판별하는 함수도 두었다. 모든 조합의 경우에 대해 판별해야하므로 `permutation`을 사용해 주었고 길이가1, 2,~ 들어온 `nubmers`의 길이 만큼 까지의 조합을 구한다.

중복되는 조합을 `set`을 통해 삭제하고 소수 판별을한다. 

소수 판별 할 때 int(n**(0.5))하고 +1을 안해줘서 실패했었는데 주의해야겠다.,,

##### 다른 사람 풀이
```python3
primeSet = set()


def isPrime(number):
    if number in (0, 1):
        return False
    for i in range(2, number):
        if number % i == 0:
            return False

    return True


def makeCombinations(str1, str2):
    if str1 != "":
        if isPrime(int(str1)):
            primeSet.add(int(str1))

    for i in range(len(str2)):
        makeCombinations(str1 + str2[i], str2[:i] + str2[i + 1:])


def solution(numbers):
    makeCombinations("", numbers)

    answer = len(primeSet)

    return answer
```
[출처: 프로그래머스 Jinsu Lim , hello2jolee]

외부 라이브러리를 사용하지 않고 재귀를 사용해서 풀이했는데 코드가 워낙 깔끔해서 가져와보았다.

`makeCombinations` 함수에서 모든 조합의 경우를 생각해준다. 이 방법...생각 잠깐 스치기만 했는데 구현이 쉽지 않아서 `permutation`을 사용하였는데 너무 깔끔하게 작성해주신 것 같다.

`123` 이 들어올 경우 `1,23`-> `12,3` -> `123,0` 
`2,13` , `3, 12` 일 경우도 마찬가지이다.

