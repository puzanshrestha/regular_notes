## Collections
### Basic Collections
- list, tuple, set, dictionary
### Other Collections
- namedtuple
- OrderedDict, defaultDict, Counter, Deque
### Named Tuple
```
In [1]: import collections                                                

In [2]: Point = collections.namedtuple("Point", "x y")                    

In [3]: p1 = Point(10, 20)                                                

In [4]: p2 = Point(30, 40)                                                

In [5]: print(p1.x)                                                       
10

In [6]: print(p2.y)                                                       
40

In [7]: p1 = p1._replace(x=100)                                           

In [8]: p1                                                                
Out[8]: Point(x=100, y=20)
```
### Default Dict
```
In [11]: fruits = ['apple', 'pear', 'orange', 'banana', 'apple', 'grape', 'banan
    ...: a', 'banana']                                                          

In [12]: from collections import defaultdict                                    

In [13]: fruitCounter = defaultdict(int)                                        

In [14]: for fruit in fruits: 
    ...:     if fruit in fruitCounter: 
    ...:         fruitCounter[fruit] += 1 
    ...:     else: 
    ...:         fruitCounter[fruit] = 1 

In [15]: fruitCounter                                                           
Out[15]: defaultdict(int, {'apple': 2, 'pear': 1, 'orange': 1, 'banana': 3, 'grape': 1})

In [16]: fruitCounter = defaultdict(int)                                        

In [17]: for fruit in fruits: 
    ...:     fruitCounter[fruit] += 1 

In [18]: fruitCounter                                                           
Out[18]: defaultdict(int, {'apple': 2, 'pear': 1, 'orange': 1, 'banana': 3, 'grape': 1})

In [19]: fruitCounter = defaultdict(lambda: 100)                                

In [20]: for fruit in fruits: 
    ...:     fruitCounter[fruit] += 1 

In [21]: fruitCounter                                                           
Out[21]: 
defaultdict(<function __main__.<lambda>()>,
            {'apple': 102,
             'pear': 101,
             'orange': 101,
             'banana': 103,
             'grape': 101})
```
### Counter
```
In [25]: from collections import Counter                                        

In [26]: c1 = Counter(class1)                                                   

In [27]: c1                                                                     
Out[27]: Counter({'Bob': 1, 'Ram': 1, 'Hari': 2, 'Hitler': 1, 'Frank': 1, 'James': 1})

In [28]: c1['Bob']                                                              
Out[28]: 1

In [29]: c1['Hari']                                                             
Out[29]: 2

In [30]: c2 = Counter(class2)                                                   

In [31]: c2                                                                     
Out[31]: 
Counter({'Bob': 2,
         'Ram': 2,
         'Hari': 1,
         'Hitler': 1,
         'Frank': 1,
         'James': 1,
         'Bill': 1})

In [32]: print(sum(c1.values()))                                                
7

In [33]: print(sum(c2.values()))                                                
9

In [34]: c1.update(class2)                                                      

In [35]: print(sum(c1.values()))                                                
16

In [36]: c1.values()                                                            
Out[36]: dict_values([3, 3, 3, 2, 2, 2, 1])

In [37]: c1                                                                     
Out[37]: 
Counter({'Bob': 3,
         'Ram': 3,
         'Hari': 3,
         'Hitler': 2,
         'Frank': 2,
         'James': 2,
         'Bill': 1})

In [38]: ## Subtracting                                                         

In [39]: c1.subtract(class2)                                                    

In [40]: c1                                                                     
Out[40]: 
Counter({'Bob': 1,
         'Ram': 1,
         'Hari': 2,
         'Hitler': 1,
         'Frank': 1,
         'James': 1,
         'Bill': 0})

In [41]: print(c1 & c2)                                                         
Counter({'Bob': 1, 'Ram': 1, 'Hari': 1, 'Hitler': 1, 'Frank': 1, 'James': 1})

In [42]: c2                                                                     
Out[42]: 
Counter({'Bob': 2,
         'Ram': 2,
         'Hari': 1,
         'Hitler': 1,
         'Frank': 1,
         'James': 1,
         'Bill': 1})

In [43]: c1                                                                     
Out[43]: 
Counter({'Bob': 1,
         'Ram': 1,
         'Hari': 2,
         'Hitler': 1,
         'Frank': 1,
         'James': 1,
         'Bill': 0})
```
### OrderedDict
### Deque
- "deck"
- appendleft(), append()
- appendleft(), append()
- popleft(), pop()
- rotate()
# 5. Advanced Python
## Enumerations
```
In [28]: from enum import Enum                                                                                                         
In [29]: class Fruit(Enum): 
    ...:     APPLE = 1 
    ...:     BANANA = 2 
    ...:     ORANGE = 3 
    ...:     TOMATO = 4 

In [30]: print(Fruit.APPLE)                                                                                                            
Fruit.APPLE

In [31]: type(Fruit.APPLE)                                                                                                             
Out[31]: <enum 'Fruit'>

In [32]: repr(Fruit.APPLE)                                                                                                             
Out[32]: '<Fruit.APPLE: 1>'

In [33]: Fruit.APPLE.name                                                                                                              
Out[33]: 'APPLE'

In [34]: Fruit.APPLE.name, Fruit.APPLE.value                                                                                           
Out[34]: ('APPLE', 1)
```
### Class Attribute functions
- `.__getattribute__(self, attr)`
--> to retrieve 
- `.__getattr__(self, attr)`
--> return dynamically return a value
- `.__getattr__(self, attr)`
- 
### Using Function References
```python
def call_a(msg):
    '''
    '''
    print("Function a: ", msg)
    

def call_b(msg):
    '''
    '''
    print("Function b: ", msg)


def call_c(msg):
    '''
    '''
    print("Function c: ", msg)

action = 'm'

# Using elif
if action == 'a':
    call_a("argument")
elif action == 'b':
    call_b("argument")
elif action == 'c':
    call_c("argument")

# Using function references
functions = dict(a=call_a, b=call_b, c=call_c)
try:
    functions[action]("argument")
except KeyError:
    print("Define method for action: ", action)
```
