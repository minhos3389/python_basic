# 사용자 입력과 출력

---

## input의 사용

```Python
>>> a = input()
Life is short
>>> a
"Life is short"
```

* ※ :주의: input은 입력되는 모든 것을 문자열로 취급한다. 


## 프롬프트를 띄워서 사용자 입력 받기

> input('질문 내용')

```Python
>>> name = input("이름을 입력하세요: ")
이름을 입력하세요: 김민호

>>> print(name)
"김민호"

>>>
```

## print 자세히 알기

### 큰 따옴표(")로 둘러싸인 문자열은 + 연산과 동일하다.
```Python
>>> print("Life" "is" "too short") 
Life is too short

>>> print("Life" + "is" + "too short")
Life is too short
```

## 문자열 띄어쓰기는 콤마로 한다.
```Python
>>> print("life", "is", "too short")
life is too short
```

## 한 줄에 결괏값 출력
```Python
>>> for i in range(10):
        print(i, end = ' ')
    
0 1 2 3 4 5 6 7 8 9
```
