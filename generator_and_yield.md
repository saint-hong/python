# 제너레이터와 yield (코딩도장)
- 제너레이터는 이터레이터를 생성해주는 함수
    - 보통 이터레이터를 만들려면 `__iter__, __next__, __getitem__` 메서드를 사용해야 한다. 
    - 제너레이터는 yield 키워드를 사용하여 이터레이터를 생성한다.
    - 제너레이터는 이터레이터보다 간단하게 작성하여 사용할 수 있다.
- 함수안에 yield만 넣어주면 함수는 제너레이터가 된다.(이터레이터의 기능을 한다.)
    - yield에는 값을 지정한다.
- 반복문에서 순회객체로 사용한다.
    - 이터레이터와 사용법이 같다.
    - for 문에서 `__next__` 메서드를 호출하여 yield의 값을 하나씩 가져온다.
- generator를 'laze iterator'(게으른 반복자) 라고도 한다.

## yield의 의미    
- 생산이라는 의미도 있지만 양보라는 의미도 있음
    - 값을 함수 바깥으로 전달하면서 코드의 실행을 함수 바깥에 양보한다.
    - yield는 현재 함수를 잠시 중단하고 함수 바깥의 코드가 실행되도록 한다.
- yield가 있는 함수의 코드를 다 실행하는 것이 아니라 yield가 값을 바깥에 반환하고 다음 실행을 바깥의 코드에 양보한다.    
- return은 반환 즉시 함수가 끝나지만, yield는 값을 바깥의 코드에 보내고, 바깥의 코드가 실행되도록 양보한 후 다시 제너레이터 안의 코드를 실행한다.

## yield의 장점
- 데이터의 길이가 길면 return 보다 yield가 더 메모리를 효율적으로 사용한다.
    - return은 모든 데이터를 계산한 후 출력한다면, yield는 하나씩 처리한다. (?)
- yield는 대용량 파일이나 스트림 데이터 처리에서 유용하게 사용할 수 있다.
- http://pyengine.blogspot.com/2012/01/yield-2-yield.html
    - 함수는 기본적으로 실행이 종료되면 함수 안의 로컬 변수들은 날아간다. (휘발성)
    - 그러므로 global을 선언하여 날라가는 것을 방지한다.
    - yield는 휘발성이 없다. global하게 살아 있는 함수와 같다.
    - 즉 "멀티프로세싱"의 기능을 한다. 일종의 "thread"와 같다.
    - turn 방식의 thread와 같다. : 한번에 하나씩 돌리면서 synchronous하게 작동


### 함수안에 yield를 사용하여 generator 함수 만들기

```python
def number_generator() :
    yield 0
    yield 1
    yield 2

for i in number_generator() :
    print(i)

>>> print

0
1
2
```

### 제너레이터 함수의 메서드 목록 확인
- 이터레이터의 메서드인 iter, next가 들어 있다.

```python
g = number_generator()
g

>>> print

<generator object number_generator at 0x000002B7869A37C8>

print(dir(g))

>>> print

['__class__', '__del__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__lt__', '__name__', '__ne__', '__new__', '__next__', '__qualname__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'close', 'gi_code', 'gi_frame', 'gi_running', 'gi_yieldfrom', 'send', 'throw']
```

### 제너레이터의 next 메서드 사용
- 제너레이터의 yield에 저장 된 값이 하나씩 출력 된다.
- 모두 출력되면 반환값이 없다.

```python
g.__next__()

>>> print

0

g.__next__()

>>> print

1

g.__next__()

>>> 2

g.__next__()

>>> print

StopIteration:
```

### yield의 기능
- 함수안에서 함수 바깥의 코드에 값을 반환하고, 함수 바깥의 코드가 실행되도록 양보한다.
- 그 동안 함수는 종료되는 것이 아니라 다음 호출이 있을때까지 기다린다.

```python
def number_generator() :
    yield 0   # next(g)에서 값을 바깥에 전달하고, print(a)가 실행되도록 양보함
    yield 1
    yield 2

g = number_generator()

a = next(g)   # yield 0을 호출하고 print(a)를 실행함(yield가 실행을 양보함)
print(a)

b = next(g)
print(b)

c = next(g)
print(c)

>>> print

0
1
2
```

### return과 yield의 차이
- return이 실행되면 함수가 종료된다.
- yield는 값이 전부 반환될때까지 함수를 종료하지 않고 기다리게 한다.

```python
def one_generator() :
    yield 1   # print(next(g))에 값 1을 전달하고 다음 코드를 양보한다.
    return 'return에 저장한 값'

try :
    g = one_generator()
    print(next(g))   # yield 1이 출력된다.
    print(next(g))   # 다음 print(next(g))에서 더이상 가져올 값이 없으므로 StopIteration error 가 반환된다.

except StopIteration as e :   # 에러가 발생하면 return 값을 반환하고 종료한다.
    print(e)

>>> print

1
return에 저장한 값
```

# python yield란? (블로그)
- https://kkamikoon.tistory.com/entry/Python-Yield%EB%9E%80-What-is-the-Yield
- yield : 생성자 generator
    - iterator와 결과값은 같지만 실행 방식이 다르다.
- generator의 의미
    - iterator를 생성해주는 함수
    - iterator는 next() 메서드를 통해 순차적으로 값을 가져오는 object
    - yield를 가지고 있으므로 다른 함수와 다른다.
- yield의 기능
    - generator가 yield를 만나면 해당 함수가 정지한다. 반환값을 next() 메서드를 호출한 바깥 코드로 전달한다. 
    - 값을 바깥에 전달하고 함수가 종료되는 것이 아니라(return 처럼) 이 상태를 유지한다.
    - 즉 함수안의 local 변수 등이 날아가지 않고 메모리에 그대로 남아있게 된다.
- generator의 장점
    - list comprehension과 비슷하다. : [] 대신 () 을 사용한다.
    - 장점 1 : memory를 효율적으로 사용
        - 리스트는 리스트 안의 모든 데이터를 메모리에 적재한다. 따라서 데이터 사이즈가 커질 수록 메모리 사용량이 늘어난다. generator는 데이터를 한번에 메모리에 적재하는 것이 아니라 next() 메서드가 호출 될 때마다 메모리에 적재하므로 데이터 사이즈가 커져도 메모리 사용량이 작다.
    - 장점 2 : 계산을 늦추는 효과가 있다.
        - lazy evaluation
        - 리스트는 모든 계산의 실행을 먼저 수행한다.
        - generator는 필요할 때마다 계산을 실행한다. 따라서 수행 시간이 긴 연산을 늦출 수 있다.


### yield의 기능

```python
def number_generator(n) :

    # return 대신 yield가 반복문에 값을 전달한다.
    print("function start")
    while n < 6 :
        yield n   # n을 print(i)에 전달하고 다음 for 문이 실행되도록 양보한다.
        n += 1
    print("function end")


if __name__ == "__main__"  :
    for i in number_generator(0) :
        print(i)

>>> print

function start
0
1
2
3
4
5
function end
```

### yield와 for문의 실행 과정
- yield는 함수 바깥의 반복문 코드에 값을 반환하고, 바깥의 반복문 코드에 다음 실행을 양보한다.
- 바깥의 코드가 실행되면 다시 함수가 작동한다.
- 이것을 반복하여 바깥의 반복문이 종료 될 때까지 함수를 종료하지 않고 지연시킨다.

```python
def generator_test(n) :

    print("===== Generator Start =====")

    while (n < 3) :
        print("<< Before Yield >>")
        yield n
        n += 1
        print("<< After Yield >>")
        print("===== Generator End =====")


if __name__ == "__main__" :
    print("----- Main Function Start -----")

    for i in generator_test(0) :
        print("**start for statement**")
        print(f"Yield : {i}")
        print("**end for statement**")

    print("----- Main Function Start -----")

>>> print

----- Main Function Start -----
===== Generator Start =====
<< Before Yield >>
**start for statement**
Yield : 0
**end for statement**
<< After Yield >>
===== Generator End =====
<< Before Yield >>
**start for statement**
Yield : 1
**end for statement**
<< After Yield >>
===== Generator End =====
<< Before Yield >>
**start for statement**
Yield : 2
**end for statement**
<< After Yield >>
===== Generator End =====
----- Main Function Start -----
```

### 리스트 컴프리핸션과 generator의 비교
- 리스트 컴프리핸션 : [] 사용
- 제너레이터 : () 사용

```python
# 리스트 컴프리핸션

[i for i in range(10)]

>>> print

[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# 제너레이터는 ()을 사용하여 생성한다.

(i for i in range(10))

>>> print

<generator object <genexpr> at 0x000002B7869D52C8>
```

#### 제너레이터는 yield 문을 사용하므로 바깥의 반복문이 종료될떄까지 함수가 유지된다.

```python
def generator(wordlist) :

    # wordlistlength가 wordlist의 길이보다 크면 종료
    print("===Generator Start")

    wordlistlength = 0
    while (wordlistlength < len(wordlist)) :
        yield wordlist[wordlistlength]
        wordlistlength += 1

if __name__ == "__main__" :

    Main_wordlist = ["TEST", "IS", "WORK", "GOOD"]
    for i in generator(Main_wordlist) :
        print(i)
    print("===Done")

>>> print

===Generator Start
TEST
IS
WORK
GOOD
===Done
```
#### generator의 장점 1 : 메모리를 효율적으로 사용
- 리스트 컴프리 핸션의 메모리 사용량

```python
import sys

a = [i for i in range(100)]
sys.getsizeof(a)

>>> print

912

b = [i for i in range(1000)]
sys.getsizeof(b)

>>> print

9024
```

- 제너레이터의 메모리 사용량

```python
c = (i for i in range(100))
sys.getsizeof(c)

>>> print

120

d = (i for i in range(1000))
sys.getsizeof(d)

>>> print

120
```

#### generator의 장점 2 : 계산을 늦추는 효과
- 함수의 return은 반복문의 호출에서 모든 계산을 한번에 끝낸 후 값을 반환한다.
    - 함수가 종료된다. 함수 안의 변수 할당도 사라진다.
- 함수의 yield는 반복문에 호출이 될때마다 함수를 실행시킨다. 반복문이 종료됐을 때 함수를 종료시킨다.
    - 따라서 함수의 실행을 늦추고, 늦추는 동안 함수가 종료되는 것이 아니라 유지된다.

```python
import time

def sleep_function(x) :

    print("sleep...")
    time.sleep(1)
    return x

print("===== List Comprehension =====")
test_list = [sleep_function(i) for i in range(5)]

for i in test_list :
    print(i)

print("===== Generator =====")
test_gen = (sleep_function(i) for i in range(5))

for i in test_gen :
    print(i)

>>> print

===== List Comprehension =====
sleep...
sleep...
sleep...
sleep...
sleep...
0
1
2
3
4
===== Generator =====
sleep...
0
sleep...
1
sleep...
2
sleep...
3
sleep...
4
```
