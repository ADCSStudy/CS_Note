# 배열 (Array)
### 회전 알고리즘
```python
arr = [1,2,3,4,5,6,7]

def rotate(arr, n):
    length = len(arr)
    res = [0]*length
    
    for i in range(length):
        res[(i+n)%length] = arr[i]
        
    return res
```

### Reverse the reversed
L과 R 각각을 뒤집은 뒤, 이것들을 합친 결과 전체를 다시 한 번 뒤집으면 우리가 원하는 RL이 나온다

arr = [1,2,3,4,5]

2만큼 회전

L : [1,2,3]  R : [4,5]

L’ : [3,2,1] R’ : [5,4]

L’+R’ = [3,2,1,5,4]

(L’+R’)’ = [4,5,1,2,3]

```python
def reverse_the_reversed(arr, n):
    left, right = arr[:-n], arr[-n:]
    reversed_list = list(reversed(left)) + list(reversed(right))
    return list(reversed(reversed_list))
```

### 저글링 알고리즘
<img width="712" alt="image" src="https://user-images.githubusercontent.com/76643037/190857487-7fe4f9e2-6af3-4122-9703-c9771aa5d790.png">

[배열의 길이가 회전 크기(n)의 배수인 경우]
1. T라는 변수에 arr[0] 을 저장
2. index를 0부터 n만큼 키워가면서 해당 index에 있는 값을 이전 index로 옮긴다
3→0, 6→3, 9→6
3. T에 저장한 값을 마지막 index로 옮긴다