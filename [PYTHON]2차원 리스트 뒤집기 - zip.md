# [PYTHON]2차원 리스트 뒤집기 - zip

-----------

>[case1]
>
>```zip``` : 각 iterables의 교소들을 모으는 이터레이터를 만든다. 튜플의 이터레이터를 돌려주는데, i 번 째 튜플은 각 인자로 전달된 시퀀스나 이터러블의 i 번째 요소를 포함한다.
>
>~~~python
>mylist = [ [1,2,3], [4,5,6], [7,8,9] ]
>new_list = list(map(list, zip(*mylist)))
>~~~

