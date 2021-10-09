# meshgrid
- meshgrid 함수는 입력받은 배열의 모양을 변형시켜주며, 3차원 그래프를 그릴 때 주로 사용된다.
- np.meshgrid(x, y) : x 배열을 행벡터로 갖는 행렬, y 배열을 열벡터로 갖는 정방행렬을 두개의 변수로 반환한다.
```
test_xx = np.array([1,2,3,4,5])
test_xx

=====<print>=====

array([1, 2, 3, 4, 5])


test_yy = np.array([6,7,8,9,10])
test_yy

=====<print>=====

array([ 6,  7,  8,  9, 10])

test_XX, test_YY = np.meshgrid(test_xx, test_yy)
test_XX

=====<print>=====

array([[1, 2, 3, 4, 5],
       [1, 2, 3, 4, 5],
       [1, 2, 3, 4, 5],
       [1, 2, 3, 4, 5],
       [1, 2, 3, 4, 5]])

test_YY

=====<print>=====

array([[ 6,  6,  6,  6,  6],
       [ 7,  7,  7,  7,  7],
       [ 8,  8,  8,  8,  8],
       [ 9,  9,  9,  9,  9],
       [10, 10, 10, 10, 10]])
```

- 0~10 까지의 정수들로 좌표 그려보기

```
x = np.linspace(0, 10, 11)
y = np.linspace(0, 10, 11)
XX, YY = np.meshgrid(x, y)

plt.scatter(XX, YY, c='r')
plt.xticks(range(11))
plt.yticks(range(11))

plt.show() ;
```
![meshgrid_scatter.png](./images/meshgrid_scatter.png)

