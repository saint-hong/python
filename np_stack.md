# numpy의 stack 함수
- 배열을 이어 붙여주는 기능
   - np.hstack([a, b]) 또는 ((a, b)) : 배열을 행 기준으로 이어 붙여준다., 열의 갯수가 일치해야한다.
   - np.vstack([a, b]) 또는 ((a, b)) : 배열을 열 기준으로 이어 붙여준다., 열의 갯수가 일치해야한다.
   - np.column_stack([a, b]) 또는 ((a, b)) : 배열에 컬럼을 추가해준다., 행의 갯수가 일치해야 한다. 

### hstack
- 행 기준으로 같은 행 끼리 이어붙여 준다.
- 행의 갯수가 일치해야 한다.

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

- 3X1 배열과 5X1 배열
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

- 3X2 배열과 2X2 배열
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

- 2X2 배열과 2X1 배열 : 열의 갯수가 다르면 hstack을 사용할 수 없다.
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
- 행의 갯수가 일치해야 한다.
- 행렬에 컬럼이 추가되는 방식이다.
- 3X2 배열과 3X1 배열
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

- 3X1 배열과 3X2 배열
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
- 3X2 배열과 1X2 배열
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
