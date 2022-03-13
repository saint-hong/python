# isalnum()
- 문자열에 영문자나 숫자가 아닌 것이 있는 경우 False를 반환한다.
   - 영문자, 숫자이면 True 반환
   - 영문자, 숫자, 특수기호 등이 섞여 있으면 False 반환
- 문자열에서 특수기호와 영문자, 숫자를 구별할 때 사용하면 좋을 거 같다.

### 사용법
- 문자열이 모두 영문자인 경우

```python
test = "abc"
test.isalnum()

=====<print>=====
True
```

- 문자열이 모두 숫자인 경우

```python
test = "123"
test.isalnum()

=====<print>=====
True
```

- 문자열이 숫자왕 영문자로 된 경우

```python
test = "abc123"
test.isalnum()

=====<print>=====
True
```

- 문자열에 영문자나 숫자가 아닌 다른 문자가 있는 경우

```python
test = "abc123%%"
test.isalnum()

=====<print>=====
False
```




