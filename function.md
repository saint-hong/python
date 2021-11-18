# 함수 사용
- 함수 선언 함수 호출

## 아규먼트와 파라미터
- 파라미터 : 함수 호출에서 넘어온 아규먼트에 대응하여 받는 변수들
  - def func(idx, name, author, price, since=1999, all_pages=200) 에서 괄호 안에 있는 변수들 
- 아규먼트 : 함수 호출시 함수에 넘겨줄 입력변수들
  - func(3, "king of ring", "J.A", 30000, since=2000, all_pages=500) 에서 괄호 안에 있는 변수들

### 함수 사용 python
- 책의 정보를 출력해주는 함수
- 파라미터 : idx, name, author, price, since=1999, all_pages=200

```python

def func(idx, name, author, price, since=1999, all_pages=200) :
  print("num of book : {}".format(idx))
  print("name : {}".format(name))
  print("author name : {}".format(author))
  print("price : {}".format(price))
  print("since : {}".format(since))
  print("all_pages : {}".format(all_pages))
```

- 함수 호출
- 키워드 아규먼트 값을 변경할 수 있다. since와 all_pages를 변경

```python
func(3, "king of ring", "J.A", 30000, since=2000, all_pages=500)

=====<print>=====

num of book : 3
name : king of ring
author name : J.A
price : 30000
since : 2000
all_pages : 500
```

- 아규먼트에 파라미터를 입력하고 값을 정의해주어도 된다.

```python

func(idx=8, name="wind", author="hong", price=1000, since=2020)

=====<print>=====

num of book : 8
name : wind
author name : hong
price : 1000
since : 2020
all_pages : 200
```

- 아규먼트로 리스트나 튜플 형태를 입력해도 된다.
- 키워드 아규먼트는 입력하지 않으면 파라미터에 설정되어있는 값 그대로 반환된다.

```python

book_idx = (4, 5, 6)
func(20, ["music_1", "music_2"], "kim", 36000)

=====<print>=====

num of book : (4, 5, 6)
name : ['music_1', 'music_2']
author name : kim
price : 36000
since : 1999
all_pages : 200
```

## ``*args``, ``**kwargs``
- 함수 호출 시 아규먼트와 키워드 아규먼트의 갯수를 특정지을 수 없을 때 사용할 수 있다.
- 함수의 파라미터 값으로 입력 : *args = 아규먼트 비특정, **kwargs : 키워드아규먼트 비특정
  - def func(*args, **kwargs)

### python
- ``*args``와 ``**kwargs`` 의 타입과 반환되는 값 확인
- 입력받은 숫자를 더한 결과를 반환하는 함수 선언

```python

def plus(*args, **kwargs) :
  print(type(args), args)
  print(type(kwargs), kwargs)
  print(kwargs.values())
  return sum(args) + sum(list(kwargs.values()))
```

- 함수 호출 시 여러개의 아규먼트를 입력 할 수 있다.
- 숫자는 파라미터의 ``*args``에서 받고, 키워드아규먼트는 ``**kwargs``에서 받는다.
- 기본적으로 ``*args`` 는 튜플타입이고, ``**kwargs``는 딕셔너리타입이다.

```python

plus(1, 2, 3, 4, 5, 6, 7, 8, 9, num1=10, num2=100)

=====<print>=====

<class 'tuple'> (1, 2, 3, 4, 5, 6, 7, 8, 9)
<class 'dict'> {'num1': 10, 'num2': 100}
dict_values([10, 100])
155
```

- 변수에 튜플이나 리스트 데이터를 저장한 후 아규먼트에 ``*+변수이름`` 을 입력하여 함수를 호출 할 수 있다.
- 아규먼트로 리스트 데이터를 입력하면, 함수에서는 ``*args``에서 받기때문에, 튜플로 변환해서 반환한다.

```python

num_data = (1, 2, 3, 4, 5)
plus(*num_data)

=====<print>=====

<class 'tuple'> (1, 2, 3, 4, 5)
<class 'dict'> {}
dict_values([])
15

''아규먼트로 리스트를 입력하면, 함수에서는 *args에서 받기때문에 튜플로 변환해서 반환한다.''
num_data_2 = [1, 2, 3, 4, 5]
plus(*num_data_2)

=====<print>=====

<class 'tuple'> (1, 2, 3, 4, 5)
<class 'dict'> {}
dict_values([])
15
```

- 함수 호출시 아규먼트는 튜플로, 키우드 아규먼트는 딕셔너리로 저장된 변수를 사용할 수 있다.
- 책 정보 함수에서 idx, price, since, pages 는 ``*변수이름`` 아규먼트로, name과 author는 ``**변수이름``으로 데이터를 받을 수 있다.
```python

def book_info(idx, price, since, pages, name="oasis", author="hong") :
  print("num of book : {}".format(idx))
  print("name : {}".format(name))
  print("author name : {}".format(author))
  print("price : {}".format(price))
  print("since : {}".format(since))
  print("all_pages : {}".format(pages))

''idx, price, since, pages는 튜플로 저장''
db1 = (5, 20000, 1998, 356)
''name과 author는 딕셔너리로 저장''
db2 = {
    "name":"king",
    "author":"kim"
}
''함수 호출 : 아규먼트는 *변수이름, 키워드아규먼트는 **변수이름 으로 호출''
book_info(*db1, **db2)  

=====<print>=====

num of book : 5
name : king
author name : kim
price : 20000
since : 1998
all_pages : 356
```
