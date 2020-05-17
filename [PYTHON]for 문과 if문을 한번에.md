# for문과 if문을 한번에

-------------

![image](https://user-images.githubusercontent.com/49120090/81983844-f4737e00-966e-11ea-8f86-a2ebcbb88411.png)

내 풀이

```python
def solution(mylist):
    answer = []
    for num in mylist:
        if num%2 == 0:
            answer.append(num*num)
        else:
            continue
    return answer
```



풀이:

>파이썬에서는 list comprehension을 사용하면 한 줄 안에 for문과 if문을 한 번에 처리할 수 있다. 
>
>```python
>mylist = [3, 2, 6, 7]
>answer = [ i**2 for i in mylist if i %2 == 0]
>```

