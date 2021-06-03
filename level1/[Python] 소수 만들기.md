## 문제

###### 문제 설명

주어진 숫자 중 3개의 수를 더했을 때 소수가 되는 경우의 개수를 구하려고 합니다. 숫자들이 들어있는 배열 nums가 매개변수로 주어질 때, nums에 있는 숫자들 중 서로 다른 3개를 골라 더했을 때 소수가 되는 경우의 개수를 return 하도록 solution 함수를 완성해주세요.

##### 제한사항

- nums에 들어있는 숫자의 개수는 3개 이상 50개 이하입니다.
- nums의 각 원소는 1 이상 1,000 이하의 자연수이며, 중복된 숫자가 들어있지 않습니다.

------

##### 입출력 예

| nums        | result |
| ----------- | ------ |
| [1,2,3,4]   | 1      |
| [1,2,7,6,4] | 4      |

##### 입출력 예 설명

```
입출력 예 #1
[1,2,4]를 이용해서 7을 만들 수 있습니다.

입출력 예 #2
[1,2,4]를 이용해서 7을 만들 수 있습니다.
[1,4,6]을 이용해서 11을 만들 수 있습니다.
[2,4,7]을 이용해서 13을 만들 수 있습니다.
[4,6,7]을 이용해서 17을 만들 수 있습니다.
```



## 내 풀이

```python
from itertools import combinations
import math

def check_prime(number):
    if number == 0 or number == 1:
        return False
    a = int(math.sqrt(number))
    for i in range(2, a+1):
        if number%i == 0:
            return False
    return True
    
    
def solution(nums):
    answer = 0
    sample_list = list(combinations(nums, 3))
    for i in sample_list:
        if check_prime(sum(i)):
            answer += 1
    return answer
```



해당 문제를 풀기위해서는 모든 경우의 수를 알아야했다. 모든 경우의 수를 알고 그 수의 합의 소수를 판별하는 로직으로 구현하였다.

- 모든 경우의 수를 알아내기 위해 `combinations` 를 사용했다. 
- 소수 판별은 다음과 같은 방법을 사용했다.
  - `n` 을 소수 판별하기 위해서 `sqrt(n)` 까지의 수로 `n` 을 나누었을 때 1을 제외하고 나누어지지 않으면 소수로 판별하였다.
