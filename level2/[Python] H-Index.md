#### **문제** 

<details>
  <summary>문제 </summary>
  <div markdown="1">
문제 설명
H-Index는 과학자의 생산성과 영향력을 나타내는 지표입니다. 어느 과학자의 H-Index를 나타내는 값인 h를 구하려고 합니다. 위키백과1에 따르면, H-Index는 다음과 같이 구합니다.

어떤 과학자가 발표한 논문 n편 중, h번 이상 인용된 논문이 h편 이상이고 나머지 논문이 h번 이하 인용되었다면 h의 최댓값이 이 과학자의 H-Index입니다.

어떤 과학자가 발표한 논문의 인용 횟수를 담은 배열 citations가 매개변수로 주어질 때, 이 과학자의 H-Index를 return 하도록 solution 함수를 작성해주세요.

제한사항
- 과학자가 발표한 논문의 수는 1편 이상 1,000편 이하입니다.
- 논문별 인용 횟수는 0회 이상 10,000회 이하입니다.
    
##### 입출력 예
|citations|	return|
|----|----|
|[3, 0, 6, 1, 5]|	3|
    
##### 입출력 예 설명
이 과학자가 발표한 논문의 수는 5편이고, 그중 3편의 논문은 3회 이상 인용되었습니다. 
    
그리고 나머지 2편의 논문은 3회 이하 인용되었기 때문에 이 과학자의 H-Index는 3입니다.
</div>
</details>

#### **내 풀이** 
```python3
def solution(citations):
    h = sum(citations) // len(citations)
    count_up = 0
    for i in citations:
        if i >= h:
            count_up += 1
    while count_up < h:
        h = h - 1
        n = citations.count(h)
        count_up = count_up + n
    return h
```
주어진 내용에서 가장 중요한 조건은 **논문 n편 중, h번 이상 인용된 논문이 h편 이상** 이라고 생각하여 해당 부분을 중점으로 코드를 작성했다. 논문의 인용 평균을 h라고 하고 h번 이상 인용된 논문이 h편 이상이 아닐 경우 

h 를 1씩 감소하면서 n편 중 줄어든 h번 이상 인용된 논문의 수를 count_up에 더해주면서 count_up이 h번 이상일 수 있도록 구현하였다.

#### **다른 사람 풀이**
```python3
def solution(citations):
    citations.sort(reverse=True)
    answer = max(map(min, enumerate(citations, start=1)))
    return answer
```
[출처] Gwon Seonggwang , 김성근 , 전복오리백숙 , 하윤아빠 , MyungHoon-Jin 외 127 명

개인적으로 신기했던 풀이이다. 먼저 들어온 리스트를 내림차순으로 정렬한다.

enumrate를 start 인덱스를 1로 하여 문제의 예시를 출력해보면
```
1 6
2 5
3 3
4 1
5 0
```
으로 나온다. 이를 각 튜플의 최소값으로 매핑시킨다. 그러면 (1,6)일 경우 1, (2,5)일 경우 2 이렇게 하여 map을 하면 [1, 2, 3, 1, 0] 나온다. 이 중에서 가장 큰 값을 반환하면 된다. 
그렇게 되면 무조건 max값 이상일 수 있다.
