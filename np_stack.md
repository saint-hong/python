# numpy의 stack 함수
- 배열을 이어 붙여주는 기능
- `np.hstack([a, b]) 또는 ((a, b))` : 행 갯수 일치 : 배열을 행 기준으로 이어 붙여준다.
    - **하나의 열벡터로 만들어준다.**
- `np.vstack([a, b]) 또는 ((a, b)`) : 열 갯수 일치 : 배열을 열 기준으로 이어 붙여준다.
    - **a, b가 각각 하나의 행이되어, 행렬로 만들어준다.**
- `np.column_stack([a, b]) 또는 ((a, b))` : 배열에 컬럼을 추가해준다., 행의 갯수가 일치해야 한다. 

### hstack
- 행의 갯수가 일치해야 한다.
- 같은 행 인덱스끼리 합해준다.
    - 열의 갯수가 늘어난다.

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print("a : ", a)
print("============")
print("b : ", b)
ab_hstack = np.hstack([a, b])
print("===hstack===")
print(ab_hstack)
print("shape : ", ab_hstack.shape)

```

```
=====<print>=====

a :  [1 2 3]
============
b :  [4 5 6]
===hstack===
[1 2 3 4 5 6]
shape :  (6,)
```

- 1X3 배열과 1X5 배열

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6, 7, 8])

print("a : ", a)
print("============")
print("b : ", b)
ab_hstack = np.hstack([a, b])
print("===hstack===")
print(ab_hstack)
print("shape : ", ab_hstack.shape)
```

```
=====<print>=====

a :  [1 2 3]
============
b :  [4 5 6 7 8]
===hstack===
[1 2 3 4 5 6 7 8]
shape :  (8,)
```

- 2X3 배열과 2X2 배열

```python
aa = np.array([[1, 2, 3], [4, 5, 6]])
bb = np.array([[0, 0], [7, 7]])

print(aa)
print("------------")
print(bb)
print("===hstack===")
aabb_hstack = np.hstack([aa, bb])
print(aabb_hstack)
print("===hstack shape===")
print(aabb_hstack.shape)
```

```
=====<print>=====

[[1 2 3]
 [4 5 6]]
------------
[[0 0]
 [7 7]]
===hstack===
[[1 2 3 0 0]
 [4 5 6 7 7]]
===hstack shape===
(2, 5)
```

- 2X2 배열과 1X2 배열 : 열의 갯수가 다르면 hstack을 사용할 수 없다.

```python
a = np.array([[1,2], [3,4]])
b = np.array([0, 0])
print("a : ", a)
print("============")
print("b : ", b)
ab_hstack = np.hstack([a, b])
print("===hstack===")
print(ab_hstack)
print("shape : ", ab_hstack.shape)
```

```
=====<print>=====

a :  [[1 2]
 [3 4]]
============
b :  [0 0]
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
C:\Users\Public\Documents\ESTsoft\CreatorTemp/ipykernel_28392/1998830177.py in <module>
      4 print("============")
      5 print("b : ", b)
----> 6 ab_hstack = np.hstack([a, b])
      7 print("===hstack===")
      8 print(ab_hstack)

<__array_function__ internals> in hstack(*args, **kwargs)

C:\DS\Anaconda3\lib\site-packages\numpy\core\shape_base.py in hstack(tup)
    343         return _nx.concatenate(arrs, 0)
    344     else:
--> 345         return _nx.concatenate(arrs, 1)
    346
    347

<__array_function__ internals> in concatenate(*args, **kwargs)

ValueError: all the input arrays must have same number of dimensions, but the array at index 0 has 2 dimension(s) and the array at index 1 has 1 dimension(s)

```

### vstack
- 열의 갯수가 일치해야 한다.
- 행이 되어 합해진다.
- 2X3 배열과 1X3 배열

```python
aa = np.array([[1, 2, 3], [4, 5, 6]])
bb = np.array([[0, 0, 0]])

print(aa)
print("------------")
print(bb)
print("===vstack===")
aabb_vstack = np.vstack([aa, bb])
print(aabb_vstack)
print("===vstack shape===")
print(aabb_vstack.shape)
```

```
=====<print>====
[[1 2 3]
 [4 5 6]]
------------
[[0 0 0]]
===vstack===
[[1 2 3]
 [4 5 6]
 [0 0 0]]
===vstack shape===
(3, 3)
```

- 1X3 배열과 2X3 배열

```python
aa = np.array([1, 2, 3])
bb = np.array([[0, 0, 0], [1, 1, 2]])

print(aa)
print("------------")
print(bb)
print("===vstack===")
aabb_vstack = np.vstack([aa, bb])
print(aabb_vstack)
print("===vstack shape===")
print(aabb_vstack.shape)
```

```
=====<print>=====

[1 2 3]
------------
[[0 0 0]
 [1 1 2]]
===vstack===
[[1 2 3]
 [0 0 0]
 [1 1 2]]
===vstack shape===
(3, 3)
```

### column_stack
- 열 갯수가 일치해야 한다.
- 행렬에 행이 추가 되는 방식
- hstack 과 같은 결과가 나온다.
- 2X3 배열과 2X1 배열

```python
aa = np.array([
    [1, 2, 3],
    [4, 5, 6]])
bb = np.array([[0], [0]])

print(aa)
print("------------")
print(bb)
print("===column_stack===")
aabb_col_stack = np.column_stack([aa, bb])
print(aabb_col_stack)
print("===column_stack shape===")
print(aabb_col_stack.shape)
print("===hstack===")
print(np.hstack((aa, bb)))
```

```
=====<print>=====

[[1 2 3]
 [4 5 6]]
------------
[[0]
 [0]]
===column_stack===
[[1 2 3 0]
 [4 5 6 0]]
===column_stack shape===
(2, 4)
===hstack===
[[1 2 3 0]
 [4 5 6 0]]
```

## np.vstack()과 np.hstack() 비교

### 분류용 가상 데이터 생성

```python
from sklearn.datasets import make_classification

X, y = make_classification(n_samples=16, n_features=2, n_informative=2,
                          n_redundant=0, random_state=0)
```

### 독립변수 X
- 16 X 2 행렬

```python
X

>>> print

array([[ 2.03418291, -0.38437236],
       [ 4.06377686,  0.17863836],
       [ 0.41966783, -1.38206096],
       [-1.27225991,  0.6600493 ],
       [-0.81664689,  1.16942291],
       [-0.3892691 , -3.09423394],
       [ 0.576704  , -1.14449107],
       [-1.32678565, -0.98652433],
       [ 0.93116074,  0.62051564],
       [-1.91103548, -0.37562912],
       [ 1.64160955, -1.21527055],
       [ 0.76452363, -0.98045514],
       [-1.79432259, -0.03012673],
       [-1.04523258,  0.90384422],
       [-1.33750374, -1.57411575],
       [ 1.15368166,  1.0903751 ]])
```

### 종속변수 y
- 16 X 1 행렬

```python
y

>>> print

array([0, 1, 0, 1, 1, 0, 0, 0, 1, 0, 1, 0, 1, 1, 0, 1])
```

### 예측값 y_hat
- 16 X 1 행렬

```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression().fit(X, y)
y_hat = model.predict(X)
y_hat

>>> print

array([1, 1, 0, 1, 1, 0, 0, 0, 1, 0, 0, 0, 1, 1, 0, 1])
```

### 판별함수 값
- 로지스틱회귀 모델의 판별함수에서 얻은 값
- 16 X 1 행렬

```python
f_value = model.decision_function(X)
f_value

>>> print

array([ 0.37829565,  1.6336573 , -1.42938156,  1.21967832,  2.06504666,
       -4.11896895, -1.04677034, -1.21469968,  1.62496692, -0.43866584,
       -0.92693183, -0.76588836,  0.09428499,  1.62617134, -2.08158634,
        2.36316277])
```

### 종속변수, 예측값, 판별함수값을 np.vstack()으로 연결
- 16 X 1 인 열벡터 3개를 하나의 행렬로 만들어 준다.
    - 3 X 16 행렬이 된다.
- 각각의 벡터가 행이 된다.

```python
test_v = np.vstack([y, y_hat, f_value])
test_v

>>> print

array([[ 0.        ,  1.        ,  0.        ,  1.        ,  1.        ,
         0.        ,  0.        ,  0.        ,  1.        ,  0.        ,
         1.        ,  0.        ,  1.        ,  1.        ,  0.        ,
         1.        ],
       [ 1.        ,  1.        ,  0.        ,  1.        ,  1.        ,
         0.        ,  0.        ,  0.        ,  1.        ,  0.        ,
         0.        ,  0.        ,  1.        ,  1.        ,  0.        ,
         1.        ],
       [ 0.37829565,  1.6336573 , -1.42938156,  1.21967832,  2.06504666,
        -4.11896895, -1.04677034, -1.21469968,  1.62496692, -0.43866584,
        -0.92693183, -0.76588836,  0.09428499,  1.62617134, -2.08158634,
         2.36316277]])
```

- vstack()으로 합한 행렬의 모양

```python
test_v.shape

>>> print

(3, 16)
```

### 종속변수, 예측값, 판별함수값을 np.hstack()으로 연결
- 16 X 1 모양의 벡터 3개가 하나의 열벡터가 된다.
    - 48 X 1 벡터가 된다.    

```python
test_h = np.hstack([y, y_hat, f_value])
test_h

>>> print

array([ 0.        ,  1.        ,  0.        ,  1.        ,  1.        ,
        0.        ,  0.        ,  0.        ,  1.        ,  0.        ,
        1.        ,  0.        ,  1.        ,  1.        ,  0.        ,
        1.        ,  1.        ,  1.        ,  0.        ,  1.        ,
        1.        ,  0.        ,  0.        ,  0.        ,  1.        ,
        0.        ,  0.        ,  0.        ,  1.        ,  1.        ,
        0.        ,  1.        ,  0.37829565,  1.6336573 , -1.42938156,
        1.21967832,  2.06504666, -4.11896895, -1.04677034, -1.21469968,
        1.62496692, -0.43866584, -0.92693183, -0.76588836,  0.09428499,
        1.62617134, -2.08158634,  2.36316277])
```

- hstack()으로 합한 행렬의 모양

```python
test_h.shape

>>> print

(48,)
```




































