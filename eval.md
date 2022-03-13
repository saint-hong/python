# eval()
- str 과 int 를 합치고 이것을 변수로 인식하게 해준다.
- str "q" 와 int "1" 을 합한 뒤 q1 이라는 변수를 호출해 준다.
- 특히 여러개의 서로다른 숫자가 있는 변수를 호출 할 때 유용하다.

## 사용방법
- str "q" 와 int "1" 을 합하면 "q1" 이 되고, 타입은 str 이다. 
```python
A = str("q") + str(1)
print(A, type(A))

=====<print>=====

q1 <class 'str'>
```

- q1 변수를 임의의 집합 데이터로 정의한다.
- eval() 함수로 q와 1을 합하면 q1 이라는 변수가 호출 된다.
```python
q1 = set([1,2,3,4])
B = eval("q" + str(1))
print(B, type(B))

=====<print>=====
{1, 2, 3, 4} <class 'set'>
```

## 반복문에 사용하기
- Q 라는 집합을 만들고 q1~q16 변수에 Q의 부분집합을 각각 정의한다.
- 반복문안에 eval 함수를 넣고 각 변수가 Q의 부분집합인지 확인하도록 한다.
- eval() 함수에 의해서 q와 숫자가 합해져 변수를 호출해 준다.
```python
Q = frozenset(['HH', 'HT', 'TH', 'TT'])

q1 = frozenset(['HH'])
q2 = frozenset(['HT'])
q3 = frozenset(['TH'])
q4 = frozenset(['TT'])
q5 = frozenset(['HH', 'HT'])
q6 = frozenset(['HH', 'TH'])
q7 = frozenset(['HH', 'TT'])
q8 = frozenset(['HT', 'TH'])
q9 = frozenset(['HT', 'TT'])
q10 = frozenset(['TH', 'TT'])
q11 = frozenset(['HH', 'HT', 'TH'])
q12 = frozenset(['HH', 'HT', 'TT'])
q13 = frozenset(['HT', 'TH', 'TT'])
q14 = frozenset(['HH', 'TH', 'TT'])
q15 = frozenset([])
q16 = Q

print(Q)
for i in range(1, 17) : 
    print("**q{}".format(i), "=", eval("q" + str(i)))
    print("   q{}".format(i), "<= Q : {}".format(eval("q"+str(i)) <= Q))

print("Q 의 부분집합의 갯수 : {}".format(2**len(Q)))
```

- q1~q16 은 모두 Q의 부분집합이다. (True)
```python
=====<print>=====

frozenset({'TH', 'HH', 'TT', 'HT'})
**q1 = frozenset({'HH'})
   q1 <= Q : True
**q2 = frozenset({'HT'})
   q2 <= Q : True
**q3 = frozenset({'TH'})
   q3 <= Q : True
**q4 = frozenset({'TT'})
   q4 <= Q : True
**q5 = frozenset({'HH', 'HT'})
   q5 <= Q : True
**q6 = frozenset({'TH', 'HH'})
   q6 <= Q : True
**q7 = frozenset({'HH', 'TT'})
   q7 <= Q : True
**q8 = frozenset({'TH', 'HT'})
   q8 <= Q : True
**q9 = frozenset({'TT', 'HT'})
   q9 <= Q : True
**q10 = frozenset({'TH', 'TT'})
   q10 <= Q : True
**q11 = frozenset({'TH', 'HH', 'HT'})
   q11 <= Q : True
**q12 = frozenset({'HH', 'TT', 'HT'})
   q12 <= Q : True
**q13 = frozenset({'TH', 'TT', 'HT'})
   q13 <= Q : True
**q14 = frozenset({'TH', 'HH', 'TT'})
   q14 <= Q : True
**q15 = frozenset()
   q15 <= Q : True
**q16 = frozenset({'TH', 'HH', 'TT', 'HT'})
   q16 <= Q : True
Q 의 부분집합의 갯수 : 16
```


