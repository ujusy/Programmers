#### **문제** 

<details>
  <summary>접기/펼치기 버튼</summary>
  <div markdown="1">
    문제 설명
    
  단어 s의 가운데 글자를 반환하는 함수, solution을 만들어 보세요. 단어의 길이가 짝수라면 가운데 두글자를 반환하면 됩니다.

  제한사항
  s는 길이가 1 이상, 100이하인 스트링입니다.

  입출력 예
    
  |s|	return|
  |--|--|
  |"abcde"|	"c"|
  |"qwer"|	"we"|
</div>
</details>

#### **내가 푼 풀이**

몫과 나머지를 이용하여 리스트를 slice 하였다.

a = [1,2,3,4,5]


a[1:2] 는 [2] 이다.

```python
def solution(s):
    s_list = list(s)
    a = len(s) // 2
    b = len(s) % 2
    if(b==0):
        return s[a-1:a+1]
    return s[a]
```
