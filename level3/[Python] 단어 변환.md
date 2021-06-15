#### **문제** 

<details>
  <summary>문제 </summary>
  <div markdown="1">
문제 설명
두 개의 단어 begin, target과 단어의 집합 words가 있습니다. 아래와 같은 규칙을 이용하여 begin에서 target으로 변환하는 가장 짧은 변환 과정을 찾으려고 합니다.

1. 한 번에 한 개의 알파벳만 바꿀 수 있습니다.
2. words에 있는 단어로만 변환할 수 있습니다.
예를 들어 begin이 "hit", target가 "cog", words가 ["hot","dot","dog","lot","log","cog"]라면 "hit" -> "hot" -> "dot" -> "dog" -> "cog"와 같이 4단계를 거쳐 변환할 수 있습니다.

두 개의 단어 begin, target과 단어의 집합 words가 매개변수로 주어질 때, 최소 몇 단계의 과정을 거쳐 begin을 target으로 변환할 수 있는지 return 하도록 solution 함수를 작성해주세요.

##### 제한사항
- 각 단어는 알파벳 소문자로만 이루어져 있습니다.
- 각 단어의 길이는 3 이상 10 이하이며 모든 단어의 길이는 같습니다.
- words에는 3개 이상 50개 이하의 단어가 있으며 중복되는 단어는 없습니다.
- begin과 target은 같지 않습니다.
- 변환할 수 없는 경우에는 0를 return 합니다.
    
##### 입출력 예
|begin|	target|	words|	return|
|--|--|--|--|   
|"hit"|	"cog"|	["hot", "dot", "dog", "lot", "log", "cog"]|	4|
|"hit"|	"cog"|	["hot", "dot", "dog", "lot", "log"]|	0|
##### 입출력 예 설명
예제 #1
문제에 나온 예와 같습니다.

예제 #2
target인 "cog"는 words 안에 없기 때문에 변환할 수 없습니다.
</div>
</details>

#### **내 풀이** 
```python3
def dfs(words, begin, target, visited):
    count = 0
    stack = []
    stack.append(begin)
    while stack:
        v = stack.pop()
        if v == target:
            return count
        for i in range(len(words)):
            a = list(v)
            b = list(words[i])
            diff = 0
            for j in range(len(a)):
                if a[j] != b[j]:
                    diff += 1
            if diff == 1 and visited[i] == False:
                visited[i] = True
                stack.append(words[i])
        count += 1
        
def solution(begin, target, words):
    answer = 0
    visited = [False] * len(words)
    if target not in words:
        return 0
    answer = dfs(words, begin, target, visited)
    return answer
```

dfs를 이용하여 코드를 작성하였고 알파벳 중 하나만 달라야한다는 조건에서는

비교할 문자를 리스트로 만들어 순회하면서 일치 여부를 판단하였다.

좀더 좋은 방법이 없을까 고민을 많이 해보았는데 difflib라는 외부라이브러리를 사용하기에는 오버헤드가 크다고 판단되어 for문으로 대체하였다.

#### **다른 사람 풀이**
```python3
for c, w in zip(current, word):
            if c != w:
                count += 1
```

문자열을 비교한 부분만 참고하였다.

`zip`을 사용하여 비교할 문자열 두 개를 tuple로 만들어 주었고 이를 반복을 통해 비교하였다.

![image](https://user-images.githubusercontent.com/49120090/122002921-5449d480-cded-11eb-9fd3-26556d69493f.png)
