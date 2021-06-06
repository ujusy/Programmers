#### **문제** 

<details>
  <summary>접기/펼치기 버튼</summary>
  <div markdown="1">
문제 설명
일반적인 프린터는 인쇄 요청이 들어온 순서대로 인쇄합니다. 그렇기 때문에 중요한 문서가 나중에 인쇄될 수 있습니다. 이런 문제를 보완하기 위해 중요도가 높은 문서를 먼저 인쇄하는 프린터를 개발했습니다. 이 새롭게 개발한 프린터는 아래와 같은 방식으로 인쇄 작업을 수행합니다.

1. 인쇄 대기목록의 가장 앞에 있는 문서(J)를 대기목록에서 꺼냅니다.
2. 나머지 인쇄 대기목록에서 J보다 중요도가 높은 문서가 한 개라도 존재하면 J를 대기목록의 가장 마지막에 넣습니다.
3. 그렇지 않으면 J를 인쇄합니다.
예를 들어, 4개의 문서(A, B, C, D)가 순서대로 인쇄 대기목록에 있고 중요도가 2 1 3 2 라면 C D A B 순으로 인쇄하게 됩니다.

내가 인쇄를 요청한 문서가 몇 번째로 인쇄되는지 알고 싶습니다. 위의 예에서 C는 1번째로, A는 3번째로 인쇄됩니다.

현재 대기목록에 있는 문서의 중요도가 순서대로 담긴 배열 priorities와 내가 인쇄를 요청한 문서가 현재 대기목록의 어떤 위치에 있는지를 알려주는 location이 매개변수로 주어질 때, 내가 인쇄를 요청한 문서가 몇 번째로 인쇄되는지 return 하도록 solution 함수를 작성해주세요.

제한사항
    
현재 대기목록에는 1개 이상 100개 이하의 문서가 있습니다.
    
인쇄 작업의 중요도는 1~9로 표현하며 숫자가 클수록 중요하다는 뜻입니다.
    
location은 0 이상 (현재 대기목록에 있는 작업 수 - 1) 이하의 값을 가지며 대기목록의 가장 앞에 있으면 0, 두 번째에 있으면 1로 표현합니다.
    
    
##### 입출력 예
|priorities	|location|	return|
|--|--|--|
|[2, 1, 3, 2]	|2|	1|
|[1, 1, 9, 1, 1, 1]	|0|	5|
    
입출력 예 설명
    
##### 예제 #1

문제에 나온 예와 같습니다.

##### 예제 #2

6개의 문서(A, B, C, D, E, F)가 인쇄 대기목록에 있고 중요도가 1 1 9 1 1 1 이므로 C D E F A B 순으로 인쇄합니다.
</div>
</details>

#### **내 풀이** 

- 문제 푸는데 한 시간 걸렸다.. ㅜㅜ
- 일단 문제를 이해하는데 시간이 오래걸렸다. 
- 예시로 [3,1,5,2], 3 이라고 해보면 [5,3,2,1] 이 될때가지 문제의 조건을 반복해야하고, 이 때의 location 3을 반환해야한다.
- 내 풀이는 경우를 통합하지 않고 주먹구구식의 느낌이 강한데 다른 사람의 풀이는 queue를 적절하게 사용하여 통일성 있게 구현하였다...(반성..ㅜ)
```python3
def solution(priorities, location):
    length = len(priorities)
    count = 0
    while True: // 계속 반복 
        a = priorities[1:] // 첫 번째 원소를 제외하고 파싱
        if(len(a)==0): // 파싱한 부분이 빈 배열이면 리턴
            return location + 1
        if count == location and max(a) <= priorities[0]: // 파싱한 배열에 더 이상 첫 번째 원소보다 큰 값이 없으면 리턴
            return location + 1
        if max(a) > priorities[0]: 
            tmp = priorities.pop(0)
            priorities.append(tmp)
            if location == 0 or count == location:
                location = length - 1
            else:
                 location -= 1
        else:
            priorities.pop(0)
            count += 1
    return location + 1
```

#### **프로그래머스의 다른 사람 풀이** 
- 이 풀이를 보고서 감탄했다..ㅋㅋ
- `enumerate`를 이용하여 인덱스와 원소를 저장해주었다.
- 첫 원소를 pop하고 `any`를 이용하여 남아있는 원소보다 작다면 `pop`한 원소를 뒤로 `append` 시켜주었다.
- 만약 크다면 answer을 더해주고 pop한 원소의 인덱스와 `location`이 같다면 답을 반환해준다.

```python3
def solution(priorities, location):
    queue =  [(i,p) for i,p in enumerate(priorities)]
    answer = 0
    while True:
        cur = queue.pop(0)
        if any(cur[1] < q[1] for q in queue):
            queue.append(cur)
        else:
            answer += 1
            if cur[0] == location:
                return answer
```
