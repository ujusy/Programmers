#### **문제** 

<details>
  <summary>문제</summary>
  <div markdown="1">
문제 설명
수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.

##### 제한사항
마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.

completion의 길이는 participant의 길이보다 1 작습니다.

참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.

참가자 중에는 동명이인이 있을 수 있습니다.

##### 입출력 예
|participant|	completion|	return|
|--|--|--|
|["leo", "kiki", "eden"]|	["eden", "kiki"]|	"leo"|
|["marina", "josipa", "nikola", "vinko", "filipa"]|	["josipa", "filipa", "marina", "nikola"]|	"vinko"|
|["mislav", "stanko", "mislav", "ana"]|	["stanko", "ana", "mislav"]|	"mislav"|

##### 입출력 예 설명
예제 #1
"leo"는 참여자 명단에는 있지만, 완주자 명단에는 없기 때문에 완주하지 못했습니다.

예제 #2
"vinko"는 참여자 명단에는 있지만, 완주자 명단에는 없기 때문에 완주하지 못했습니다.

예제 #3
"mislav"는 참여자 명단에는 두 명이 있지만, 완주자 명단에는 한 명밖에 없기 때문에 한명은 완주하지 못했습니다.
</div>
</details>

#### **내가 푼 풀이**
```python3
def solution(participant, completion):
    dictionary = {}
    for i in participant:
        try: dictionary[i] += 1
        except: dictionary[i] = 1
    for i in completion:
        if dictionary.get(i):
            dictionary[i] += 1
    sol = {v:k for k,v in dictionary.items()}
    b = list(dictionary.values())
    for i in b:
        if i % 2 == 1:
            return sol.get(i)
```
음.. 효율성 때문에 까다로웠던 문제이다 ㅜㅜ 계속 효율성에서 점수가 안나와서 코드를 여러번 수정했다. 

딕셔너리를 이용해서 풀었다. 기본에 `participant`로 들어온 리스트를 딕셔너리로 몇명인지를 value로 설정해 주었다. 

그리고 `comletion`을 돌면서 딕셔너리에 존재하는 값이면 해당 값을 +1 해주었다. 

문제 조건을 보면 길이가 하나가 차이나고 participant의 값을 기준으로 completion에 값이 존재하면 +1씩 해주게 되면 결과적으로 하나를 제외하고는 모두 2로 나누어 떨어진다.

이를 이용해서 홀수인 경우 리턴하게 해주었다. .

#### **다른 사람이 푼 풀이**
```python3
import collections


def solution(participant, completion):
    answer = collections.Counter(participant) - collections.Counter(completion)
    return list(answer.keys())[0]
```
([출처: Programmers] 김형준 , ii , - , YoungHo Choi , 민홍 외 966 명)

풀이보고..참 파이썬은 넓고도 넓구나라는 생각이 들었다... 처음부터 `collections.counter`을 이용하여 객체(딕셔너리로) 데이터의 개수를 카운트 해준다.. 

들어온 리스트를 모두 딕셔너리 객체로 만들고 이 둘을 빼준다. 

그러면 딕셔너리 객체가 나오고 여기서 keys를 추출하여 리스트로 변환하여 반환하는 것이다..

간단하고 똑똑한 풀이인것 같다
