#### **문제** 

<details>
  <summary>문제 </summary>
  <div markdown="1">
    
##### 문제 설명
2016년 1월 1일은 금요일입니다. 2016년 a월 b일은 무슨 요일일까요? 
    
두 수 a ,b를 입력받아 2016년 a월 b일이 무슨 요일인지 리턴하는 함수, solution을 완성하세요. 요일의 이름은 일요일부터 토요일까지 각각 `SUN,MON,TUE,WED,THU,FRI,SAT`

입니다. 예를 들어 a=5, b=24라면 5월 24일은 화요일이므로 문자열 "TUE"를 반환하세요.

##### 제한 조건
- 2016년은 윤년입니다.
- 2016년 a월 b일은 실제로 있는 날입니다. (13월 26일이나 2월 45일같은 날짜는 주어지지 않습니다)
    
##### 입출력 예
|a|	b|	result|
|--|--|--|    
|5|	24|	"TUE"|
</div>
</details>

#### **내 풀이**
```python3
import datetime
def solution(a, b):
    days = ['MON','TUE','WED','THU','FRI','SAT','SUN']
    return days[datetime.date(2016,a,b).weekday()]

```

`datetime`의 `weekday`를 이용하여 해결하였다. 숫자로 반환해주는데 0: 월요일 - 6: 일요일이다. 이에 맞추어 days의 리스트를 선언하였다.

외부 라이브러리를 사용하지 않고 푼 다른 풀이도 있었다.

```python3
def getDayName(a,b):
    months = [31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
    days = ['FRI', 'SAT', 'SUN', 'MON', 'TUE', 'WED', 'THU']
    return days[(sum(months[:a-1])+b-1)%7]

#아래 코드는 테스트를 위한 출력 코드입니다.
print(getDayName(5,24))
```

`출처:  - , 김세환`

깔끔한 코드인 것 같다. 요일을 계산하는 방법은 1월 1일부터 구하려는 날짜를 모두 더하여 7로 나누어준 값이 요일이다.
