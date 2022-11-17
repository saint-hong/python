# np.in1d()
- `np.in1d(ar1, ar2, assume_unique=False, invert=False)`
- `discription`

```
Returns a boolean array the same length as `ar1` that is True
where an element of `ar1` is in `ar2` and False otherwise.
```
- `반환값`
    - ar1과 같은 크기의 배열을 반환한다.
    - ar1 중에서 ar2에 있는 것은 True, 없는 것은 False
- **카테고리값을 인덱싱할 때 유용함**

### 리스트 자료형 생성

```python
test = [1, 2, 3, 4, 5, 6, 7]
test

>>> print

[1, 2, 3, 4, 5, 6, 7]
```

### 실행
- test 중에서 [1, 2] 에 있는 것 True, 없는 것 False 반환

```python
idx = np.in1d(test, [1, 2])
idx

>>> print

array([ True,  True, False, False, False, False, False])
```

### 배열 랜덤 데이터 생성

```python
import random

test = np.array([random.randint(1, 10) for _ in range(20)])
test

>>> print

array([ 6,  1,  1,  5, 10,  6,  6,  9,  6,  3,  4,  6,  5,  2,  2,  6,  8,
        2,  9, 10])
```

### 실행

```python
num_lst = [2, 8, 5]
idx = np.in1d(test, num_lst)
idx

>>> print

array([False, False, False,  True, False, False, False, False, False,
       False, False, False,  True,  True,  True, False,  True,  True,
       False, False])
```

### 불리언 값을 사용하여 데이터 인덱싱
- 넘파이의 배열인 경우에만 사용 가능하다.

```python
test[idx]

>>> print

array([5, 5, 2, 2, 8, 2])
```

### 붓꽃 데이터의 종속변수로 테스트
- 0과 2 클래스만 선택한다.

```python
from sklearn.datasets import load_iris

iris = load_iris()
y = iris.target
y

>>> print

array([0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
       0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
       0, 0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,
       1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,
       1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2,
       2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2,
       2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2])
```

```python
idx = np.in1d(iris.target, [0, 2])
idx

>>> print

array([ True,  True,  True,  True,  True,  True,  True,  True,  True,
        True,  True,  True,  True,  True,  True,  True,  True,  True,
        True,  True,  True,  True,  True,  True,  True,  True,  True,
        True,  True,  True,  True,  True,  True,  True,  True,  True,
        True,  True,  True,  True,  True,  True,  True,  True,  True,
        True,  True,  True,  True,  True, False, False, False, False,
       False, False, False, False, False, False, False, False, False,
       False, False, False, False, False, False, False, False, False,
       False, False, False, False, False, False, False, False, False,
       False, False, False, False, False, False, False, False, False,
       False, False, False, False, False, False, False, False, False,
       False,  True,  True,  True,  True,  True,  True,  True,  True,
        True,  True,  True,  True,  True,  True,  True,  True,  True,
        True,  True,  True,  True,  True,  True,  True,  True,  True,
        True,  True,  True,  True,  True,  True,  True,  True,  True,
        True,  True,  True,  True,  True,  True,  True,  True,  True,
        True,  True,  True,  True,  True,  True])
```

- 불리언으로 인덱싱

```python
new_y = iris.target[idx]
new_y

>>> print

array([0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
       0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
       0, 0, 0, 0, 0, 0, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2,
       2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2,
       2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2])
```

