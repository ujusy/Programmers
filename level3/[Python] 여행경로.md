#### **문제** 

<details>
  <summary>문제 </summary>
  <div markdown="1">
문제 설명
주어진 항공권을 모두 이용하여 여행경로를 짜려고 합니다. 항상 "ICN" 공항에서 출발합니다.

항공권 정보가 담긴 2차원 배열 tickets가 매개변수로 주어질 때, 방문하는 공항 경로를 배열에 담아 return 하도록 solution 함수를 작성해주세요.

##### 제한사항
- 모든 공항은 알파벳 대문자 3글자로 이루어집니다.
- 주어진 공항 수는 3개 이상 10,000개 이하입니다.
- tickets의 각 행 [a, b]는 a 공항에서 b 공항으로 가는 항공권이 있다는 의미입니다.
- 주어진 항공권은 모두 사용해야 합니다.
- 만일 가능한 경로가 2개 이상일 경우 알파벳 순서가 앞서는 경로를 return 합니다.
- 모든 도시를 방문할 수 없는 경우는 주어지지 않습니다.
##### 입출력 예
|tickets|	return|
|--|--|    
|[["ICN", "JFK"], ["HND", "IAD"], ["JFK", "HND"]]|	["ICN", "JFK", "HND", "IAD"]|
|[["ICN", "SFO"], ["ICN", "ATL"], ["SFO", "ATL"], ["ATL", "ICN"], ["ATL","SFO"]]|	["ICN", "ATL", "ICN", "SFO", "ATL", "SFO"]|
##### 입출력 예 설명
예제 #1

["ICN", "JFK", "HND", "IAD"] 순으로 방문할 수 있습니다.

예제 #2

["ICN", "SFO", "ATL", "ICN", "ATL", "SFO"] 순으로 방문할 수도 있지만 ["ICN", "ATL", "ICN", "SFO", "ATL", "SFO"] 가 알파벳 순으로 앞섭니다.
</div>
</details>

#### **내 풀이** 
```python3
def dfs(tickets, visited):
    path = []
    tickets.sort()
    stack = ['ICN']
    while stack:
        v = stack[-1]
        c = 0
        for i in range(len(tickets)):
            if tickets[i][0] == v and visited[i] == False:
                visited[i] = True
                stack.append(tickets[i][1])
                c +=1
                break
        if c == 0:
            a = stack.pop()
            path.append(a)
    path = list(reversed(path))
    return path

def solution(tickets):
    visited = [False] * len(tickets)
    answer = dfs(tickets, visited)
    return answer
```

stack을 사용해 구현했다. 알파벳 순서가 앞에 있는 경로가 우선적으로 return 되므로 tickets 를 sort로 정렬 후 진행하였다.

stack 리스트에 있는 마지막 원소와 연결될 수 있는 원소가 있으면 알파벳 순서가 앞에 있는 원소를 append 시켜주고 visited를 True로 바꿔준다.

만약 stack 리스트에 있는 마지막 원소가 연결될 수 있는 원소가 없으면 pop시켜주고 path 리스트에 넣어준다.

이렇게 되면 path에 알파벳 순서가 가장 뒤인 것부터 연결되는 경로가 나온다.

path를 역순으로 출력해보면 알파벳 순서가 가장 앞 부터 방문하는 경로가 나온다.
