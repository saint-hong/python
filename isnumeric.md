# isnumeric()
- str에서 숫자인지를 확인 후 T, F 값을 반환해준다.

### 사용방법
- 변수에 저장된 문자열의 값이 문자인 경우 : False
   - 변수의 타입은 str 이다.

```python
tmp = "a"
tmp.isnumeric()

=====<print>=====
False
```

- 변수에 저장된 문자열의 값이 숫자인 경우 : True
  - 변수의 타입은 str 이다.

```python
tmp = "123"
tmp.isnumeric()

=====<print>=====
True
```

### 응용
- 문자열에 숫자와 문자가 섞여 있는 경우, 숫자와 문자를 구분해야 할 때 사용하면 좋다.
   - 반복문을 사용하여 각 인덱스의 값을 문자인지, 숫자인지 확인

```python
test_words = "number1234"
for i in range(len(test_words)) :
    if test_words[i].isnumeric() == True :
        print("숫자 : {}".format(test_words[i]))
    else :
        print("문자 : {}".format(test_words[i]))

=====<print>=====
문자 : n
문자 : u
문자 : m
문자 : b
문자 : e
문자 : r
숫자 : 1
숫자 : 2
숫자 : 3
숫자 : 4
```
