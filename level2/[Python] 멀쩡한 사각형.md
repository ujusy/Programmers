#### **문제** 

<details>
  <summary>문제 </summary>
  <div markdown="1">
    
##### 문제 설명
    
가로 길이가 Wcm, 세로 길이가 Hcm인 직사각형 종이가 있습니다. 종이에는 가로, 세로 방향과 평행하게 격자 형태로 선이 그어져 있으며, 모든 격자칸은 1cm x 1cm 크기입니다. 이 종이를 격자 선을 따라 1cm × 1cm의 정사각형으로 잘라 사용할 예정이었는데, 누군가가 이 종이를 대각선 꼭지점 2개를 잇는 방향으로 잘라 놓았습니다. 그러므로 현재 직사각형 종이는 크기가 같은 직각삼각형 2개로 나누어진 상태입니다. 새로운 종이를 구할 수 없는 상태이기 때문에, 이 종이에서 원래 종이의 가로, 세로 방향과 평행하게 1cm × 1cm로 잘라 사용할 수 있는 만큼만 사용하기로 하였습니다.
    
가로의 길이 W와 세로의 길이 H가 주어질 때, 사용할 수 있는 정사각형의 개수를 구하는 solution 함수를 완성해 주세요.

##### 제한사항
- W, H : 1억 이하의 자연수
    
입출력 예
|W|	H|	result|
|--|--|--|    
|8|	12|	80|
    
입출력 예 설명
    
입출력 예 #1
    
가로가 8, 세로가 12인 직사각형을 대각선 방향으로 자르면 총 16개 정사각형을 사용할 수 없게 됩니다. 원래 직사각형에서는 96개의 정사각형을 만들 수 있었으므로, 96 - 16 = 80 을 반환합니다.
    ![image](https://user-images.githubusercontent.com/49120090/123585863-dccd6980-d81e-11eb-8e50-e4f7e5e7c43e.png)

</div>
</details>

#### **내 풀이** 
```python3
import math
def solution(w,h):
    answer = 0
    tmp = 0
    m = math.ceil(h/w)
    if w == 1:
        return 0
    else:
        if h%w == 0 or w%h==0:
            answer = (w*h) - (w*m)
        else: 
            for i in range(0,w):
                a = math.floor((h*i)/w)
                b = math.ceil((h*(i+1))/w)
                tmp += (b-a)
            answer = (w*h)-(tmp)
        
    return answer
```

많은 사람들이 `gcd` 최대공약수를 활용해서 풀었던데..ㅎ,,,

for문을 사용해서 `w` 길이 만큼 순회하며 각각 얼만큼의 사각형을 사용하는지 계산해서 전체에서 빼주었습니다.

이렇게 하면 1억의 수가 들어오면 시간 소요가 엄청나다는 단점이 ,,

https://leedakyeong.tistory.com/entry/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4-%EB%A9%80%EC%A9%A1%ED%95%9C-%EC%82%AC%EA%B0%81%ED%98%95-in-python

```python3
import math
def solution(w,h):        
    return w*h-(w+h-math.gcd(w,h))
```
