- - -

# 판다스 입문 : 데이터프레임 구성

### Pandas Primer: Constructing DataFrame

* * *

**박 진 수** 교수  
Intelligent Data Semantics Lab  
Seoul National University

- - -

<h3>Table of Contents<span class="tocSkip"></span></h3>
<div class="toc"><ul class="toc-item"><li><span><a href="#판다스-데이터프레임(DataFrame)" data-toc-modified-id="판다스-데이터프레임(DataFrame)-1">판다스 데이터프레임(DataFrame)</a></span></li><li><span><a href="#배열/리스트로-데이터프레임-구성하기" data-toc-modified-id="배열/리스트로-데이터프레임-구성하기-2">배열/리스트로 데이터프레임 구성하기</a></span></li><li><span><a href="#딕셔너리로-데이터프레임-구성하기-:-기초" data-toc-modified-id="딕셔너리로-데이터프레임-구성하기-:-기초-3">딕셔너리로 데이터프레임 구성하기 : 기초</a></span><ul class="toc-item"><li><span><a href="#키-=-열(컬럼)-이름" data-toc-modified-id="키-=-열(컬럼)-이름-3.1">키 = 열(컬럼) 이름</a></span></li><li><span><a href="#열(컬럼)-순서-지정하기" data-toc-modified-id="열(컬럼)-순서-지정하기-3.2">열(컬럼) 순서 지정하기</a></span></li><li><span><a href="#열(컬럼)-이름으로-접근하기" data-toc-modified-id="열(컬럼)-이름으로-접근하기-3.3">열(컬럼) 이름으로 접근하기</a></span><ul class="toc-item"><li><span><a href="#열(컬럼)-자료형은?" data-toc-modified-id="열(컬럼)-자료형은?-3.3.1">열(컬럼) 자료형은?</a></span></li><li><span><a href="#인덱스-값-지정하기" data-toc-modified-id="인덱스-값-지정하기-3.3.2">인덱스 값 지정하기</a></span></li></ul></li></ul></li><li><span><a href="#열(컬럼)과-인덱스-이름을-지정하고-데이터프레임-구성하기" data-toc-modified-id="열(컬럼)과-인덱스-이름을-지정하고-데이터프레임-구성하기-4">열(컬럼)과 인덱스 이름을 지정하고 데이터프레임 구성하기</a></span></li><li><span><a href="#데이터프레임-정보-열람하기" data-toc-modified-id="데이터프레임-정보-열람하기-5">데이터프레임 정보 열람하기</a></span></li><li><span><a href="#딕셔너리로-데이터프레임-구성하기-:-고급" data-toc-modified-id="딕셔너리로-데이터프레임-구성하기-:-고급-6">딕셔너리로 데이터프레임 구성하기 : 고급</a></span></li><li><span><a href="#Lab:-데이터프레임-구성하기" data-toc-modified-id="Lab:-데이터프레임-구성하기-7">Lab: 데이터프레임 구성하기</a></span></li></ul></div>

# 판다스 데이터프레임(DataFrame)

- 2차원의 자료구조다.
    - 2차원 배열 혹은 리스트와 유사한 자료 구조다.
- 시리즈(Series)의 집합이다.
- 행렬(matrix)과 같이 행(row)과 열(column)로 이루어져 있으며, 인덱스를 이용해 접근이 가능하다.
    - 두 개의 축(axis)이 있어 행과 열을 관리한다.
- 데이터프레임도 시리즈처럼 이종 자료형을 담을 수 있다.   

[pandas.DataFrame](https://pandas.pydata.org/pandas-docs/stable/reference/frame.html)
- Two-dimensional size-mutable, potentially heterogeneous tabular data structure with labeled axes (rows and columns). 
- [pandas.**DataFrame**(*data=None, index=None, columns=None, dtype=None, copy=False)*](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html#pandas.DataFrame)
    + ***data*** 에는
         - 1차원의 리스트, 딕셔너리 혹은 시리즈를 값(**value**)으로 갖는 딕셔너리
         - 1차원의 리스트, 딕셔너리 혹은 시리즈의 리스트
         - 시리즈(Series)
         - 데이터프레임(DataFrame)
    + 등이 들어갈 수 있다.


```python
import pandas  # as pd
import numpy   # as np <== numpy도 주로 같이 불러온다.
pandas.__version__
```

# 배열/리스트로 데이터프레임 구성하기


```python
# 넘파이 배열(array)로 데이터프레임을 구성한다.
df1 = pandas.DataFrame(numpy.zeros((2, 3)))
df1
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 파이썬 리스트 자료형으로 데이터프레임을 구성한다.
df2 = pandas.DataFrame([[1, 2, 3], [4, 5, 6]])
df2
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 중첩 리스트(리스트의 리스트: 2차원 리스트)로 데이터프레임을 구성한다.
list_of_list = [
    ['John', 'Tim', 'Elizabeth', 'Bruce', 'Nancy'],
    ['A+', 'B-', 'F'],
    ['M', 'M', 'F', 'M', 'F'],
    [None, {}, 3.14, True]
]

df3 = pandas.DataFrame(list_of_list)
df3
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>Tim</td>
      <td>Elizabeth</td>
      <td>Bruce</td>
      <td>Nancy</td>
    </tr>
    <tr>
      <th>1</th>
      <td>A+</td>
      <td>B-</td>
      <td>F</td>
      <td>None</td>
      <td>None</td>
    </tr>
    <tr>
      <th>2</th>
      <td>M</td>
      <td>M</td>
      <td>F</td>
      <td>M</td>
      <td>F</td>
    </tr>
    <tr>
      <th>3</th>
      <td>None</td>
      <td>{}</td>
      <td>3.14</td>
      <td>True</td>
      <td>None</td>
    </tr>
  </tbody>
</table>
</div>



# 딕셔너리로 데이터프레임 구성하기 : 기초

- 딕셔너리 형태로 구성하는 것이 제일 간편하다.

## 키 = 열(컬럼) 이름


```python
names = ['John', 'Tim', 'Bruce']
grades = ['A+', 'B-', 'F']
d = {'grade': grades, 'name': names}
d
```




    {'grade': ['A+', 'B-', 'F'], 'name': ['John', 'Tim', 'Bruce']}




```python
# 파이썬 딕셔너리 자료형으로 데이터프레임을 생성한다.
# 이렇게 하면 카가 열의 인덱스 값으로 사용된다.
df4 = pandas.DataFrame(d)
df4
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
      <th>grade</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A+</td>
      <td>John</td>
    </tr>
    <tr>
      <th>1</th>
      <td>B-</td>
      <td>Tim</td>
    </tr>
    <tr>
      <th>2</th>
      <td>F</td>
      <td>Bruce</td>
    </tr>
  </tbody>
</table>
</div>



## 열(컬럼) 순서 지정하기

이때 딕셔너리 자료형의 특성 때문에 열의 순서가 임의로 정해질 수 있는데 이를 원하는 순서로 지정하려면 컬럼 값을 지정하면 된다.


```python
# 열의 순서를 정할 수 있다.
df5 = pandas.DataFrame(d, columns=['name', 'grade'])
df5
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
      <th>name</th>
      <th>grade</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>A+</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tim</td>
      <td>B-</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Bruce</td>
      <td>F</td>
    </tr>
  </tbody>
</table>
</div>



## 열(컬럼) 이름으로 접근하기

키가 열의 이름이기 때문에 마치 딕셔너리에 접근하듯이 열(컬럼)의 이름으로 데이터에 접근이 가능하다.


```python
# df5에서 name 열의 데이터를 열람한다.
df5['name']
```




    0     John
    1      Tim
    2    Bruce
    Name: name, dtype: object



또한 클래스의 속성에 접근하듯이 열 이름으로 접근이 가능하다.


```python
# df5에서 name 열의 데이터를 열람한다.
# 위와 동일하게 작동한다.
df5.name
```




    0     John
    1      Tim
    2    Bruce
    Name: name, dtype: object



### 열(컬럼) 자료형은?

각 열의 자료형은 시리즈(Series)이다.


```python
# df5의 grade 열의 자료형을 확인한다.
type(df5.grade)
```




    pandas.core.series.Series



### 인덱스 값 지정하기

인덱스의 값도 지정할 수 있다.


```python
student_id = ['1111', '1112', '1113']
df6 = pandas.DataFrame(d, index=student_id)
df6
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
      <th>grade</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1111</th>
      <td>A+</td>
      <td>John</td>
    </tr>
    <tr>
      <th>1112</th>
      <td>B-</td>
      <td>Tim</td>
    </tr>
    <tr>
      <th>1113</th>
      <td>F</td>
      <td>Bruce</td>
    </tr>
  </tbody>
</table>
</div>



# 열(컬럼)과 인덱스 이름을 지정하고 데이터프레임 구성하기

- 열 이름과 인덱스를 전달인자로 설정할 수 있다.
- 따로 설정하지 않을 경우 기본값(**0**부터 시작하는 정수)으로 설정된다.


```python
df1 = pandas.DataFrame(numpy.random.randn(10, 3),  # shape of (10, 3)
                       index=list('abcdefghij'), 
                       columns=list('ABC'))
df1
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>-0.380326</td>
      <td>1.005693</td>
      <td>-0.933230</td>
    </tr>
    <tr>
      <th>b</th>
      <td>-1.502842</td>
      <td>-2.243511</td>
      <td>1.065208</td>
    </tr>
    <tr>
      <th>c</th>
      <td>1.190737</td>
      <td>-0.564509</td>
      <td>0.971650</td>
    </tr>
    <tr>
      <th>d</th>
      <td>0.191854</td>
      <td>-0.430524</td>
      <td>-0.246978</td>
    </tr>
    <tr>
      <th>e</th>
      <td>-0.135077</td>
      <td>-0.670383</td>
      <td>0.855122</td>
    </tr>
    <tr>
      <th>f</th>
      <td>1.134730</td>
      <td>1.096429</td>
      <td>0.273888</td>
    </tr>
    <tr>
      <th>g</th>
      <td>0.647413</td>
      <td>1.239580</td>
      <td>-0.322709</td>
    </tr>
    <tr>
      <th>h</th>
      <td>0.712009</td>
      <td>0.493667</td>
      <td>-1.117355</td>
    </tr>
    <tr>
      <th>i</th>
      <td>-0.066463</td>
      <td>-0.544168</td>
      <td>0.669985</td>
    </tr>
    <tr>
      <th>j</th>
      <td>-1.173644</td>
      <td>-0.284844</td>
      <td>-1.255652</td>
    </tr>
  </tbody>
</table>
</div>




```python
# --- 각 열의 자료형을 다르게 해서 복잡한 데이터프레임을 만들 수 있다.
df2 = pandas.DataFrame({'A': pandas.Series(list(range(1, 6)), 
                                           index=pandas.date_range('2025-5-12', periods=5),
                                           dtype='float32'),
                        'B': numpy.random.randint(1, 100, size=5),
                        'C': pandas.Categorical(['AAA', 'AA', 'BB', 'B', 'C']),
                        'D': 'pd',
                        'E': pandas.Timestamp('2050-10-9')})
df2
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2025-05-12</th>
      <td>1.0</td>
      <td>33</td>
      <td>AAA</td>
      <td>pd</td>
      <td>2050-10-09</td>
    </tr>
    <tr>
      <th>2025-05-13</th>
      <td>2.0</td>
      <td>87</td>
      <td>AA</td>
      <td>pd</td>
      <td>2050-10-09</td>
    </tr>
    <tr>
      <th>2025-05-14</th>
      <td>3.0</td>
      <td>48</td>
      <td>BB</td>
      <td>pd</td>
      <td>2050-10-09</td>
    </tr>
    <tr>
      <th>2025-05-15</th>
      <td>4.0</td>
      <td>48</td>
      <td>B</td>
      <td>pd</td>
      <td>2050-10-09</td>
    </tr>
    <tr>
      <th>2025-05-16</th>
      <td>5.0</td>
      <td>16</td>
      <td>C</td>
      <td>pd</td>
      <td>2050-10-09</td>
    </tr>
  </tbody>
</table>
</div>




```python
# df2 모든 열의 자료형을 확인한다.
df2.dtypes
```




    A           float32
    B             int64
    C          category
    D            object
    E    datetime64[ns]
    dtype: object



# 데이터프레임 정보 열람하기

[pandas.DataFrame.info](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.info.html?highlight=info#pandas.DataFrame.info)
- Print a concise summary of a DataFrame.
- DataFrame.**info**(*self, verbose=None, buf=None, max_cols=None, memory_usage=None, null_counts=None*)



```python
df2.info()  # info(verbose=True, memory_usage=True)와 같은 결과를 보여준다.
```

    <class 'pandas.core.frame.DataFrame'>
    DatetimeIndex: 5 entries, 2025-05-12 to 2025-05-16
    Freq: D
    Data columns (total 5 columns):
     #   Column  Non-Null Count  Dtype         
    ---  ------  --------------  -----         
     0   A       5 non-null      float32       
     1   B       5 non-null      int64         
     2   C       5 non-null      category      
     3   D       5 non-null      object        
     4   E       5 non-null      datetime64[ns]
    dtypes: category(1), datetime64[ns](1), float32(1), int64(1), object(1)
    memory usage: 385.0+ bytes


# 딕셔너리로 데이터프레임 구성하기 : 고급


```python
# 딕셔너리로 데이터프레임을 구성한다.
d1 = {
    'Name': ['John', 'Tim', 'Elizabeth', 'Bruce', 'Nancy'],
    'Grade': ('A+', 'B-', 'F', 'C0', 'B+'),
    'Gender': ('M', 'M', 'F', 'M', 'F'),
    '비고': [None, (10, 9), 3.14, True, list('xyz')]
}

df1 = pandas.DataFrame(d1)
df1
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
      <th>Name</th>
      <th>Grade</th>
      <th>Gender</th>
      <th>비고</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>A+</td>
      <td>M</td>
      <td>None</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tim</td>
      <td>B-</td>
      <td>M</td>
      <td>(10, 9)</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Elizabeth</td>
      <td>F</td>
      <td>F</td>
      <td>3.14</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Bruce</td>
      <td>C0</td>
      <td>M</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Nancy</td>
      <td>B+</td>
      <td>F</td>
      <td>[x, y, z]</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 앞서 정의한 딕셔너리 d1으로 인덱스를 지정하고 데이터프레임을 구성한다.
df2 = pandas.DataFrame(d1, index=list('abcde'))
df2
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
      <th>Name</th>
      <th>Grade</th>
      <th>Gender</th>
      <th>비고</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>John</td>
      <td>A+</td>
      <td>M</td>
      <td>None</td>
    </tr>
    <tr>
      <th>b</th>
      <td>Tim</td>
      <td>B-</td>
      <td>M</td>
      <td>(10, 9)</td>
    </tr>
    <tr>
      <th>c</th>
      <td>Elizabeth</td>
      <td>F</td>
      <td>F</td>
      <td>3.14</td>
    </tr>
    <tr>
      <th>d</th>
      <td>Bruce</td>
      <td>C0</td>
      <td>M</td>
      <td>True</td>
    </tr>
    <tr>
      <th>e</th>
      <td>Nancy</td>
      <td>B+</td>
      <td>F</td>
      <td>[x, y, z]</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 딕셔너리를 매핑값으로 가지는 딕셔너리로 데이터프레임을 구성한다.
# 키는 데이터프레임의 열 이름으로 되며,
# 매핑값의 키는 데이터프레임의 인덱스가 된다.
d2 = {
    'Name': {
        'a': 'John', 
        'b': 'Tim', 
        'c': 'Elizabeth', 
        'd': 'Bruce', 
        'e': 'Nancy'
    },
    'Grade': {
        'a': 'A+', 
        'b': 'B-', 
        'c': 'F', 
        'd': 'C0', 
        'e': 'B+'
    },
    'Gender': {
        'a': 'M', 
        'b': 'M', 
        'c': 'F', 
        'd': 'M', 
        'e': 'F'
    },
    '비고': {
        'a': None, 
        'b': (10, 9), 
        'c': 3.14, 
        'd': True, 
        'e': list('xyz')
    }
}

df3 = pandas.DataFrame(d2)
df3
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
      <th>Name</th>
      <th>Grade</th>
      <th>Gender</th>
      <th>비고</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>John</td>
      <td>A+</td>
      <td>M</td>
      <td>None</td>
    </tr>
    <tr>
      <th>b</th>
      <td>Tim</td>
      <td>B-</td>
      <td>M</td>
      <td>(10, 9)</td>
    </tr>
    <tr>
      <th>c</th>
      <td>Elizabeth</td>
      <td>F</td>
      <td>F</td>
      <td>3.14</td>
    </tr>
    <tr>
      <th>d</th>
      <td>Bruce</td>
      <td>C0</td>
      <td>M</td>
      <td>True</td>
    </tr>
    <tr>
      <th>e</th>
      <td>Nancy</td>
      <td>B+</td>
      <td>F</td>
      <td>[x, y, z]</td>
    </tr>
  </tbody>
</table>
</div>




```python
# --- 인덱스와 열 이름을 지정하고 데이터프레임을 구성한다. 
# 앞서 정의한 딕셔너리 d2에서 인덱스는 'a', 'c', 'e'만, 
# 열은 'Name', 'Grade'만 지정하고 데이터프레임을 구성한다. 
df4 = pandas.DataFrame(d2, 
                       index=['a', 'c', 'e'], 
                       columns=['Name', 'Grade'])
df4
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
      <th>Name</th>
      <th>Grade</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>John</td>
      <td>A+</td>
    </tr>
    <tr>
      <th>c</th>
      <td>Elizabeth</td>
      <td>F</td>
    </tr>
    <tr>
      <th>e</th>
      <td>Nancy</td>
      <td>B+</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 매핑값의 키가 다르면?
d3 = {
    'Name': {
        'a': 'John', 
        'b': 'Tim', 
        'c': 'Elizabeth', 
        'd': 'Bruce', 
        'e': 'Nancy'
    },
    'Grade': {
        'a': 'A+', 
        'x': 'B-', 
        'b': 'F', 
        'y': 'C0', 
        'c': 'B+'
    },
    'Gender': {
        'x': 'M', 
        'b': 'M', 
        'y': 'F', 
        'd': 'M', 
        'x': 'F'
    },
    '비고': {
        'e': None, 
        'd': (10, 9), 
        'c': 3.14, 
        'b': True, 
        'a': list('xyz')
    }
}

df5 = pandas.DataFrame(d3)
df5
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
      <th>Name</th>
      <th>Grade</th>
      <th>Gender</th>
      <th>비고</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>John</td>
      <td>A+</td>
      <td>NaN</td>
      <td>[x, y, z]</td>
    </tr>
    <tr>
      <th>b</th>
      <td>Tim</td>
      <td>F</td>
      <td>M</td>
      <td>True</td>
    </tr>
    <tr>
      <th>c</th>
      <td>Elizabeth</td>
      <td>B+</td>
      <td>NaN</td>
      <td>3.14</td>
    </tr>
    <tr>
      <th>d</th>
      <td>Bruce</td>
      <td>NaN</td>
      <td>M</td>
      <td>(10, 9)</td>
    </tr>
    <tr>
      <th>e</th>
      <td>Nancy</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None</td>
    </tr>
    <tr>
      <th>x</th>
      <td>NaN</td>
      <td>B-</td>
      <td>F</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>y</th>
      <td>NaN</td>
      <td>C0</td>
      <td>F</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 딕셔너리를 담고 있는 리스트로 데이터프레임을 구성한다.
# 이 경우 딕셔너리의 키는 데이터프레임의 인덱스가 아니라 열 이름으로 된다.
list_of_dict = [
    {
        'a': 'John', 
        'b': 'Tim', 
        'c': 'Elizabeth', 
        'd': 'Bruce', 
        'e': 'Nancy'
    },
    {
        'a': 'A+', 
        'b': 'B-', 
        'c': 'F', 
        'd': 'C0', 
        'e': 'B+'
    },
    {
        'a': 'M', 
        'b': 'M', 
        'c': 'F', 
        'd': 'M', 
        'e': 'F'
    },
    {
        'a': None, 
        'b': (10, 9), 
        'c': 3.14, 
        'd': True, 
        'e': list('xyz')
    }      
]

df6 = pandas.DataFrame(list_of_dict)
df6
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
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
      <th>e</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>Tim</td>
      <td>Elizabeth</td>
      <td>Bruce</td>
      <td>Nancy</td>
    </tr>
    <tr>
      <th>1</th>
      <td>A+</td>
      <td>B-</td>
      <td>F</td>
      <td>C0</td>
      <td>B+</td>
    </tr>
    <tr>
      <th>2</th>
      <td>M</td>
      <td>M</td>
      <td>F</td>
      <td>M</td>
      <td>F</td>
    </tr>
    <tr>
      <th>3</th>
      <td>None</td>
      <td>(10, 9)</td>
      <td>3.14</td>
      <td>True</td>
      <td>[x, y, z]</td>
    </tr>
  </tbody>
</table>
</div>




```python
# --- 전치를 하면 원하는 형태로 바꿀 수 있다.
# df6을 전치(transpose)하고 열 이름을 지정하면 원하는 형태로 바꿀 수 있다.
df7 = df6.T
df7.columns = ['Name', 'Grade', 'Gender', '비고']
df7
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
      <th>Name</th>
      <th>Grade</th>
      <th>Gender</th>
      <th>비고</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>John</td>
      <td>A+</td>
      <td>M</td>
      <td>None</td>
    </tr>
    <tr>
      <th>b</th>
      <td>Tim</td>
      <td>B-</td>
      <td>M</td>
      <td>(10, 9)</td>
    </tr>
    <tr>
      <th>c</th>
      <td>Elizabeth</td>
      <td>F</td>
      <td>F</td>
      <td>3.14</td>
    </tr>
    <tr>
      <th>d</th>
      <td>Bruce</td>
      <td>C0</td>
      <td>M</td>
      <td>True</td>
    </tr>
    <tr>
      <th>e</th>
      <td>Nancy</td>
      <td>B+</td>
      <td>F</td>
      <td>[x, y, z]</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 딕셔너리를 담고 있는 리스트로 데이터프레임을 구성한다.
# 딕셔너리의 키는 데이터프레임의 열 이름으로 된다.
list_of_dict2 = [
    {
        'Name': 'John',
        'Grade': 'A+',
        'Gender': 'M',
        '비고': None
    },
    {
        'Name': 'Tim',
        'Grade': 'B-', 
        'Gender': 'M', 
        '비고': (10, 9),  
    },

    {
        'Name': 'Elizabeth',
        'Grade': 'F', 
        'Gender': 'F', 
        '비고': 3.14,   
    },

    {
        'Name': 'Bruce',
        'Grade': 'C0', 
        'Gender': 'M', 
        '비고': True,     
    },

    {
        'Name': 'Nancy',
        'Grade': 'B+',
        'Gender': 'F',
        '비고': list('xyz')   
    }
]

df8 = pandas.DataFrame(list_of_dict2)
df8
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
      <th>Name</th>
      <th>Grade</th>
      <th>Gender</th>
      <th>비고</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>A+</td>
      <td>M</td>
      <td>None</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tim</td>
      <td>B-</td>
      <td>M</td>
      <td>(10, 9)</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Elizabeth</td>
      <td>F</td>
      <td>F</td>
      <td>3.14</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Bruce</td>
      <td>C0</td>
      <td>M</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Nancy</td>
      <td>B+</td>
      <td>F</td>
      <td>[x, y, z]</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 시리즈를 매핑값으로 하는 딕셔너리로 데이터프레임을 구성한다.
d_series = {
    'Name': pandas.Series(['John', 'Tim', 'Elizabeth', 'Bruce', 'Nancy']),
    'Grade': pandas.Series(('A+', 'B-', 'F', 'C0', 'B+')),
    'Gender': pandas.Series(('M', 'M', 'F', 'M', 'F')),
    '비고': pandas.Series([None, (10, 9), 3.14, True, list('xyz')])
}

df9 = pandas.DataFrame(d_series)
df9
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
      <th>Name</th>
      <th>Grade</th>
      <th>Gender</th>
      <th>비고</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>A+</td>
      <td>M</td>
      <td>None</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tim</td>
      <td>B-</td>
      <td>M</td>
      <td>(10, 9)</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Elizabeth</td>
      <td>F</td>
      <td>F</td>
      <td>3.14</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Bruce</td>
      <td>C0</td>
      <td>M</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Nancy</td>
      <td>B+</td>
      <td>F</td>
      <td>[x, y, z]</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 시리즈로 데이터프레임을 구성한다.
# 시리즈의 이름이 데이터프레임의 열 이름이 된다.
s_name = pandas.Series(['John', 'Tim', 'Elizabeth', 'Bruce', 'Nancy'], name='Name')
s_grade = pandas.Series(('A+', 'B-', 'F', 'C0', 'B+'), name='Grade')
s_gender = pandas.Series(('M', 'M', 'F', 'M', 'F'), name='Gender')
s_remarks = pandas.Series([None, (10, 9), 3.14, True, list('xyz')])
s_remarks.name = '비고'

df_series = pandas.concat(__TODO__, axis='columns')
print(df_series)
```


```python
# 시리즈로 데이터프레임을 구성한다.
# 시리즈의 이름이 데이터프레임의 열 이름이 된다.
s_name = pandas.Series(['John', 'Tim', 'Elizabeth', 'Bruce', 'Nancy'], name='Name')
s_grade = pandas.Series(('A+', 'B-', 'F', 'C0', 'B+'), name='Grade')
s_gender = pandas.Series(('M', 'M', 'F', 'M', 'F'), name='Gender')
s_remarks = pandas.Series([None, (10, 9), 3.14, True, list('xyz')])
s_remarks.name = '비고'

df_series = pandas.concat([s_name, s_grade, s_gender, s_remarks], axis='columns')
df_series
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
      <th>Name</th>
      <th>Grade</th>
      <th>Gender</th>
      <th>비고</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>John</td>
      <td>A+</td>
      <td>M</td>
      <td>None</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tim</td>
      <td>B-</td>
      <td>M</td>
      <td>(10, 9)</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Elizabeth</td>
      <td>F</td>
      <td>F</td>
      <td>3.14</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Bruce</td>
      <td>C0</td>
      <td>M</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Nancy</td>
      <td>B+</td>
      <td>F</td>
      <td>[x, y, z]</td>
    </tr>
  </tbody>
</table>
</div>



# Lab: 데이터프레임 구성하기

---

다음 내용의 데이터를 담은 데이터프레임을 구성해 보자.

Index|Title|Artist|Length|Year
:-:|:-:|:-:|:-:|:-:
0|Skyfall|Adele|4:46|2012
1|Lose Yourself|Eminem|5:26|2002
2|Another Brick in the Wall|Pink Floyd|3:59|1979
3|Use Somebody|Kings of Leon|3:51|2008
4|Treasure|Bruno Mars|2:58|2013

- Title, Artist, Length는 문자열(string)로, Year는 정수형(int)으로 저장한다.
- 결과로 만들어진 데이터프레임 출력한다.

---

**답**


```python
# Your answer here
```

- - -

# THE END
