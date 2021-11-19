# docstring
- 함수의 기능, 요소, 작동 방식 등에 대한 설명을 작성하는 기능
- 다른 사람이 만든 함수나 패키지 등을 사용할 떄 docstring 을 볼 수 있다. 
- 내가 만든 함수나 작업물에 대한 docstring 보고 다른 사람도 사용할 수 있어야 한다. 

### 사용방법
- 함수의 본문에 " 를 사이에 두고 설명문을 작성한다. (다른 사람이 읽어봐도 이해하기 쉽고 최대한 간결하지만, 꼼꼼하게 작성할 것)
  - """ description """
- docstring을 확인하는 방법
  - shift + tap
  - 함수이름?
  - 함수이름??
  - help(함수이름)

### docstring 작성!
- 리스트 안의 숫자의 갯수를 파악하여 반환해주는 함수를 만들고 docstring 작성

```python

def count_number_in_array(n, lst) :
    
    """
    count_number_in_array :
    This func reutrn number of data of in the input lst (= list)
    param "n" defines the range of the entire data
    
    The operation is :
        1. In the first iteration, the j data of the array is compared with i,
            and 1 is added to the i-th data fo the count_list whenever they are equal.
        2. In th second iteration, the k-th value in the count_list where the number
            of data in the array is stored is output only when it is not 0.
    
    param : n : int, lst : str
    print : data1 = number 개, data2 = number 개, ...
    
    """
    count_list = [0] * 200
    
    i = 0
    while i <= n :
        j = 0
        while j <= len(lst) -1 :
            if lst[j] == i :
                count_list[i] += 1
            j += 1
        i += 1
        
    k = 0
    while k <= (n+1) :
        if count_list[k] != 0 :
            print("{} = {} 개".format(k, count_list[k]), end=", ")
        k += 1
```

- docstirng 확인
- ``shift + tap : 함수이름에 커서를 놓고 실행, 일반적으로 많이 사용하는 방법``
- ``함수이름?`` : 함수이름 뒤에 ?를 붙이고 실행하면 docstring을 볼 수 있다.
- ``함수이름??`` : 함수이름 뒤에 ??를 붙이고 실행하면 docstring과 함수의 코드 전체를 볼 수 있다.
- ``help(함수이름)`` : help() 함수안에 함수이름을 넣고 실행하면 docstirng을 볼 수 있다.

```python

''함수이름 뒤에 ??를 붙이고 실행하면 docstring과 함수의 코드, 파일의 위치 함께 나타난다''
count_number_in_array??

Signature: count_number_in_array(n, lst)
Source:   
def count_number_in_array(n, lst) :
    
    """
    count_number_in_array :
    This func reutrn number of data of in the input lst (= list)
    param "n" defines the range of the entire data
    
    The operation is :
        1. In the first iteration, the j data of the array is compared with i,
            and 1 is added to the i-th data fo the count_list whenever they are equal.
        2. In th second iteration, the k-th value in the count_list where the number
            of data in the array is stored is output only when it is not 0.
    
    param : n : int, lst : str
    print : data : number
    
    """
    
    i = 0
    count_list = [0] * 200
    while i <= n :
        j = 0
        while j <= len(lst) -1 :
            if lst[j] == i :
                count_list[i] += 1
            j += 1
        i += 1
        
    k = 0
    while k <= (n+1) :
        if count_list[k] != 0 :
            print("{} = {} 개".format(k, count_list[k]), end=", ")
        k += 1
File:      c:\dss12\010_my_summary\my_summary_python\<ipython-input-18-9f1bb4451d9b>
Type:      function

```

- 함수 호출

```python

''랜덤하게 숫자를 선택하여 random_list 변수에 저장''
random_list = [random.randint(1, 50) for _ in range(30)]
print(random_list)

=====<print>=====

[44, 41, 16, 8, 30, 36, 48, 20, 42, 48, 36, 30, 5, 28, 5, 18, 11, 44, 4, 14, 11, 38, 33, 20, 7, 6, 28, 50, 24, 37]


count_number_in_array(100, random_list)

=====<print>=====

4 = 1 개, 5 = 2 개, 6 = 1 개, 7 = 1 개, 8 = 1 개, 11 = 2 개, 14 = 1 개, 16 = 1 개, 18 = 1 개, 20 = 2 개, 
24 = 1 개, 28 = 2 개, 30 = 2 개, 33 = 1 개, 36 = 2 개, 37 = 1 개, 38 = 1 개, 41 = 1 개, 42 = 1 개, 44 = 2 개, 
48 = 2 개, 50 = 1 개,

```
