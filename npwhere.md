# np.where
- 넘파이의 배열의 요소들을 조건에 부합하는지 확인하고, 조건에 따라서 출력해준다.
- np.where(condition, x, y) : condition이 맞으면 x, 틀리면 y를 출력
```
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
