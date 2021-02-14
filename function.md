# 함수

* 똑같은 내용을 반복해서 작성하는 것을 방지하기 위해 함수를 사용한다.
* 반복되는 부분이 있을 경우 "반복적으로 사용되는 가치 있는 부분"을 한 뭉치로 묶어서 "어떤 입력값을 주었을 때 
어떤 결괏값을 돌려준다"라는 식의 함수로 작성하는 것이 현명하다.

## 파이썬 함수의 구조

```Python
# 함수의 구조.
>>> def 함수명(매개변수):
        <수행할 문장1>
        <수행할 문장2>
        ...

# 더하기 함수를 만들 경우. 
>>> def add(a, b):
        return a + b

>>> c = add(2, 3)
>>> print(c)
>>> 5
```
위의 코드에서 add 함수의 매개변수(parameter)는 a, b 이고  3,4 는 인수(arguments)이다.

- 매개변수: 함수에 입력으로 전달된 값을 받는 변수를 의미.
- 인수    : 함수를 호출할 때 전달하는 입력값을 의미.


## 입력값과 결괏값에 따른 함수의 형태
```Python
# 일반적인 함수
>>> def 함수이름(매개변수):
        <수행할 문장>
        ...
        return 결과값

# 일반 함수 예
# 입력값과 결괏값이 있는 함수의 사용법
# 결괏값을 받을 변수 = 함수이름(입력인수1, 입력인수2)
>>> def add(a, b):
        result = a + b
        return result

>>> a = add(3, 4)
>>> print(a)
7

#########################################################################################

# 입력값이 없는 함수
>>> def say():
        retrun 'Hi'

# 위 함수를 사용하기 위해서는 say()처럼 괄호 안에 아무 값도 넣지 않아야 한다.
# 입력값은 없지만 결괏값으로 Hi라는 문자열을 반환한다. 

# a에 Hi문자열이 대입된다.
# 결괏값을 받을 변수 = 함수이름()
>>> a = say()
>>> print(a)
'Hi'

#########################################################################################

#  결괏값이 없는 함수
>>> def add(a, b):
        print(f'{a} 와{b} 의 합은 {a+b} 입니다.')
    
>>> add(3, 4)
3 와 4 의 합은 7 입니다.

>>> a = add(3, 4)
>>> print(a)
None


#########################################################################################

# 입력값도 결괏값도 없는 함수
>>> def say():
        print('Hi')

# 입력인수를 받는 매개변수도 없고 return 문도 없으니 입력값도 결괏값도 없는 함수이다.
# 함수이름() 으로 사용한다.
>>> say()
Hi

```


## 매개변수 지정하여 호출하기

* 함수를 호출할 때 매개변수를 지정할 수 있다.
```Python
>>> def add(a, b):
        return a + b

>>> result = add(a=3, b=7)
>>> print(result)
10
```

* 매개변수를 지정하면 다음과 같이 **순서에 상관없이** 사용할 수 있다는 장점이 있다.

```Python
>>> result = add(b=5, a=3)
>>> print(result)
8
```


## 입력값이 몇 개가 될지 모를 때

```Python
>>> def 함수이름(*매개변수):
        <수행할문장>
        ...
```

* 입력값이 여러개일 때, 몇 개가 입력될지 모를 때 사용하는 방법이다. <br> 일반적으로 볼 수 있는 함수 형태에서 괄호 안의 매개변수 부분이 *매개변수로 바뀌었다.

```Python
# *args 처럼 매개변수 이름 앞에 * 을 붙이면 입력값을 전부 모아서 튜플로 만들어준다.
>>> def add_many(*args):
        result = 0
        for i in args:
            result = result + i
        return result
```

> ※ args는 매개변수를 뜻하는 영어단어 arguments의 약자.


```Python
>>>  def add_mul(choice, *args): 
...     if choice == "add": 
...         result = 0 
...         for i in args: 
...             result = result + i 
...     elif choice == "mul": 
...         result = 1 
...         for i in args: 
...             result = result * i 
...     return result 
...

# add_mul 함수는 여러개의 입력값을 의미하는 *args 매개변수 앞에 choice 매개변수가 추가되어 있다.
>>> result = add_mul('add', 1, 2, 3, 4, 5)
>>> print(result)
15

>>> result = add_mul('mul', 1, 2, 3, 4, 5)
>>> print(result)
120
```

## 키워드 파라미터 kwargs
키워드 파라미터를 사용할 때는 매개변수 앞에 별 두개(**)를 붙인다.
```Python
>>> def print_kwargs(**kwargs):
        print(kwargs)

>>> print_kwargs(a=1)
{'a':1}

>>> print_kwargs(name='foo',age=3)
{'age': 3, 'name': 'foo'}

```
- 입력값 a=1 또는 name='foo', age=3 이 모두 딕셔너리로 만들어져 출력되었다.
- **kwargs처럼 매개변수 이름 앞에 **을 붙이면 매개변수 kwargs는 딕셔너리가 되고 모든 key=value 형태의 결괏값이 그 딕셔너리에 저장된다.

> ※ kwargs는 keyword arguments의 약자이며 args와 마찬가지로 관례적으로 사용한다.


## 함수의 결괏값은 언제나 하나.
```Python
>>> def add_and_mul(a, b):
        return a+b, a*b

# 결괏값은 2개가 아닌 언제나 하나로 결괏값 a+b와 a*b는 하나의 튜플형태로 반환된다.
>>> result = add_and_mul(3, 4)

>>> result
(7, 12)

# 만약 이 하나의 튜플 값을 2개의 결괏값처럼 받고 싶다면 다음과 같이 함수를 호출해야 한다.
>>> result1, result2 = add_and_mul(3, 4)

>>> result1
7
>>> result2
12
```

## return 문 사용 (종종 이용된다.)
```Python
>>> def say_nick(nick):
        if nick == "바보":
            return
        print(f"나의 별명은 {nick} 입니다.")

>>> say_nick("멍청이")
나의 별명은 멍청이 입니다.
# return문으로 함수 빠져나갔으므로 실행되지 않는다.
>>> say_nick("바보")
>>>
```


## 매개변수에 초깃값 미리 설정하기
```Python
def say_myself(name, old, man=True): 
    print("나의 이름은 %s 입니다." % name) 
    print("나이는 %d 살입니다." % old) 
    if man: 
        print("남자입니다.")
    else: 
        print("여자입니다.")

# 매개변수에 초깃값 man=True 적었으므로 인자가 2개일 경우에는 man=True가 default다.
>>> say_myself("민기",23)
나의 이름은 민기 입니다.
나이는 23 살입니다.
남자입니다.

>>> say_myself("민기",23,False)
나의 이름은 민기 입니다.
나이는 23 살입니다.
여자입니다.

# 초깃값이 있는 man=True 매개변수와 old 매개변수의 위치변경.
def say_myself(name, man=True, old): 
    print("나의 이름은 %s 입니다." % name) 
    print("나이는 %d 살입니다." % old) 
    if man: 
        print("남자입니다.")
    else: 
        print("여자입니다.")

>>> say_myself("김응수",24)
# python인터프리터는 24를 man변수와 old변수 중 어느곳에 대입해야 할지 알 수 없게 되어 명사 에러난다.
# ※ 초기화하고 싶은 매개변수를 항상 뒤쪽에 놓아야 한다.
>>> SyntaxError: non-defualt argument follows default argument

```

## 함수 안에서 선언한 변수의 효력 범위
```Python
>>> a = 1

>>> def vartest(a):
        a = a + 1

>>> varteset(a)
>>> print(a)
1
```
* vartest함수에서 매개변수 a의 값에 1을 더했으니 2가 출력될 것 같지만 결괏값은 1이 나온다.<br>그 이유는 함수 안에서 새로 만든 매개변수는 함수 안에서만 사용하는 "함수만의 변수"이기 때문이다. <br> 즉 def vartest(a)에서 입력값을 전달받는 매개변수 a는 함수 안에서만 사용하는 변수이지 함수 밖의 변수 a가 아니라는 것이다.

```Python
# 위의 vartest함수는 다음처럼 변수 이름을 hello로 한 vartest함수와 완전히 동일.
>>> def vartest(hello):
        hello = hello + 1

>>> vartest(3)
# 에러난다. 이유는 hello라는 변수는 어디에서도 찾을 수 없기 때문이다.
>>> print(hello)
```


## 함수 안에서 함수 밖의 변수를 변경하는 방법.

### 1. return 사용

```Python
>>> a = 1
>>> def vartest(a):
        a = a + 1
        return a

>>> a = vartest(a)
>>> print(a)
2
```

### 2. global 명령어 사용하기
```Python
>>> a = 1
>>> def vartest():
        global a
        a = a+1

>>> vartest()
>>> print(a)
2
```
* 두 번째 방법은 global 명령어를 사용하는 방법이다. <br>
 위 예에서 볼 수 있듯이 vartest 함수 안의 global a 문장은 함수 안에서 함수 밖의 a 변수를 직접 사용하겠다는 뜻이다.<Br> 하지만 프로그래밍을 할 때 global 명령어는 사용하지 않는 것이 좋다. 왜냐하면 함수는 독립적으로 존재하는 것이 좋기 때문이다. <br>외부 변수에 종속적인 함수는 그다지 좋은 함수가 아니다. 그러므로 가급적 global 명령어를 사용하는 이 방법은 피하고 첫 번째 방법을 사용하기를 권한다.


 
## lambda

* lambda는 함수를 생성할 때 사용하는 예약어로 def와 동일한 역할을 한다. <br>def를 사용해야 할 정도로 복잡하지 않거나 def를 사용할 수 없는 곳에 주로 쓰인다.

사용법
> lambda 매개변수1, 매개변수2, ...: 매개변수를 이용한 표현식

```Python
>>> add = lambda a, b : a+b
>>> result = add(3, 4)
>>> print(result)
7


# 위와 동일
>>> def add(a, b):
        return a+b

>>> result = add(3, 4)
>>> print(result)
7
```

> ※ lambda 예약어로 만든 함수는 return 명령어가 없어도 결괏값을 돌려준다.

