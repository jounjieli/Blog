[numpy1](https://www.jianshu.com/p/166e04e7b659)
[numpy2](https://www.jianshu.com/p/520084e85f2d)
[numpy3](https://www.jianshu.com/p/98deb28eacbe)
### 數組的[運算](https://docs.scipy.org/doc/numpy-1.14.0/reference/index.html) ###
- **基本運算**

| 運算           | 對應函數                                                     |
| -------------- | ------------------------------------------------------------ |
| y = x1   + x2  | add(x1, x2 [, y])                                            |
| y = x1   - x2  | subtract(x1, x2 [,   y])                                     |
| y = x1   * x2  | multiply (x1, x2   [, y])                                    |
| y = x1   / x2  | divide (x1, x2 [,   y]), 如果兩個陣列的元素為整數，那麼用整數除法 |
| y = x1   / x2  | true_divide(x1,   x2 [, y]), 總是返回精確的商               |
| y = x1   // x2 | floor_divide (x1,   x2 [, y]), 總是返回商值取整              |
| y = -x         | negative(x [,y])                                             |
| y =   x1**x2   | power(x1, x2 [,   y])                                        |
| y = x1   % x2  | remainder(x1, x2   [, y]), mod(x1, x2, [, y])                |

| [數學運算](https://docs.scipy.org/doc/numpy/reference/ufuncs.html#math-operations) |                                                |
| ------------------------------------------------------------ | ---------------------------------------------- |
| [add(x1, x2, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.add.html#numpy.add) | 按元素添加參數。                               |
| [subtract(x1, x2, /[, out, where, casting, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.subtract.html#numpy.subtract) | 從元素方面減去參數。                           |
| [multiply(x1, x2, /[, out, where, casting, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.multiply.html#numpy.multiply) | 元素相乘的論證。                               |
| [divide(x1, x2, /[, out, where, casting, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.divide.html#numpy.divide) | 以元素方式返回輸入的真正除法。                 |
| [logaddexp(x1, x2, /[, out, where, casting, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.logaddexp.html#numpy.logaddexp) | 輸入的取冪之和的對數。                         |
| [logaddexp2(x1, x2, /[, out, where, casting, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.logaddexp2.html#numpy.logaddexp2) | base-2中輸入的取冪之和的對數。                 |
| [true_divide(x1, x2, /[, out, where, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.true_divide.html#numpy.true_divide) | 以元素方式返回輸入的真正除法。                 |
| [floor_divide(x1, x2, /[, out, where, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.floor_divide.html#numpy.floor_divide) | 返回小於或等於輸入除法的最大整數。             |
| [negative(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.negative.html#numpy.negative) | 數字否定，元素方面。                           |
| [positive(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.positive.html#numpy.positive) | 數字正面，元素方面。                           |
| [power(x1, x2, /[, out, where, casting, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.power.html#numpy.power) | 第一個數組元素從第二個數組提升到冪，逐個元素。 |
| [remainder(x1, x2, /[, out, where, casting, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.remainder.html#numpy.remainder) | 返回除法元素的餘數。                           |
| [mod(x1, x2, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.mod.html#numpy.mod) | 返回除法元素的餘數。                           |
| [fmod(x1, x2, /[, out, where, casting, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.fmod.html#numpy.fmod) | 返回除法的元素餘數。                           |
| [divmod(x1, x2[, out1, out2], / [, out, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.divmod.html#numpy.divmod) | 同時返回逐元素的商和余數。                     |
| [absolute(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.absolute.html#numpy.absolute) | 逐個元素地計算絕對值。                         |
| [fabs(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.fabs.html#numpy.fabs) | 以元素方式計算絕對值。                         |
| [rint(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.rint.html#numpy.rint) | 將數組的元素舍入為最接近的整數。               |
| [sign(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.sign.html#numpy.sign) | 返回數字符號的元素指示。                       |
| [heaviside(x1, x2, /[, out, where, casting, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.heaviside.html#numpy.heaviside) | 計算Heaviside階躍函數。                        |
| [conj(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.conj.html#numpy.conj) | 以元素方式返回复共軛。                         |
| [exp(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.exp.html#numpy.exp) | 計算輸入數組中所有元素的指數。                 |
| [exp2(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.exp2.html#numpy.exp2) | 計算輸入數組中所有p的2 ** p。                  |
| [log(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.log.html#numpy.log) | 自然對數，元素方面。                           |
| [log2(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.log2.html#numpy.log2) | x的基數為2的對數。                             |
| [log10(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.log10.html#numpy.log10) | 以元素方式返回輸入數組的基數10對數。           |
| [expm1(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.expm1.html#numpy.expm1) | 計算數組中的所有元素。exp(x) - 1               |
| [log1p(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.log1p.html#numpy.log1p) | 返回一個加上輸入數組的自然對數，逐個元素。     |
| [sqrt(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.sqrt.html#numpy.sqrt) | 以元素方式返回數組的非負平方根。               |
| [square(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.square.html#numpy.square) | 返回輸入的元素方塊。                           |
| [cbrt(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.cbrt.html#numpy.cbrt) | 以元素方式返回數組的立方根。                   |
| [reciprocal(x, /[, out, where, casting, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.reciprocal.html#numpy.reciprocal) | 以元素為單位返回參數的倒數。                   |
| [gcd(x1, x2, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.gcd.html#numpy.gcd) | 返回\|x1\|和的最大公約數\|x2\|                 |
| [lcm(x1, x2, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.lcm.html#numpy.lcm) | 返回\|x1\|和的最小公倍數\|x2\|                 |


- **三角函數**

|||
| ------------------------------------------------------------ | -------------------------------------------- |
| [sin(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.sin.html#numpy.sin) | 三角正弦，元素。                   |
| [cos(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.cos.html#numpy.cos) | 餘弦元素。                         |
| [tan(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.tan.html#numpy.tan) | 計算切線元素。                     |
| [arcsin(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.arcsin.html#numpy.arcsin) | 反正弦，元素。                     |
| [arccos(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.arccos.html#numpy.arccos) | 三角反餘弦，元素方式。             |
| [arctan(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.arctan.html#numpy.arctan) | 三角反正切，逐元素。               |
| [arctan2(x1, x2, /[, out, where, casting, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.arctan2.html#numpy.arctan2) | x1/x2正確選擇象限的逐元素反正切。  |
| [hypot(x1, x2, /[, out, where, casting, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.hypot.html#numpy.hypot) | 給定直角三角形的“腿”，返回其斜邊。 |
| [sinh(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.sinh.html#numpy.sinh) | 雙曲正弦，元素。                   |
| [cosh(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.cosh.html#numpy.cosh) | 雙曲餘弦，元素。                   |
| [tanh(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.tanh.html#numpy.tanh) | 計算雙曲正切元素。                 |
| [arcsinh(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.arcsinh.html#numpy.arcsinh) | 逆雙曲正弦元素。                   |
| [arccosh(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.arccosh.html#numpy.arccosh) | 反雙曲餘弦，元素。                 |
| [arctanh(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.arctanh.html#numpy.arctanh) | 逆雙曲正切元素。                   |
| [deg2rad(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.deg2rad.html#numpy.deg2rad) | 將角度從度數轉換為弧度。           |
| [rad2deg(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.rad2deg.html#numpy.rad2deg) | 將角度從弧度轉換為度數。           |



- **捨入**

|||
| ------------------------------------------------------------ | -------------------------------- |
| [around(a[, decimals, out])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.around.html#numpy.around) | 均勻舍入到給定的小數位數。       |
| [round_(a[, decimals, out])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.round_.html#numpy.round_) | 將數組舍入到給定的小數位數。     |
| [rint(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.rint.html#numpy.rint) | 將數組的元素舍入為最接近的整數(四捨五入)。 |
| [fix(x[, out])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.fix.html#numpy.fix) | 向零舍入到最接近的整數。         |
| [floor(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.floor.html#numpy.floor) | 以元素方式返回輸入的下限(取下限)。       |
| [ceil(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ceil.html#numpy.ceil) | 以元素方式返回輸入的上限(取上限)。       |
| [trunc(x, /[, out, where, casting, order, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.trunc.html#numpy.trunc) | 以元素方式返回輸入的截斷值。     |

- **總和，乘積，差異**

|||
| ------------------------------------------------------------ | ----------------------------------------------------------- |
| [prod(a[, axis, dtype, out, keepdims, initial])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.prod.html#numpy.prod) | 返回給定軸上的數組元素的乘積。                              |
| [sum(a[, axis, dtype, out, keepdims, initial])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.sum.html#numpy.sum) | 給定軸上的數組元素的總和。                                  |
| [nanprod(a[, axis, dtype, out, keepdims])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.nanprod.html#numpy.nanprod) | 返回給定軸上的數組元素的乘積，將非數字（NaN）視為1。        |
| [nansum(a[, axis, dtype, out, keepdims])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.nansum.html#numpy.nansum) | 返回給定軸上的數組元素的總和，將非數字（NaN）視為零。       |
| [cumprod(a[, axis, dtype, out])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.cumprod.html#numpy.cumprod) | 返回給定軸上元素的累積乘積。                                |
| [cumsum(a[, axis, dtype, out])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.cumsum.html#numpy.cumsum) | 返回給定軸上元素的累積和。                                  |
| [nancumprod(a[, axis, dtype, out])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.nancumprod.html#numpy.nancumprod) | 返回給定軸上的數組元素的累積乘積，將非數字（NaN）視為一個。 |
| [nancumsum(a[, axis, dtype, out])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.nancumsum.html#numpy.nancumsum) | 返回給定軸上的數組元素的累積和，將非數字（NaN）視為零。     |
| [diff(a[, n, axis])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.diff.html#numpy.diff) | 計算沿給定軸的第n個離散差。                                 |
| [ediff1d(ary[, to_end, to_begin])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ediff1d.html#numpy.ediff1d) | 數組的連續元素之間的差異。                                  |
| [gradient(f, *varargs, **kwargs)](https://docs.scipy.org/doc/numpy/reference/generated/numpy.gradient.html#numpy.gradient) | 返回N維數組的漸變。                                         |
| [cross(a, b[, axisa, axisb, axisc, axis])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.cross.html#numpy.cross) | 返回兩個（數組）向量的叉積。                                |
| [trapz(y[, x, dx, axis])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.trapz.html#numpy.trapz) | 使用複合梯形法則沿給定軸積分。                              |

- **比較運算及邏輯運算**

| 運算子| 描述                                                         | 實例                    |
| ------ | ------------------------------------------------------------ | ----------------------- |
| ==     | 等於   - 比較物件是否相等                                    | (a   == b) 返回 False。 |
| !=     | 不等於 - 比較兩個物件是否不相等                              | (a != b) 返回 True。    |
| >      | 大於 - 返回x是否大於y                                        | (a > b) 返回 False。    |
| <      | 小於 -   返回x是否小於y。所有比較運算子返回1表示真，返回0表示假。這分別與特殊的變數True和False等價。注意，這些變數名的大寫。 | (a < b) 返回 True。     |
| >=     | 大於等於 - 返回x是否大於等於y。                              | (a >= b) 返回 False。   |
| <=     | 小於等於 - 返回x是否小於等於y。                              | (a <= b) 返回 True。    |

| 運算子 | 邏輯運算式 | 描述                                                         | 實例                    |
| ------ | ---------- | ------------------------------------------------------------ | ----------------------- |
| and    | x   and y  | 布林"與"   - 如果 x 為 False，x and y 返回 False，否則它返回 y 的計算值。 | (a   and b) 返回 20。   |
| or     | x or y     | 布林"或" - 如果 x 是 True，它返回 x 的值，否則它返回 y 的計算值。 | (a or b) 返回 10。      |
| not    | not x      | 布林"非" - 如果 x 為 True，返回 False 。如果 x 為 False，它返回   True。 | not(a and b) 返回 False |

|比較運算及邏輯運算| |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [greater（x1，x2，/   [，out，where，cast，...]）](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.greater.html#numpy.greater) | 以元素方式返回（x1 >   x2）的布林值。                           |
| [greater_equal（x1，x2，/ [，out，where，...]）](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.greater_equal.html#numpy.greater_equal) | 以元素方式返回（x1 >= x2）的布林值。                         |
| [less（x1，x2，/   [，out，where，cast，...]）](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.less.html#numpy.less) | 以元素方式返回（x1 < x2）的布林值。                           |
| [less_equal（x1，x2，/ [，out，where，cast，...]）](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.less_equal.html#numpy.less_equal) | 以元素方式返回（x1 =< x2）的布林值。                         |
| [not_equal（x1，x2，/ [，out，where，cast，...]）](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.not_equal.html#numpy.not_equal) | 以元素方式返回（x1 != x2）的布林值。                               |
| [equal（x1，x2，/   [，out，where，cast，...]）](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.equal.html#numpy.equal) | 以元素方式返回（x1 == x2）的布林值。                               |
警告
不要使用Python關鍵字“and”和“or”來組合邏輯數組表達式。   這些關鍵字將測試整個數組的真值（不是你想像的逐個元素）。 使用按位運算符“＆”和“\|” 代替。
|||
| ------------------------------------------------------------ | ------------------------------------------------------------ | 
| [logical_and（x1，x2，/ [，out，where，...]）](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.logical_and.html#numpy.logical_and) | 計算x1 and x2元素的布林值。                                       |
| [logical_or（x1，x2，/ [，out，where，cast，...]）](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.logical_or.html#numpy.logical_or) | 計算x1 or x2元素的布林值。                                   |
| [logical_xor（x1，x2，/ [，out，where，...]）](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.logical_xor.html#numpy.logical_xor) | 以元素方式計算x1 xor x2的布林值。                            |
| [logical_not（x，/ [，out，where，cast，...]）](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.logical_not.html#numpy.logical_not) | 計算not x元素的布林值。                                      |
**警告**
按位運算符“＆”和“\|” 是執行逐元素數組比較的正確方法。 確保您理解運算符優先級：“（a> 2）＆（a <5）”是正確的語法，因為“a> 2＆a <5”將導致錯誤，因為“2＆a” 首先評估。
|||
| ------------------------------------------------------------ | ------------------------------------------------------------ | 
| [maximum（x1，x2，/   [，out，where，cast，...]）](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.maximum.html#numpy.maximum) | 元素最大數組元素。                                           |
| [minimum（x1，x2，/   [，out，where，cast，...]）](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.minimum.html#numpy.minimum) | 元素最小的數組元素。                                         |
**提示**
Python函數“max（）”將在一維數組中找到最大值，但它將使用較慢的序列接口來實現。 maximum ufunc的reduce方法要快得多。 此外，“max（）”方法不會給出具有多個維度的數組所期望的答案。 reduce的minimal方法還允許您計算數組的總最小值。
**警告**
“maximum（a，b）”的行為與“max（a，b）”的行為不同。 作為ufunc，“maximum（a，b）”執行 a和b and 的逐元素比較，根據兩個數組中的哪個元素更大來選擇結果的每個元素。 
相反，“max（a，b）”將對象a和b視為一個整體，查看“a> b”的（總）真值，並使用它返回a或b（作為一個整體）。 “最小（a，b）”和“min（a，b）”之間存在類似的差異。 
|||
| ------------------------------------------------------------ | ------------------------------------------------------------ | 
| [fmax（x1，x2，/   [，out，where，cast，...]）](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fmax.html#numpy.fmax) | 元素最大數組元素。                                           |
| [fmin（x1，x2，/   [，out，where，cast，...]）](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fmin.html#numpy.fmin) | 元素最小的數組元素。                                         |

- **位運算**

| 運算子 | 描述                                                         | 實例                                                         |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| &      | 按位與運算子：參與運算的兩個值,如果兩個相應位都為1,則該位的結果為1,否則為0 | (a   & b) 輸出結果 12 ，二進位解釋： 0000 1100               |
| \|     | 按位或運算子：只要對應的二個二進位有一個為1時，結果位就為1。 | (a \| b) 輸出結果 61 ，二進位解釋： 0011 1101                |
| ^      | 按位異或運算子：當兩對應的二進位相異時，結果為1              | (a ^ b) 輸出結果 49 ，二進位解釋： 0011 0001                 |
| ~      | 按位取反運算子：對資料的每個二進位位元取反,即把1變為0,把0變為1。~x類似於 -x-1 | (~a ) 輸出結果 -61 ，二進位解釋： 1100 0011， 在一個有符號二進位數字的補數形式。 |
| <<     | 左移動運算子：運算數的各二進位元全部左移若干位元，由"<<"右邊的數指定移動的位元數，高位丟棄，低位元補0。 | a << 2 輸出結果 240 ，二進位解釋： 1111 0000                 |
| >>     | 右移動運算子：把">>"左邊的運算數的各二進位元全部右移若干位元，">>"右邊的數指定移動的位數 | a >> 2 輸出結果 15 ，二進位解釋： 0000 1111                  |

|||
| ------------------------------------------------------------ | --------------------------------- |
| [bitwise_and(x1, x2, /[, out, where, ...])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.bitwise_and.html#numpy.bitwise_and) | 逐個元素地計算兩個數組的逐位AND。 |
| [bitwise_or(x1, x2, /[, out, where, casting, ...])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.bitwise_or.html#numpy.bitwise_or) | 逐個元素地計算兩個數組的逐位OR。  |
| [bitwise_xor(x1, x2, /[, out, where, ...])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.bitwise_xor.html#numpy.bitwise_xor) | 計算兩個數組的逐位XOR元素。       |
| [invert(x, /[, out, where, casting, order, ...])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.invert.html#numpy.invert) | 按位元素計算逐位反轉或逐位NOT。   |
| [left_shift(x1, x2, /[, out, where, casting, ...])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.left_shift.html#numpy.left_shift) | 將整數位移到左側。                |
| [right_shift(x1, x2, /[, out, where, ...])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.right_shift.html#numpy.right_shift) | 將整數位移到右側。                |

- **統計**

| [統計](https://docs.scipy.org/doc/numpy/reference/routines.statistics.html#statistics) |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [**Order statistics**](https://docs.scipy.org/doc/numpy/reference/routines.statistics.html#order-statistics) |                                                              |
| [amin(a[, axis, out, keepdims, initial])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.amin.html#numpy.amin) | 沿軸返回數組或最小值的最小值。                               |
| [amax(a[, axis, out, keepdims, initial])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.amax.html#numpy.amax) | 沿軸返回數組的最大值或最大值。                               |
| [nanmin(a[, axis, out, keepdims])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.nanmin.html#numpy.nanmin) | 沿軸返回最小數組或最小值，忽略任何NaN。                      |
| [nanmax(a[, axis, out, keepdims])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.nanmax.html#numpy.nanmax) | 沿軸返回數組的最大值或最大值，忽略任何NaN。                  |
| [ptp(a[, axis, out, keepdims])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ptp.html#numpy.ptp) | 沿軸的值範圍（最大值 - 最小值）。                            |
| [percentile(a, q[, axis, out, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.percentile.html#numpy.percentile) | 計算沿指定軸的數據的第q個百分位數。                          |
| [nanpercentile(a, q[, axis, out, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.nanpercentile.html#numpy.nanpercentile) | 計算沿指定軸的數據的第q個百分位數，同時忽略nan值。           |
| [quantile(a, q[, axis, out, overwrite_input, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.quantile.html#numpy.quantile) | 计算沿指定轴的数据的`q`th分位数...版本添加:: 1.15.0。        |
| [nanquantile(a, q[, axis, out, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.nanquantile.html#numpy.nanquantile) | 計算沿指定軸的數據的第q個分位數，同時忽略nan值。             |
| [**Averages and variances**](https://docs.scipy.org/doc/numpy/reference/routines.statistics.html#averages-and-variances) |                                                              |
| [median(a[, axis, out, overwrite_input, keepdims])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.median.html#numpy.median) | 計算沿指定軸的中位數。                                       |
| [average(a[, axis, weights, returned])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.average.html#numpy.average) | 計算沿指定軸的加權平均值。                                   |
| [mean(a[, axis, dtype, out, keepdims])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.mean.html#numpy.mean) | 計算沿指定軸的算術平均值。                                   |
| [std(a[, axis, dtype, out, ddof, keepdims])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.std.html#numpy.std) | 計算沿指定軸的標準偏差。                                     |
| [var(a[, axis, dtype, out, ddof, keepdims])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.var.html#numpy.var) | 計算沿指定軸的方差。                                         |
| [nanmedian(a[, axis, out, overwrite_input, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.nanmedian.html#numpy.nanmedian) | 計算沿指定軸的中位數，同時忽略`NaN`。                          |
| [nanmean(a[, axis, dtype, out, keepdims])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.nanmean.html#numpy.nanmean) | 計算沿指定軸的算術平均值，忽略`NaN`。                          |
| [nanstd(a[, axis, dtype, out, ddof, keepdims])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.nanstd.html#numpy.nanstd) | 計算沿指定軸的標準偏差，同時忽略`NaN`。                        |
| [nanvar(a[, axis, dtype, out, ddof, keepdims])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.nanvar.html#numpy.nanvar) | 計算沿指定軸的方差，同時忽略`NaN`。                            |
| [**Correlating**](https://docs.scipy.org/doc/numpy/reference/routines.statistics.html#correlating) |                                                              |
| [corrcoef(x[, y, rowvar, bias, ddof])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.corrcoef.html#numpy.corrcoef) | 返回Pearson乘積矩相關係數。                                  |
| [correlate(a, v[, mode])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.correlate.html#numpy.correlate) | 兩個1維序列的互相關。                                        |
| [cov(m[, y, rowvar, bias, ddof, fweights, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.cov.html#numpy.cov) | 給定數據和權重，估計協方差矩陣。                             |
| [**Histograms**](https://docs.scipy.org/doc/numpy/reference/routines.statistics.html#histograms) |                                                              |
| [histogram(a[, bins, range, normed, weights, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.histogram.html#numpy.histogram) | 計算一組數據的直方圖。                                       |
| [histogram2d(x, y[, bins, range, normed, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.histogram2d.html#numpy.histogram2d) | 計算兩個數據樣本的二維直方圖。                               |
| [histogramdd(sample[, bins, range, normed, …])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.histogramdd.html#numpy.histogramdd) | 計算一些數據的多維直方圖。                                   |
| [bincount(x[, weights, minlength])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.bincount.html#numpy.bincount) | 計算非負的int數組中每個值的出現次數。                        |
| [histogram_bin_edges(a[, bins, range, weights])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.histogram_bin_edges.html#numpy.histogram_bin_edges) | 僅計算函數使用的bin的邊緣的[histogram](https://docs.scipy.org/doc/numpy/reference/generated/numpy.histogram.html#numpy.histogram)函數。 |
| [digitize(x, bins[, right])](https://docs.scipy.org/doc/numpy/reference/generated/numpy.digitize.html#numpy.digitize) | 返回輸入數組中每個值所屬的bin的索引。                        |

- **線性代數**

| [線性代數（numpy.linalg）](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.linalg.html#linear-algebra-numpy-linalg) |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [**Matrix and vector products**](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.linalg.html#matrix-and-vector-products) |                                                              |
| [dot(a, b[, out])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.dot.html#numpy.dot) | 兩個數組的點積。                                             |
| [linalg.multi_dot(arrays)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.multi_dot.html#numpy.linalg.multi_dot) | 在單個函數調用中計算兩個或多個數組的點積，同時自動選擇最快的求值順序。 |
| [vdot(a, b)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.vdot.html#numpy.vdot) | 返回兩個向量的點積。                                         |
| [inner(a, b)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.inner.html#numpy.inner) | 兩個數組的內積。                                             |
| [outer(a, b[, out])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.outer.html#numpy.outer) | 計算兩個向量的外積。                                         |
| [matmul(a, b[, out])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.matmul.html#numpy.matmul) | 兩個數組的矩陣乘積。                                         |
| [tensordot(a, b[, axes])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.tensordot.html#numpy.tensordot) | 對於數組> = 1-D，沿指定軸計算張量點積。                      |
| [einsum(subscripts, *operands[, out, dtype, ...])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.einsum.html#numpy.einsum) | 評估操作數上的愛因斯坦求和約定。                             |
| [einsum_path(subscripts, *operands[, optimize])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.einsum_path.html#numpy.einsum_path) | 通過考慮中間數組的創建，評估einsum表達式的最低成本收縮順序。 |
| [linalg.matrix_power(M, n)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.matrix_power.html#numpy.linalg.matrix_power) | 將方陣提高到（整數）冪n。                                    |
| [kron(a, b)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.kron.html#numpy.kron) | 兩個陣列的Kronecker產品。                                    |
| [**Decompositions**](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.linalg.html#decompositions) |                                                              |
| [linalg.cholesky(a)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.cholesky.html#numpy.linalg.cholesky) | Cholesky分解。                                               |
| [linalg.qr(a[, mode])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.qr.html#numpy.linalg.qr) | 計算矩陣的qr分解。                                           |
| [linalg.svd(a[, full_matrices, compute_uv])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.svd.html#numpy.linalg.svd) | 奇異值分解。                                                 |
| [**Matrix eigenvalues**](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.linalg.html#matrix-eigenvalues) |                                                              |
| [linalg.eig(a)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.eig.html#numpy.linalg.eig) | 計算正方形陣列的特徵值和右特徵向量。                         |
| [linalg.eigh(a[, UPLO])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.eigh.html#numpy.linalg.eigh) | 返回Hermitian或對稱矩陣的特徵值和特徵向量。                  |
| [linalg.eigvals(a)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.eigvals.html#numpy.linalg.eigvals) | 計算一般矩陣的特徵值。                                       |
| [linalg.eigvalsh(a[, UPLO])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.eigvalsh.html#numpy.linalg.eigvalsh) | 計算Hermitian或實對稱矩陣的特徵值。                          |
| [**Norms and other numbers**](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.linalg.html#norms-and-other-numbers) |                                                              |
| [linalg.norm(x[, ord, axis, keepdims])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.norm.html#numpy.linalg.norm) | 矩陣或矢量規範。                                             |
| [linalg.cond(x[, p])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.cond.html#numpy.linalg.cond) | 計算矩陣的條件數。                                           |
| [linalg.det(a)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.det.html#numpy.linalg.det) | 計算數組的行列式。                                           |
| [linalg.matrix_rank(M[, tol, hermitian])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.matrix_rank.html#numpy.linalg.matrix_rank) | 使用SVD方法返回陣列的矩陣等級                                |
| [linalg.slogdet(a)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.slogdet.html#numpy.linalg.slogdet) | 計算數組行列式的符號和（自然）對數。                         |
| [trace(a[, offset, axis1, axis2, dtype, out])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.trace.html#numpy.trace) | 返回數組對角線的總和。                                       |
| [**Solving equations and inverting matrices**](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.linalg.html#solving-equations-and-inverting-matrices) |                                                              |
| [linalg.solve(a, b)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.solve.html#numpy.linalg.solve) | 求解線性矩陣方程或線性標量方程組。                           |
| [linalg.tensorsolve(a, b[, axes])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.tensorsolve.html#numpy.linalg.tensorsolve) | 求解x的张量方程“a x = b”。                                   |
| [linalg.lstsq(a, b[, rcond])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.lstsq.html#numpy.linalg.lstsq) | 將最小二乘解返回到線性矩陣方程。                             |
| [linalg.inv(a)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.inv.html#numpy.linalg.inv) | 計算矩陣的（乘法）逆。                                       |
| [linalg.pinv(a[, rcond])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.pinv.html#numpy.linalg.pinv) | 計算矩陣的（Moore-Penrose）偽逆。                            |
| [linalg.tensorinv(a[, ind])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.tensorinv.html#numpy.linalg.tensorinv) | 計算N維數組的“逆”。                                          |
| [**Exceptions**](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.linalg.html#exceptions) |                                                              |
| [linalg.LinAlgError](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.linalg.LinAlgError.html#numpy.linalg.LinAlgError) | 由linalg函數引發的通用Python異常派生對象。                   |

- **離散傅立葉變換**

| 離散傅立葉變換（[numpy.fft](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.fft.html#module-numpy.fft)）                                  |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [**Standard FFTs**](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.fft.html#standard-ffts) |                                                              |
| [fft(a[, n, axis, norm])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.fft.html#numpy.fft.fft) | 計算一維離散傅立葉變換。                                     |
| [ifft(a[, n, axis, norm])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.ifft.html#numpy.fft.ifft) | 計算一維離散傅里葉逆變換。                                   |
| [fft2(a[, s, axes, norm])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.fft2.html#numpy.fft.fft2) | 計算二維離散傅立葉變換                                       |
| [ifft2(a[, s, axes, norm])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.ifft2.html#numpy.fft.ifft2) | 計算二維逆離散傅立葉變換。                                   |
| [fftn(a[, s, axes, norm])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.fftn.html#numpy.fft.fftn) | 計算N維離散傅立葉變換。                                      |
| [ifftn(a[, s, axes, norm])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.ifftn.html#numpy.fft.ifftn) | 計算N維逆離散傅立葉變換。                                    |
| [**Real FFTs**](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.fft.html#real-ffts) |                                                              |
| [rfft(a[, n, axis, norm])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.rfft.html#numpy.fft.rfft) | 計算一維離散傅立葉變換用於實際輸入。                         |
| [irfft(a[, n, axis, norm])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.irfft.html#numpy.fft.irfft) | 計算實際輸入的n點DFT的倒數。                                 |
| [rfft2(a[, s, axes, norm])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.rfft2.html#numpy.fft.rfft2) | 計算實數組的二維FFT。                                        |
| [irfft2(a[, s, axes, norm])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.irfft2.html#numpy.fft.irfft2) | 計算實數組的二維逆FFT。                                      |
| [rfftn(a[, s, axes, norm])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.rfftn.html#numpy.fft.rfftn) | 為實際輸入計算N維離散傅立葉變換。                            |
| [irfftn(a[, s, axes, norm])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.irfftn.html#numpy.fft.irfftn) | 計算實際輸入的N維FFT的逆。                                   |
| [**Hermitian FFTs**](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.fft.html#hermitian-ffts) |                                                              |
| [hfft(a[, n, axis, norm])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.hfft.html#numpy.fft.hfft) | 計算具有厄米對稱性的信號的FFT，即實際頻譜。                  |
| [ihfft(a[, n, axis, norm])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.ihfft.html#numpy.fft.ihfft) | 計算具有厄米對稱性的信號的逆FFT。                            |
| [**Helper routines**](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.fft.html#helper-routines) |                                                              |
| [fftfreq(n[, d])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.fftfreq.html#numpy.fft.fftfreq) | 返回離散傅立葉變換採樣頻率。                                 |
| [rfftfreq(n[, d])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.rfftfreq.html#numpy.fft.rfftfreq) | 返回離散傅里葉變換採樣頻率（用於rfft，irfft）。              |
| [fftshift(x[, axes])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.fftshift.html#numpy.fft.fftshift) | 將零頻率分量移到頻譜中心。                                   |
| [ifftshift(x[, axes])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.ifftshift.html#numpy.fft.ifftshift) | [逆的fftshift。](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.fft.fftshift.html#numpy.fft.fftshift) |

- **排序,搜索,計數**

| [排序，搜索和計數](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.sort.html#sorting-searching-and-counting) |                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------ |
| [Sorting](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.sort.html#sorting) |                                                        |
| [sort(a[, axis, kind, order])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.sort.html#numpy.sort) | 返回數組的排序副本。                                   |
| [lexsort(keys[, axis])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.lexsort.html#numpy.lexsort) | 使用一系列鍵執行間接排序。                             |
| [argsort(a[, axis, kind, order])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.argsort.html#numpy.argsort) | 返回對數組進行排序的索引。                             |
| [ndarray.sort([axis, kind, order])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.ndarray.sort.html#numpy.ndarray.sort) | 就地對數組進行排序。                                   |
| [msort(a)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.msort.html#numpy.msort) | 返回沿第一個軸排序的數組副本。                         |
| [sort_complex(a)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.sort_complex.html#numpy.sort_complex) | 首先使用實部對複雜數組進行排序，然後使用虛部進行排序。 |
| [partition(a, kth[, axis, kind, order])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.partition.html#numpy.partition) | 返回數組的分區副本。                                   |
| [argpartition(a, kth[, axis, kind, order])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.argpartition.html#numpy.argpartition) | 使用kind關鍵字指定的算法沿給定軸執行間接分區。         |
| [**Searching**](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.sort.html#searching) |                                                        |
| [argmax(a[, axis, out])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.argmax.html#numpy.argmax) | 返回沿軸的最大值的索引。                               |
| [nanargmax(a[, axis])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.nanargmax.html#numpy.nanargmax) | 返回指定軸中忽略NaN的最大值的索引。                    |
| [argmin(a[, axis, out])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.argmin.html#numpy.argmin) | 返回沿軸的最小值的索引。                               |
| [nanargmin(a[, axis])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.nanargmin.html#numpy.nanargmin) | 返回指定軸中忽略NaN的最小值的索引。                    |
| [argwhere(a)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.argwhere.html#numpy.argwhere) | 查找按元素分組的非零的數組元素的索引。                 |
| [nonzero(a)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.nonzero.html#numpy.nonzero) | 返回非零元素的索引。                                   |
| [flatnonzero(a)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.flatnonzero.html#numpy.flatnonzero) | 返回a的展平版本中非零的索引。                          |
| [where(condition, [x, y])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.where.html#numpy.where) | 返回元素，可以是x或y，具體取決於條件。                 |
| [searchsorted(a, v[, side, sorter])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.searchsorted.html#numpy.searchsorted) | 查找應插入元素以維護順序的索引。                       |
| [extract(condition, arr)](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.extract.html#numpy.extract) | 返回滿足某些條件的數組元素。                           |
| [**Counting**](https://docs.scipy.org/doc/numpy-1.14.0/reference/routines.sort.html#counting) |                                                        |
| [count_nonzero(a[, axis])](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.count_nonzero.html#numpy.count_nonzero) | 计算数组a中的非零值的数量。                            |

#### 其他(持續補充) ####
### 掩碼 ###
[掩碼數組](https://docs.scipy.org/doc/numpy/reference/maskedarray.html)
### 讀取、儲存 ###
[numpy.save](https://docs.scipy.org/doc/numpy-1.15.0/reference/generated/numpy.save.html)
[numpy.load](https://docs.scipy.org/doc/numpy-1.15.0/reference/generated/numpy.load.html#numpy.load)
[numpy.loadtxt](https://docs.scipy.org/doc/numpy-1.13.0/reference/generated/numpy.loadtxt.html)
### 迭代 ###
[numpy.nditer](https://docs.scipy.org/doc/numpy-1.15.0/reference/generated/numpy.nditer.html#numpy-nditer)

參考閱讀:
1.https://wizardforcel.gitbooks.io/ts-numpy-tut/content/
2.https://docs.scipy.org/doc/numpy-1.14.0/index.html
