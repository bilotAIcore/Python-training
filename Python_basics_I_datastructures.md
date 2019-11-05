
<img src="py-logo.png" width="100pt"/>



# INTRODUCTION TO PYTHON 
# I – DATA STRUCTURES
*Lasse Ruokolainen*

*Seasoned Data Master, BILOT Consulting Oy* 

***

## (1) Data types
In Python there are several types of data entries that are treated differently. These **types** include: **int**, **float**, **string**, and **boolean**. Numeric types **int** and **float** can be subjected to any mathematical operation, whereas textual operations are used with **string** types. Boolean types are convenient in control structures as well in filtering/indexing variables data/tables. The type of an **object** can be queried with the **function** `type()`.

### (a) *Numeric*
Numeric objects are either integers or decimal numbers.


```python
# assign a value to an object:
a = 6
# query the type of a and print it to the console:
print(type(a))
```

    <class 'int'>



```python
b = 2.3
print(type(b))
```

    <class 'float'>



```python
print(a + b)
```

    8.3



```python
# assign the result from an operation to an object:
c = a * b - b/a
# controlled printing:
print('%.2f' %c)
# or:
print('Result: {0:.2f}'.format(c))
```

    13.42
    Result: 13.42


### (b) *String*
String objects can be either single words or longer sentences.


```python
animal = 'cat'
print(type(animal))
```

    <class 'str'>



```python
print(animal.capitalize())
```

    Cat



```python
# number of characters:
print(len(animal))
```

    3



```python
# concatenate strings:
fact = animal.capitalize() + ' is a feline'
print(fact)
```

    Cat is a feline



```python
opinion = 'I hate ' + animal.upper() + 'S!'
print(opinion)
```

    I hate CATS!



```python
# repeat a string:
print(animal * 3)
```

    catcatcat



```python
# find the position of a character/pattern:
print(opinion.index('e'))
```

    5



```python
# replace a part of a string:
print(opinion.replace('hate','love').replace('I','You'))
```

    You love CATS!



```python
# join strings:
animals = ['cat', 'dog', 'horse', 'python']

', '.join(animals)
```




    'cat, dog, horse, python'




```python
# list the content of the current workspace:
%who
```

    a	 animal	 animals	 b	 c	 fact	 opinion	 


### (c) *Boolean*
Boolean objects contain values `True` or `False`, which can be interpretted as numeric 1/0.


```python
# logical test:
test = a > b
print(test)
```

    True



```python
print(type(test))
```

    <class 'bool'>



```python
# logical matching:
print('cat' in fact)
```

    False



```python
print(animal is 'cat')
```

    True


***
## (2) Data structures
Python contains a rich set of different data structures that are convenient for different purposes. 

### (a) *List*
Lists in Python are used to store collection of heterogeneous items. Lists are generated using square brackets (`[` and `]`) that hold elements, separated by a comma (`,`). That is, a **list** is a collection of entries that can be of any **type**. Lists can also be nested, meaning that a list can contain a list (or any other data structure). Lists can be either appended or reduced with convenient methods `.append()` and `.remove()` (note that these operations modify the list without the need to redefine the object). To make an empty list, type: [].


```python
# generate a list with heterogeneous items:
x = [1,'a',1,2,'a','b',4,'b']
print(x)
```

    [1, 'a', 1, 2, 'a', 'b', 4, 'b']



```python
print(type(x))
```

    <class 'list'>



```python
# count number of instances:
print(x.count('b'))
```

    2



```python
# concatenate two lists:
print(x + [3,'c'])
```

    [1, 'a', 1, 2, 'a', 'b', 4, 'b', 3, 'c']



```python
# query the length of a list:
print(len(x))
```

    8



```python
# make a nested list:
y = [[1,2,3,4], ['a','b','c','d']]
print(y)
```

    [[1, 2, 3, 4], ['a', 'b', 'c', 'd']]



```python
print(len(y))
```

    2



```python
# append a list:
x.append(4.75)
print(x)
```

    [1, 'a', 1, 2, 'a', 'b', 4, 'b', 4.75]



```python
# remove elements of a list:
x.remove(4.75)
print(x)
```

    [1, 'a', 1, 2, 'a', 'b', 4, 'b']



```python
# extend a list:
x.extend([0,5,1,'stop'])
print(x)
```

    [1, 'a', 1, 2, 'a', 'b', 4, 'b', 0, 5, 1, 'stop']


What is the difference between `.append` and `.extend`? The former will add what ever is the input as a new element in the list, while the latter will extent the list with the input:
x = [1,2,3]

x.append([4, 5, 6]) -> [1,2,3,[4,5,6]]

x.extend([4, 5, 6]) -> [1,2,3,4,5,6]
### (b) *Numpy array*
Lists cannot used in calculations, as they are allowed to contain any type data. NumPy arrays are like lists, but can be used in calculations, because they can only contain a single type of values. To use Numpy arrays one needs to import the `numpy` package. This is done using the `import` command: `import numpy`. This will load the library to the working memory, with name `numpy`. It is however a convention to import `numpy` as `np`, but you are free to do this anyway you like.


```python
# import numpy:
import numpy as np
```


```python
# generate a numeric array:
nar = np.array(range(0,5))
print(nar)
print(type(nar))
```

    [0 1 2 3 4]
    <class 'numpy.ndarray'>



```python
# calculate sum over the array:
print(sum(nar))
```

    10



```python
# mathematical operation on array:
print(nar/2)
```

    [0.  0.5 1.  1.5 2. ]



```python
# bind arrays together:
matrix = np.column_stack((nar,nar))
print(matrix)
```

    [[0 0]
     [1 1]
     [2 2]
     [3 3]
     [4 4]]



```python
# query the shape of an array (note: this returns a tuple):
print(matrix.shape)
```

    (5, 2)


Even if **arrays** can contain only a singly data type, it does not mean it needs to be numeric; string arrays and boolean arrays are also possible.  


```python
# generate string array:
sar = np.array(['anaconda','worm,','viper','snake','python','boa'])
print(len(sar))
```

    6



```python
print('snake' in sar)
```

    True



```python
# logical matching generates a boolean array:
print(sar == 'python')
```

    [False False False False  True False]


### (c) *Tuple*
Tuples are sequences, just like lists. The differences between tuples and lists are, the tuples cannot be changed unlike lists and tuples use parentheses, whereas lists use square brackets. In Python tuples are written with round brackets (`(` and `)`). An empty tuple is created by: ().


```python
tu = matrix.shape
print(type(tu))
```

    <class 'tuple'>



```python
tu2 = (1,2,3,4)
print(tu2)
```

    (1, 2, 3, 4)



```python
tu3 = 'anaconda','worm','viper','snake','python','boa'
print(tu3)
```

    ('anaconda', 'worm', 'viper', 'snake', 'python', 'boa')



```python
print(tu3[3])
```

    snake



```python
tu3[3] = 'serpent'
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-57-702bbf9ac3f6> in <module>
    ----> 1 tu3[3] = 'serpent'
    

    TypeError: 'tuple' object does not support item assignment



```python
# unpacking of a tuple:
a,b,c,d = tu2
```

but what if one want's only the first element from the tuple as a separate object?


```python
a,*rest = tu2
print(a)
print(rest)
```

    1
    [2, 3, 4]


### (d) *Dictionary*
Dictionaries are handy data structures that combine key-value pairs. Each key is separated from its value by a colon (`:`), the items are separated by commas, and the whole thing is enclosed in curly braces (`{` and `}`). An empty dictionary without any items is written with just two curly braces, like this: {}. Dictionary keys can be accessed with `.keys()` method, while the values can be accessed with the `.values()` method. As lists, dictionaries can be nested.


```python
# create a dictionary:
mydict = {'name':'Anne','pet':'cat','age':25}
```


```python
# get keys:
print(mydict.keys())
```

    dict_keys(['name', 'pet', 'age'])



```python
# get values:
print(mydict.values())
```

    dict_values(['Anne', 'cat', 25])



```python
# add new data:
mydict['job'] = 'manager'
print(mydict)
```

    {'name': 'Anne', 'pet': 'cat', 'age': 25, 'job': 'manager'}



```python
# remove data:
del(mydict['job'])
print(mydict)
```

    {'name': 'Anne', 'pet': 'cat', 'age': 25}


### (e) *DataFrame*
A DataFrame is a two-dimensional array with heterogeneous data. For this a powerful library is available in Python, called `pandas`. By convention, pandas is usually imported as `import pandas as pd`. In practice, one usually encounters a dataframe when reading data into Python via the `pd.read_csv()` function.


```python
# import pandas
import pandas as pd

# read .csv file to dataframe:
df = pd.read_csv('Datasets/iris.csv')
```


```python
# inspect the dataframe shape:
print(df.shape)
```

    (150, 5)



```python
# print the dataframe head:
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sepal_length</th>
      <th>sepal_width</th>
      <th>petal_length</th>
      <th>petal_width</th>
      <th>species</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <td>1</td>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <td>2</td>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <td>3</td>
      <td>4.6</td>
      <td>3.1</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <td>4</td>
      <td>5.0</td>
      <td>3.6</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
  </tbody>
</table>
</div>




```python
# quary variable types:
print(df.dtypes)
```

    sepal_length    float64
    sepal_width     float64
    petal_length    float64
    petal_width     float64
    species          object
    dtype: object



```python
# descriptive statistics for numeric variables:
df.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sepal_length</th>
      <th>sepal_width</th>
      <th>petal_length</th>
      <th>petal_width</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>count</td>
      <td>150.000000</td>
      <td>150.000000</td>
      <td>150.000000</td>
      <td>150.000000</td>
    </tr>
    <tr>
      <td>mean</td>
      <td>5.843333</td>
      <td>3.057333</td>
      <td>3.758000</td>
      <td>1.199333</td>
    </tr>
    <tr>
      <td>std</td>
      <td>0.828066</td>
      <td>0.435866</td>
      <td>1.765298</td>
      <td>0.762238</td>
    </tr>
    <tr>
      <td>min</td>
      <td>4.300000</td>
      <td>2.000000</td>
      <td>1.000000</td>
      <td>0.100000</td>
    </tr>
    <tr>
      <td>25%</td>
      <td>5.100000</td>
      <td>2.800000</td>
      <td>1.600000</td>
      <td>0.300000</td>
    </tr>
    <tr>
      <td>50%</td>
      <td>5.800000</td>
      <td>3.000000</td>
      <td>4.350000</td>
      <td>1.300000</td>
    </tr>
    <tr>
      <td>75%</td>
      <td>6.400000</td>
      <td>3.300000</td>
      <td>5.100000</td>
      <td>1.800000</td>
    </tr>
    <tr>
      <td>max</td>
      <td>7.900000</td>
      <td>4.400000</td>
      <td>6.900000</td>
      <td>2.500000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# access the dataframe row index:
print(df.index)
```

    RangeIndex(start=0, stop=150, step=1)



```python
# access the dataframe column index (variable names):
print(df.columns)
```

    Index(['sepal_length', 'sepal_width', 'petal_length', 'petal_width',
           'species'],
          dtype='object')



```python
# get usefull information about the data.frame:
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 150 entries, 0 to 149
    Data columns (total 5 columns):
    sepal_length    150 non-null float64
    sepal_width     150 non-null float64
    petal_length    150 non-null float64
    petal_width     150 non-null float64
    species         150 non-null object
    dtypes: float64(4), object(1)
    memory usage: 6.0+ KB


***
## (3) Indexing

### (a) *Indexing a list*
One can access the content of a **list** using square brackets and specifying the desired index location. Alternatively, one can also use logical expressions to filter the content of a list. Note that indexing take place on open range, such that the last index is not contained in the range.


```python
# access the first entry (at index location 0!) of x:
print(x[0])
# access the last entry of x:
print(x[-1])
print(x)
```

    1
    stop
    [1, 'a', 1, 2, 'a', 'b', 4, 'b', 0, 5, 1, 'stop']



```python
# selecting a range:
print(x[2:]) # from 3rd to last
print(x[:2]) # from 1st to 2nd
```

    [1, 2, 'a', 'b', 4, 'b', 0, 5, 1, 'stop']
    [1, 'a']



```python
# access the second list within y:
print(y[1])
```

    ['a', 'b', 'c', 'd']



```python
# hierarchical indexing:
print(y[0][1:])
```

    [2, 3, 4]



```python
# index a string:
print(opinion[0:6])
```

    I hate



```python
# use list comprehension to get only the numeric values in list:
print([i for i in x if isinstance(i,(int,float))])
print([i for i in x if isinstance(i,(str))])
```

    [1, 1, 2, 4, 0, 5, 1]
    ['a', 'a', 'b', 'b', 'stop']


### (b) *Indexing an array*
Arrays are indexed in a similar way to lists, using square brackets.


```python
# indexing with location:
print(nar[:3])
```

    [0 1 2]



```python
# indexing using a boolean:
print(nar[nar<3])
#print(nar<3)
```

    [0 1 2]


### (c) *Indexing a dictionary*
Dictionaries are indexed first by **key**, then by index location.


```python
# example:
mydict = {'name':['Anne','Mike'],'pet':['cat','python'],'age':[25,37]}
print(mydict['pet'][1])
```

    python


### (d) *Indexing a DataFrame*
Dataframe indexing is somewhat more complicated than for other data structures. Indexing a dataframe using a numeric index returns a slice of rows, while using variable names as index returns a slice of columns. If one needs to index across several dimensions, indexers `.loc` or `.iloc` need to be used, depending on whether the index uses values in the dataframe index or not, respectively.


```python
# row slice:
df[:3]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sepal_length</th>
      <th>sepal_width</th>
      <th>petal_length</th>
      <th>petal_width</th>
      <th>species</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <td>1</td>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <td>2</td>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
  </tbody>
</table>
</div>




```python
# column slice:
df[['species','sepal_length']].head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>species</th>
      <th>sepal_length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>setosa</td>
      <td>5.1</td>
    </tr>
    <tr>
      <td>1</td>
      <td>setosa</td>
      <td>4.9</td>
    </tr>
    <tr>
      <td>2</td>
      <td>setosa</td>
      <td>4.7</td>
    </tr>
    <tr>
      <td>3</td>
      <td>setosa</td>
      <td>4.6</td>
    </tr>
    <tr>
      <td>4</td>
      <td>setosa</td>
      <td>5.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# filtering:
df.loc[df.species=='setosa'].head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sepal_length</th>
      <th>sepal_width</th>
      <th>petal_length</th>
      <th>petal_width</th>
      <th>species</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <td>1</td>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <td>2</td>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <td>3</td>
      <td>4.6</td>
      <td>3.1</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <td>4</td>
      <td>5.0</td>
      <td>3.6</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 2D slicing:
df.iloc[:3,[0,3]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sepal_length</th>
      <th>petal_width</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>5.1</td>
      <td>0.2</td>
    </tr>
    <tr>
      <td>1</td>
      <td>4.9</td>
      <td>0.2</td>
    </tr>
    <tr>
      <td>2</td>
      <td>4.7</td>
      <td>0.2</td>
    </tr>
  </tbody>
</table>
</div>




```python
# more advanced filtering (note the use of function np.logical_and()):
df.loc[
    np.logical_and(
        df.species=='versicolor',
        df.sepal_length<5.5
    )
]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>sepal_length</th>
      <th>sepal_width</th>
      <th>petal_length</th>
      <th>petal_width</th>
      <th>species</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>57</td>
      <td>4.9</td>
      <td>2.4</td>
      <td>3.3</td>
      <td>1.0</td>
      <td>versicolor</td>
    </tr>
    <tr>
      <td>59</td>
      <td>5.2</td>
      <td>2.7</td>
      <td>3.9</td>
      <td>1.4</td>
      <td>versicolor</td>
    </tr>
    <tr>
      <td>60</td>
      <td>5.0</td>
      <td>2.0</td>
      <td>3.5</td>
      <td>1.0</td>
      <td>versicolor</td>
    </tr>
    <tr>
      <td>84</td>
      <td>5.4</td>
      <td>3.0</td>
      <td>4.5</td>
      <td>1.5</td>
      <td>versicolor</td>
    </tr>
    <tr>
      <td>93</td>
      <td>5.0</td>
      <td>2.3</td>
      <td>3.3</td>
      <td>1.0</td>
      <td>versicolor</td>
    </tr>
    <tr>
      <td>98</td>
      <td>5.1</td>
      <td>2.5</td>
      <td>3.0</td>
      <td>1.1</td>
      <td>versicolor</td>
    </tr>
  </tbody>
</table>
</div>


