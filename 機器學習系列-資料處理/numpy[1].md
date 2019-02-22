[numpy1](https://www.jianshu.com/p/166e04e7b659)
[numpy2](https://www.jianshu.com/p/520084e85f2d)
[numpy3](https://www.jianshu.com/p/98deb28eacbe)
## 匯入numpy ##
```python
import numpy as np    #使用np來簡化輸入名稱
```
## Numpy數據類型 ##
- **每個python內建類型都有一個唯一定義它的字符代碼：**
'b'：布爾值
'i'：符號整數
'u'：無符號整數
'f'：浮點
'c'：複數浮點
'm'：時間間隔
'M'：日期時間
'O'：Python 對象
'S', 'a'：字節串
'U'：Unicode
'V'：原始數據（void）
第一個字符指定數據的類型，其餘字符指定每個項目的字節數，Unicode除外，其中它被解釋為字符數。項目大小必須對應於現有類型，否則將出現錯誤。
前綴<或>。<是小端（最小有效字節存儲在最小地址中）。>是大端（最大有效字節存儲在最小地址中）。
```python
import numpy as np 
a = np.dtype('<i2')
a1 = np.array([32766,32768],dtype=a)
b = np.dtype('>i2')
b1 = np.array([32766,32768],dtype=b)
print('i2內建數據類型:','\n<i2:',a,'\n>i2:',b,'\n32768超過i2大小->溢位:','\na1:',a1,'\nb1:',b1)
```
>i2內建數據類型: 
<i2: int16 
>\>i2: >i2 
32768超過i2大小->溢位: 
a1: [ 32766 -32768] 
b1: [ 32766 -32768]

- **NumPy 數字類型是dtype對象的實例:**   
![](https://upload-images.jianshu.io/upload_images/13539817-f86f100c7eb892c1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- **自定義dtype數據類型:**
1) 方法一
```python
import numpy as np 
student = np.dtype([('name','S20'),  ('age',  'i1'),  ('student_ID',  'i4')]) 
Department_of_Chemistry_student = np.array([('jeff',  21,  50),('dora',  18,  75)], dtype = student)
print('學生結構:\n',student)
print('化學系學生的名子:\n',Department_of_Chemistry_student['name'],'\n化學系學生的年齡:\n',Department_of_Chemistry_student['age'])
print('索引0的學生資料:\n',Department_of_Chemistry_student[0])
```
>學生結構:
 [('name', 'S20'), ('age', 'i1'), ('student_ID', '<i4')]
化學系學生的名子:
 [b'jeff' b'dora'] 
化學系學生的年齡:
 [21 18]
索引0的學生資料:
 (b'jeff', 21, 50)

2) 方法二
```python
import numpy as np
new_student = np.dtype({
    'names':['name','age','weight(kg)','height(cm)'],
    'formats':['S30','i','f','f']}, align=True)
new_Department_of_Chemistry_student = np.array([('Zhang',32,72.5,167),
              ('Wang',24,65,170)],dtype=new_student)
print('學生結構:\n',new_student)
print('化學系學生的名子:\n',new_Department_of_Chemistry_student['name'],'\n化學系學生的年齡:\n',new_Department_of_Chemistry_student['age'])
```
>學生結構:
 {'names':['name','age','weight(kg)','height(cm)'], 'formats':['S30','<i4','<f4','<f4'], 'offsets':[0,32,36,40], 'itemsize':44, 'aligned':True}
化學系學生的名子:
 [b'Zhang' b'Wang'] 
化學系學生的年齡:
 [32 24]
>>offsets:
結構數據的byte偏移量，S以4byte為單位(30視為32)，'i4'=32bit=4byte，'f4'=32bit=4byte
itemsize:
結構數據的總大小(byte)
aligned:
>>數據是否[對齊](https://baike.baidu.com/item/%E5%AD%97%E8%8A%82%E5%AF%B9%E9%BD%90)

- **NumPy字節(byte順序)交換**  
numpy.ndarray.byteswap（）函數在兩個表示之間切換：bigendian(大端)和little-endian(小端)。  
![](https://upload-images.jianshu.io/upload_images/13539817-bafac9d58f7cf8ce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)                                
```python
import numpy as np 
a = np.array([1,  256,  8755], dtype = np.int16)  
print('數組:\n',a)
print('十六進制表示記憶體中的資料:')
print(np.array([hex(a[j])for j in range(3)])) 
print('\n數組(調用byteswap()函數後):')  
print(a.byteswap(True)) 
print('十六進制表示記憶體中的資料:')
print(np.array([hex(a[j])for j in range(3)]))
```
>數組:
 [   1  256 8755]
十六進制表示記憶體中的資料:
['0x1' '0x100' '0x2233']
>數組(調用byteswap()函數後):
[  256     1 13090]
十六進制表示記憶體中的資料:
['0x100' '0x1' '0x3322']

- **數據類型轉換**
astype( )函數  
```python
import numpy as np 
a = np.array([10,20,30],dtype=np.int32)
print('dtype:',a.dtype,'a:',a)
b = a.astype(np.float32)
print('dtype:',b.dtype,'b:',b)
```
>dtype: int32 a: [10 20 30]
dtype: float32 b: [10. 20. 30.]

補充:缺省值(NaN)
![](https://upload-images.jianshu.io/upload_images/13539817-bc62ae6f6916f9b7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 數組 ##
### 數組基本概念 ###
- **python list與numpy.array差異**
python list儲存的是python變數，而python變數並不像C語言一樣有指定資料型態來固定儲存的空間大小，python變數是一組指向[複合式C語言結構](https://zh.wikipedia.org/wiki/%E7%BB%93%E6%9E%84%E4%BD%93_(C%E8%AF%AD%E8%A8%80))的指標，所以python變數可以指定變數為任意資料型態，使用起來較為方便，但在處理大型運算時效能相當的差，此時我們會改用numpy.array來固定資料型態(dtype)與儲存的空間大小，從而增加運算效率。
shape數組的形狀，zero matrix shape = (2,1,3)，[ [ [0, 0, 0] ],[ [0, 0, 0] ] ]，越左邊的數字越外層，由內往外疊加。
ex.  zero matrix shape = (2,1) = [ [0],[0] ] = $\begin{pmatrix} 0\\0 \end{pmatrix}，2 row\ 1column $。
ex.  zero matrix shape = (2,2) = [ [0,0] , [0,0] ] = $\begin{pmatrix} 0&0\\0&0 \end{pmatrix}，2 row\ 2column $。

#### 建立矩陣 ####
1) np.array()：由list建立矩陣
```python
list1 = [[1,2,3],[4,5,6],(7,8,9)]
data0 = np.array(list1,dtype=np.float32)
print('data0:\n',data0)
data1 = np.array([[10,11,12],[13,14,15]],dtype=np.int)
print('data1:\n',data1)
```
>data0:
 [[1. 2. 3.]
 [4. 5. 6.]
 [7. 8. 9.]]
>data1:
 >[[10 11 12]
> [13 14 15]]

2) zero()：建立零矩陣
```python
np.zeros((2,10),dtype=int)
```
>array([
>[0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
>[0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
>])

3) ones()：建立全為１的矩陣
```python
np.ones((2,10),dtype=int)
```
>array([[1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
>       [1, 1, 1, 1, 1, 1, 1, 1, 1, 1]])

4) np.full()：建立全為任意數的矩陣
```python
np.full((2,4),0.98,dtype=float)
```
>array([[0.98, 0.98, 0.98, 0.98],
>       [0.98, 0.98, 0.98, 0.98]])

5) np.linspace()：建立固定數量平均分佈於兩值之間 ●----●
```python
np.linspace(0,10,5)
```
>array([ 0. ,  2.5,  5. ,  7.5, 10. ])

6) np.arange()：建立固定間隔依序填滿矩陣 ●----○
```python
np.arange(0,10,2)
```
>array([0, 2, 4, 6, 8])

7) np.eye()：建立單位矩陣
```python
np.eye(3)
```
>array([[1., 0., 0.],
>       [0., 1., 0.],
>       [0., 0., 1.]])

8) np.empty()：建立未初始化矩陣(值不固定，值為原記憶體中的值)
```python
np.empty((2,2))
```
>array([[ 2.5,  5. ],
       [ 7.5, 10. ]])

|||
| ------------------------------------------------------------ | ------------------- |
| [empty_like(prototype[, dtype, order, subok])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.empty_like.html#numpy.empty_like) | 將數組轉成empty形式 |
| [ones_like(a[, dtype, order, subok])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ones_like.html#numpy.ones_like) | 將數組轉成ones形式  |
| [zeros_like(a[, dtype, order, subok])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.zeros_like.html#numpy.zeros_like) | 將數組轉成zeros形式 |
| [full_like(a, fill_value[, dtype, order, subok])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.full_like.html#numpy.full_like) | 將數組轉成full形式  |

#### 數組的屬性 ####
```python
a = np.array([[1,2,3],[4,5,6]])
print('a:',a)
print('ndim(維度):',a.ndim)
print('shape(形狀):',a.shape)
print('dtype(類型):',a.dtype)
print('size(元素數量):',a.size)
print('nbytes(int32*6=24byte):',a.nbytes)
print('itemsize(元素byte數):',a.itemsize)
```
>a: [[1 2 3]
 [4 5 6]]
ndim(維度): 2
shape(形狀): (2, 3)
dtype(類型): int32
size(元素數量): 6
nbytes(int32*6=24byte): 24
itemsize(元素byte數): 4

#### ufunc ####
通用函數（或簡稱為[ufunc](https://docs.scipy.org/doc/numpy/glossary.html#term-ufunc)）是一種[`ndarrays`](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.html#numpy.ndarray "numpy.ndarray")以逐元素方式運行的函數，支持[陣列廣播](https://docs.scipy.org/doc/numpy/reference/ufuncs.html#ufuncs-broadcasting)，[類型轉換](https://docs.scipy.org/doc/numpy/reference/ufuncs.html#ufuncs-casting)和其他一些標準功能。也就是說，ufunc是一個函數的“ 矢量化 ”包裝器，它接受固定數量的特定輸入並產生固定數量的特定輸出。

1) ufunc.reduce()  
![](https://upload-images.jianshu.io/upload_images/13539817-2b461f2d73d63155.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2) ufunc.accumulate()  
![](https://upload-images.jianshu.io/upload_images/13539817-9d9cb7ee33149e04.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3) ufunc.reduceat()  
![](https://upload-images.jianshu.io/upload_images/13539817-a127835bf6aab80e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

4) ufunc.outer()  
![](https://upload-images.jianshu.io/upload_images/13539817-cbd6e16bf8da0f1b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

5) ufunc.at()  
![](https://upload-images.jianshu.io/upload_images/13539817-f8c350202d874dbf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

|||
| ------------------------------------------------------------ | ------------------------------------------------------ |
| [ufunc.reduce(a[, axis, dtype, out, keepdims])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ufunc.reduce.html#numpy.ufunc.reduce) | 減少一個接一個的尺寸，由沿一個軸施加ufunc。            |
| [ufunc.accumulate(array[, axis, dtype, out])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ufunc.accumulate.html#numpy.ufunc.accumulate) | 累計將運算符應用於所有元素的結果。                     |
| [ufunc.reduceat(a, indices[, axis, dtype, out])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ufunc.reduceat.html#numpy.ufunc.reduceat) | 在單個軸上使用指定切片執行（局部）縮減。               |
| [ufunc.outer(A, B, **kwargs)](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ufunc.outer.html#numpy.ufunc.outer) | 應用ufunc 運到所有對（a，b）用在甲和b在乙。            |
| [ufunc.at(a, indices[, b])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ufunc.at.html#numpy.ufunc.at) | 對'index'指定的元素在操作數'a'上執行無緩衝的就地操作。 |


#### 匯入數組 ####
| [array(object[, dtype, copy, order, subok, ndmin])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.array.html#numpy.array) | 創建一個數組。                           |
| ------------------------------------------------------------ | ---------------------------------------- |
| [asarray(a[, dtype, order])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.asarray.html#numpy.asarray) | 將輸入轉換為數組。                       |
| [asanyarray(a[, dtype, order])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.asanyarray.html#numpy.asanyarray) | 將輸入轉換為ndarray，但通過ndarray子類。 |
| [ascontiguousarray(a[, dtype])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ascontiguousarray.html#numpy.ascontiguousarray) | 在內存中返回一個連續的數組（C順序）。    |
| [asmatrix(data[, dtype])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.asmatrix.html#numpy.asmatrix) | 將輸入解釋為矩陣。                       |
| [copy(a[, order])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.copy.html#numpy.copy) | 返回給定對象的數組副本。                 |
| [frombuffer(buffer[, dtype, count, offset])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.frombuffer.html#numpy.frombuffer) | 將緩衝區解釋為一維數組。                 |
| [fromfile(file[, dtype, count, sep])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.fromfile.html#numpy.fromfile) | 根據文本或二進製文件中的數據構造數組。   |
| [fromfunction(function, shape, **kwargs)](https://docs.scipy.org/doc/numpy/reference/generated/numpy.fromfunction.html#numpy.fromfunction) | 通過在每個坐標上執行函數來構造數組。     |
| [fromiter(iterable, dtype[, count])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.fromiter.html#numpy.fromiter) | 從可迭代對象創建新的1維數組。            |
| [fromstring(string[, dtype, count, sep])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.fromstring.html#numpy.fromstring) | 從字符串中的文本數據初始化的新1-D數組。  |
| [loadtxt(fname[, dtype, comments, delimiter, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.loadtxt.html#numpy.loadtxt) | 從文本文件加載數據。                     |


### 隨機數(亂數)  ###
- **隨機數種子**
1. 隨機數是由[隨機數種子](https://baike.baidu.com/item/%E9%9A%8F%E6%9C%BA%E7%A7%8D%E5%AD%90)根據一定的計算方法計算出來的數值。只要計算方法固定，隨機種子固定，那麼產生的隨機數就固定。
2. python與numpy默認情況下隨機數種子來自系統時鐘

- **隨機生成器**
```python
np.random.seed(1)
z0 = np.random.randint(0,10,10)
z1 = np.random.randint(0,10,10)
print('seed(1):')
print('z0:',z0)
print('z1:',z1)
np.random.seed(1)
z2 = np.random.randint(0,10,10)
z3 = np.random.randint(0,10,10)
print('seed(1):')
print('z2:',z2)
print('z3:',z3)
np.random.seed()
print('seed():')
z4 = np.random.randint(0,10,10)
z5 = np.random.randint(0,10,10)
print('z4:',z4)
print('z5:',z5)
```
>seed(1):
z0: [5 8 9 5 0 0 1 7 6 9]
z1: [2 4 5 2 4 2 4 7 7 9]
seed(1):
z2: [5 8 9 5 0 0 1 7 6 9]
z3: [2 4 5 2 4 2 4 7 7 9]
seed():
>z4: [0 5 4 3 4 0 0 6 8 8]
z5: [9 8 1 5 3 3 3 7 7 1]

| Random generator | |
| ------------------------------------------------------------ | ---------------------------------------- |
| [RandomState](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.RandomState.html#numpy.random.RandomState) | Mersenne   Twister偽隨機數發生器的容器。 |
| [seed([seed])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.seed.html#numpy.random.seed) | 種子。                                   |
| [get_state()](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.get_state.html#numpy.random.get_state) | 返回表示生成器內部狀態的元組。           |
| [set_state(state)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.set_state.html#numpy.random.set_state) | 從元組設置生成器的內部狀態。             |

- **簡單隨機數**

| Simple   random data                                         |                                                |
| ------------------------------------------------------------ | ---------------------------------------------- |
| [rand(d0, d1, ..., dn)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.rand.html#numpy.random.rand) | 給定形狀的隨機值。                             |
| [randn(d0, d1, ..., dn)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.randn.html#numpy.random.randn) | 從“標準正態”分佈中返回一個樣本（或樣本）。     |
| [randint(low[, high, size, dtype])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.randint.html#numpy.random.randint) | 將隨機整數從低（包含）返回到高（不包括）。●----○     |
| [random_integers(low[, high, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.random_integers.html#numpy.random.random_integers) | np.int類型的隨機整數介於低和高之間，包括在內。●----● |
| [random_sample([size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.random_sample.html#numpy.random.random_sample) | 在半開區間[0.0,1.0]中返回隨機浮點數。          |
| [random([size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.random.html#numpy.random.random) | 在半開區間[0.0,1.0]中返回隨機浮點數。          |
| [ranf([size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.ranf.html#numpy.random.ranf) | 在半開區間[0.0,1.0]中返回隨機浮點數。          |
| [sample([size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.sample.html#numpy.random.sample) | 在半開區間[0.0,1.0]中返回隨機浮點數。          |
| [choice(a[, size, replace, p])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.choice.html#numpy.random.choice) | 從給定的1-D陣列生成隨機樣本，可設置不重複取樣。                    |
| [bytes(length)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.bytes.html#numpy.random.bytes) | 返回隨機字節。                                 |

- **分佈函數**

| Distributions                                                |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [beta(a, b[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.beta.html#numpy.random.beta) | 從Beta分佈中抽取樣本。                                       |
| [binomial(n, p[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.binomial.html#numpy.random.binomial) | 從二項分佈中抽取樣本。                                       |
| [chisquare(df[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.chisquare.html#numpy.random.chisquare) | 從卡方分佈中抽取樣本。                                       |
| [dirichlet(alpha[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.dirichlet.html#numpy.random.dirichlet) | 從Dirichlet分佈中抽取樣本。                                  |
| [exponential([scale, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.exponential.html#numpy.random.exponential) | 從指數分佈中抽取樣本。                                       |
| [f(dfnum, dfden[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.f.html#numpy.random.f) | 從F分佈中抽取樣本。                                          |
| [gamma(shape[, scale, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.gamma.html#numpy.random.gamma) | 從Gamma分佈中抽取樣本。                                      |
| [geometric(p[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.geometric.html#numpy.random.geometric) | 從幾何分佈中抽取樣本。                                       |
| [gumbel([loc, scale, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.gumbel.html#numpy.random.gumbel) | 從Gumbel分佈中抽取樣本。                                     |
| [hypergeometric(ngood, nbad, nsample[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.hypergeometric.html#numpy.random.hypergeometric) | 從超幾何分佈中抽取樣本。                                     |
| [laplace([loc, scale, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.laplace.html#numpy.random.laplace) | 從拉普拉斯或雙指數分佈中抽取具有指定位置（或平均值）和比例（衰減）的樣本。 |
| [logistic([loc, scale, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.logistic.html#numpy.random.logistic) | 從邏輯分佈中抽取樣本。                                       |
| [lognormal([mean, sigma, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.lognormal.html#numpy.random.lognormal) | 從對數正態分佈中抽取樣本。                                   |
| [logseries(p[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.logseries.html#numpy.random.logseries) | 從對數級數分佈中抽取樣本。                                   |
| [multinomial(n, pvals[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.multinomial.html#numpy.random.multinomial) | 從多項分佈中抽取樣本。                                       |
| [multivariate_normal(mean, cov[, size, ...)]](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.multivariate_normal.html#numpy.random.multivariate_normal) | 從多元正態分佈中抽取隨機樣本。                               |
| [negative_binomial(n, p[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.negative_binomial.html#numpy.random.negative_binomial) | 從負二項分佈中抽取樣本。                                     |
| [noncentral_chisquare(df, nonc[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.noncentral_chisquare.html#numpy.random.noncentral_chisquare) | 從非中心卡方分佈中抽取樣本。                                 |
| [noncentral_f(dfnum, dfden, nonc[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.noncentral_f.html#numpy.random.noncentral_f) | 從非中心F分佈中抽取樣本。                                    |
| [normal([loc, scale, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.normal.html#numpy.random.normal) | 從正態（高斯）分佈中抽取隨機樣本。                           |
| [pareto(a[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.pareto.html#numpy.random.pareto) | 從具有指定形狀的Pareto   II或Lomax分佈中抽取樣本。           |
| [poisson([lam, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.poisson.html#numpy.random.poisson) | 從泊松分佈中抽取樣本。                                       |
| [power(a[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.power.html#numpy.random.power) | 從具有正指數a-1的功率分佈中繪製[0,1]中的樣本。               |
| [rayleigh([scale, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.rayleigh.html#numpy.random.rayleigh) | 從瑞利分佈中抽取樣本。                                       |
| [standard_cauchy([size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.standard_cauchy.html#numpy.random.standard_cauchy) | 從模式=   0的標準Cauchy分佈中抽取樣本。                      |
| [standard_exponential([size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.standard_exponential.html#numpy.random.standard_exponential) | 從標準指數分佈中抽取樣本。                                   |
| [standard_gamma(shape[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.standard_gamma.html#numpy.random.standard_gamma) | 從標準Gamma分佈中抽取樣本。                                  |
| [standard_normal([size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.standard_normal.html#numpy.random.standard_normal) | 從標準正態分佈中繪製樣本（均值=   0，stdev = 1）。           |
| [standard_t(df[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.standard_t.html#numpy.random.standard_t) | 從具有df自由度的標準Student t分佈中抽取樣本。                |
| [triangular(left, mode, right[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.triangular.html#numpy.random.triangular) | 從間隔上的三角形分佈中抽取樣本。[left, right]                |
| [uniform([low, high, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.uniform.html#numpy.random.uniform) | 從均勻分佈中抽取樣本。                                       |
| [vonmises(mu, kappa[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.vonmises.html#numpy.random.vonmises) | 從von   Mises分佈中抽取樣本。                                |
| [wald(mean, scale[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.wald.html#numpy.random.wald) | 從Wald或逆高斯分佈中繪製樣本。                               |
| [weibull(a[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.weibull.html#numpy.random.weibull) | 從Weibull分佈中抽取樣本。                                    |
| [zipf(a[, size])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.zipf.html#numpy.random.zipf) | 從Zipf分佈中提取樣本。                                       |

- **排序**

| Permutations                                                 |                                |
| ------------------------------------------------------------ | ------------------------------ |
| [shuffle(x)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.shuffle.html#numpy.random.shuffle) | 通過改組其內容來就地修改序列。 |
| [permutation(x)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.random.permutation.html#numpy.random.permutation) | 隨機置換序列，或返回置換範圍。 |

- **隨機數應用**  
![](https://upload-images.jianshu.io/upload_images/13539817-9faa00ddd526efe9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   
模擬由lognormal分佈10000群體中隨機抽取35個樣本重複1000次，觀察群體參數與樣本統計量以及非常態分怖群體是否接近卡方分佈與T分佈。
```python
import numpy as np
import matplotlib.pyplot as plt
population = 10000
sample_num = 35
sampling_num = 1000
np.random.seed(1)
# z = np.random.uniform(0,100,(population))
a = np.round(np.random.lognormal(1,1,(population))+8,2) #population個lognormal隨機分佈(μ=1,σ=1)值，取小數以下2位，
np.random.seed()

data1 = np.zeros((sampling_num,sample_num))
for num in range(sampling_num):
    data1[num] = [a[choice1] for choice1 in np.random.choice(population,sample_num,replace=False)]
s_std = np.array([np.std(data1[num],ddof= 1) for num in range(sampling_num)])
s_Var = s_std**2
s_mean = np.array([np.mean(data1[num]) for num in range(sampling_num)])
p_std = np.std(a,ddof= 0)
p_Var = p_std**2
p_mean = np.mean(a)
chi_square = (s_Var*(sample_num-1))/(p_Var)
t_student = (s_mean-p_mean)/(s_std/(np.sqrt(sample_num)))
# my_x_ticks = np.arange(0, 15, 1)
plt.xlim((0, 80))
plt.hist((a), # 绘图数据
        bins = 100, # 指定直方图的条形数为20个
        color = 'steelblue', # 指定填充色
        edgecolor = 'k', # 指定直方图的边界色
        label = '直方图' )# 为直方图呈现标签
plt.show()
plt.xlim((0, 80))
plt.hist((s_Var), # 绘图数据
        bins = 200, # 指定直方图的条形数为20个
        color = 'steelblue', # 指定填充色
        edgecolor = 'k', # 指定直方图的边界色
        label = '直方图' )# 为直方图呈现标签
plt.show()
# plt.xlim((0, 80))
plt.hist((s_mean), # 绘图数据
        bins = 100, # 指定直方图的条形数为20个
        color = 'steelblue', # 指定填充色
        edgecolor = 'k', # 指定直方图的边界色
        label = '直方图' )# 为直方图呈现标签
plt.show()
# plt.xlim((0, 80))
plt.hist((t_student), # 绘图数据
        bins = 50, # 指定直方图的条形数为20个
        color = 'steelblue', # 指定填充色
        edgecolor = 'k', # 指定直方图的边界色
        label = '直方图' )# 为直方图呈现标签
plt.show()
plt.hist((chi_square), # 绘图数据
        bins = 50, # 指定直方图的条形数为20个
        color = 'steelblue', # 指定填充色
        edgecolor = 'k', # 指定直方图的边界色
        label = '直方图' )# 为直方图呈现标签
plt.show()
```
>![](https://upload-images.jianshu.io/upload_images/13539817-c16228bc5a706d7b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![](https://upload-images.jianshu.io/upload_images/13539817-a4580f82e86bf194.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![](https://upload-images.jianshu.io/upload_images/13539817-8cac22907a1b19d5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![](https://upload-images.jianshu.io/upload_images/13539817-dbda364c86e197f4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## Numpy日期 ##     
[**Datetimes and Timedeltas**](https://docs.scipy.org/doc/numpy/reference/arrays.datetime.html)
- 建立     
![範例1](https://upload-images.jianshu.io/upload_images/13539817-e3fc118b77fbd3b6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![範例2](https://upload-images.jianshu.io/upload_images/13539817-5e7cf6cd9b750697.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![範例3](https://upload-images.jianshu.io/upload_images/13539817-b24128b34822cfc1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![範例4](https://upload-images.jianshu.io/upload_images/13539817-86c66eb33987ad0b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 運算     
![範例](https://upload-images.jianshu.io/upload_images/13539817-af65c15537982fdc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


- 日期時間單位     
![日期時間單位](https://upload-images.jianshu.io/upload_images/13539817-15bf1dd80f3be353.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 定義工作日的掩碼
![工作日的掩碼(默認是六日為假日)](https://upload-images.jianshu.io/upload_images/13539817-1a359209cc3feb7c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 營業日功能    
![往後偏移幾個工作日(06/25、06/26為假日)](https://upload-images.jianshu.io/upload_images/13539817-db7c14b6f1b31224.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![若輸入日期為假日需加入forward or backward規則](https://upload-images.jianshu.io/upload_images/13539817-c6747ae1be2c244c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![計算母親節(forward到第一個星期日再偏移到第2個)](https://upload-images.jianshu.io/upload_images/13539817-caabdeb81fbde507.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## 字符串操作 ##
[String operations](https://docs.scipy.org/doc/numpy-1.13.0/reference/routines.char.html)

![範例](https://upload-images.jianshu.io/upload_images/13539817-07d47806502031b6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
