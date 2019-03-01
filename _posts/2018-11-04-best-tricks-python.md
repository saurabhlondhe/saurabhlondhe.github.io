---
layout: post
title:  "python.learning"
date:   2018-11-04
desc: "python devolopers tricks and tricks"
keywords: "python,tricks,gh-pages,website,blog"
categories: [Python]
tags: [open source,python, python-leaning,pythoncode]
icon: icon-python
---
---
## Dictionary
-   merge two dicts in python
    ```python
    >>> x = { 'a' : 1, 'b' : 2 }
    >>> y = { 'b' : 3, 'c' : 4 }
    
    >>> z = { **x, **y }
    
    >>> z
    {'a': 1, 'b': 3, 'c': 4}
    ```
    -   as here the value of b is 3, because as dictionary property value of b will be lastly assinged value

---

## List
-   list comprehension
    ```python
    val = []
    for  i in range(10):
        if not i % 2:
        val.append(i*i)
    ```
    this code can be writtien in list comprehension way as follow:

    ```val = [ expression for i in collection if condition]```
    ```python
    even_sqr = [ i*i for i in range(10) if not i % 2]
    ```
    ---
-   remove duplicates
    ```python
    l=[1,1,1,2,2,2,3,3,3,3,4,4,5,5,5,5,6]
    l=list(set(l))
    #   [1, 2, 3, 4, 5, 6]
    ```
---

## itertools
-   permutation
    ```python
    import itertools as it
    l=[]
    for  i in it.permutations("TF"):
        l.append(i)
    print(l)
    print(len(l))
    ```
    -   *output*
        ```python
        [('T', 'F'), ('F', 'T')]
        2
        ```
    
    ---
-   combinations
    ```python
    import itertools as it
    it.combinations(["t","o","o","l"],2)
    ```
    -   *output*
        ```python
        <itertools.combinations object at 0x7f277b70a728>
        ```
    ```python
    list(it.combinations(["t","o","o","l"],2))
    #   [('t', 'o'), ('t', 'o'), ('t', 'l'), ('o', 'o'), ('o', 'l'), ('o', 'l')]
    list(it.combinations(["t","o","o","l"],3))
    #   [('t', 'o', 'o'), ('t', 'o', 'l'), ('t', 'o', 'l'), ('o', 'o', 'l')]
    ```
---

## Function
-   list of functions
    ```python
    def foo(a,b):
        return (a+b)
    ```
    ```python
    >>> funcs = [foo]
    >>> funcs[0]
    <function f at 0x7f293dc6fe18>
    >>> funcs[0](5,3)
    8
    ```

    ---

-   function by diff ways
    ```python
    def cal1(op,x,y):
        if op == 'add':
            return x + y
        elif op == 'sub':
            return x - y
        elif op == 'mul':
            return x * y
        elif op == 'div':
            return x / y
        else:
            return None
    def cal2(op,x,y):
        return {
        'add': lambda: x+y,
        'sub': lambda: x-y,
        'mul': lambda: x*y,
        'div': lambda: x/y,
        }.get(op,lambda: None)()
    print(cal1("add",10,20))
    print(cal2("add",10,20))
    ```
    - *output*
        ```python
        30
        30
        ```
    ---

-   function conditional calling
    ```python
    def add(a,b):
        return a+b
    def power(a,b):
        return a**b
    flag=True
    print((add if flag else power)(3,2))    # 5
    print((add if not flag else power)(3,2))    #   9
    ```

## Programs
-   odd even
    ```python
    a=list(range(1,20))
    #   [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
    odd=list(filter(lambda x: x% 2, a))
    #   [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]
    even=list(filter(lambda x: x% 2 == 0, a))
    #   [2, 4, 6, 8, 10, 12, 14, 16, 18]
    ```
    ---
-   square of list without for
    ```python
    >>> a=list(range(1,20))
    >>> def sqr(i):
    ...     return i*i
    ... 
    >>> list(map(sqr,a))
    [1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121, 144, 169, 196, 225, 256, 289, 324, 361]
    ```
    ---
-   xmas
    ```python
    for i in range(15):
        print(" "*(15-i-1)+"*"*(2*i-1))
    ```

    -   *output*
        ```python                  
                     *
                    ***
                   *****
                  *******
                 *********
                ***********
               *************
              ***************
             *****************
            *******************
           *********************
          ***********************
         *************************
        ***************************
        ```
    ---