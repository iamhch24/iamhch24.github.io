---
title: "[파이썬] list 내포식 사용하여 소수 구하기 문제(Prime number)"
categories:
    - dev
tags:
    - dev
    - python 
toc: true

---
## lambda 함수를 이용하여 소수 구하기

```Python
n = 100
nums = list(range(2,n+1))
prime_nums = list(filter(lambda x: x if list(map( lambda m, n : m%n,[x]*(x-2), range(2,x))).count(0)==0 else 0,nums))
print(prime_nums)
```

## list 내포식을 이용하여 소수 구하기
```Python
n = 100
prime_nums = [
    i for i in range(2,n+1) 
    if [ i%j for j in range(2,i)].count(0)==0
]
print(prime_nums)
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwNzgwODc3MiwtMTA0MjU2OTc3OCwtMT
Q2Nzg4OTE0MV19
-->