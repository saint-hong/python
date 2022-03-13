# np.where

### 기본 사용
- 넘파이의 배열의 요소들을 조건에 부합하는지 확인하고, 조건에 따라서 출력해준다.
- np.where(condition, x, y) : condition이 맞으면 x, 틀리면 y를 출력

```python
a = [1, 2, 6, 11, 23]
for i in a :
    print(i, ":", np.where(i < 10, i, i*10))   # i가 10보다 작으면 i를 출력, i가 10보다 크면 i*10 을 출력

=====<print>=====

1 : 1
2 : 2
6 : 6
11 : 110
23 : 230
```

- 다른 예시

```python
test_x = np.linspace(0, 10, 11)
test_x

=====<print>=====

array([ 0.,  1.,  2.,  3.,  4.,  5.,  6.,  7.,  8.,  9., 10.])
```

- 5 이상이면 값을 그대로 반환하고, 5보다 작으면 'x' 를 반환

```python
np.where(test_x>=5, test_x, 'x')

=====<print>====

array(['x', 'x', 'x', 'x', 'x', '5.0', '6.0', '7.0', '8.0', '9.0', '10.0'],
      dtype='<U32')
```

### np.where() 에 여러가지 조건을 사용하는 방법

#### AND 조건

- 2이상, 6이하
- & 기호 사용

``` python
test_x[np.where((test_x>=2)&(test_x<=6))]

=====<print>=====

array([2., 3., 4., 5., 6.])
```

- np.logical_and() 함수를 사용하여 나타낼 수 있음

```python
test_x[np.where(np.logical_and(test_x>=2, test_x<=6))]

=====<print>=====

array([2., 3., 4., 5., 6.])
```

### OR 조건
- 3보다 작거나, 8보다 큰 수 반환
- | 기호 사용

```python
test_x[np.where((test_x<3) | (test_x>8))]

=====<print>=====

array([ 0.,  1.,  2.,  9., 10.])
```

- np.logical_or() 함수를 사용하여 나타낼 수 있음

```python
test_x[np.where(np.logical_or(test_x<3, test_x>8))]

=====<print>=====

array([ 0.,  1.,  2.,  9., 10.])
```

