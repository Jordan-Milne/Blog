Title: Modern Functional Programming: Coconut
Date: 2020-01-20 11:35
Slug: Functional Programming with Coconut
cover: https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse1.mm.bing.net%2Fth%3Fid%3DOIP.UBnhV5Wff8AgBnzMks06gAHaFU%26pid%3DApi&f=1

# Functional Programming with Coconut

Coconut is a language that was built to be useful for functional programming and piggy-backs off of Python (valid Python code is valid Coconut code). Coconut provides modern functional programmuing tools that are easy to use and very powerful. Coconut does to functional programming what Python did to imperative programming

We will start simple and print 'hello world!' in Coconut using a pipeline. Coconut takes the string 'hello world!' and with the pipe `|>` sends it to the `print` function.


```coconut
"hello, world!" |> print
```

    hello, world!


Coconut also allows for more elegant lamda functions. Instead of having to type 'lambda' and using the colon Coconut just uses an arrow, `->`, as shown below.


```coconut
# Coconut
a = x -> x ** 2
print(a(5))
```

    25



```coconut
# Python
b = lambda x : x ** 2
print(b(5)) 
```

    25


The `where` keyword in Coconut is something that Python should adopt. The `where` statement executes each assignment (`a = 1`, `b = 2`) then evaluates the base (`c = a + b`).


```coconut
c = a + b where:
    a = 1
    b = 2 
print(c)
```

    3


Another operator that is very interesting and can tie into a data science project workflow is the `pipeline`. This allows objects to get passed from function to function in human readable code.


```coconut
def add(n):
    return n+5
def subtract(n):
    return n-2
def mult(n):
    return n*6
def div(n):
    return n/3
```


```coconut
2 |> add |> subtract |> mult |> div |> print
```

    10.0


Two powerfull key words in Coconut are `case` and `match` and they give python `if` statements a run for their money. The function below takes a `list` or `tuple` and classify the sequence of the given value. the `case` block provides a value that the `match` statment have to match in order to execute. Only one match statement inside of a case block can ever succeed, so more general matches should be put below more specific ones .


```coconut
def classify_sequence(value):
    out = ""    
    case value:   
        match ():
            out += "empty"
        match (_,):
            out += "singleton"
        match (x,x):
            out += "duplicate pair of "+str(x)
        match (_,_):
            out += "pair"
        match _ is (tuple, list):
            out += "sequence"
    else:
        raise TypeError()
    return out

# Try it out
[] |> classify_sequence |> print
() |> classify_sequence |> print
[1] |> classify_sequence |> print
(1,1) |> classify_sequence |> print
(1,2) |> classify_sequence |> print
(1,1,2) |> classify_sequence |> print
```

    empty
    empty
    singleton
    duplicate pair of 1
    pair
    sequence

