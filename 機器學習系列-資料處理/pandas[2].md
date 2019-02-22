[pandas1](https://www.jianshu.com/p/5114db1e603f)
[pandas2](https://www.jianshu.com/p/58d5ae4b848f)
---
### 分組操作 ###
##### GroupBy #####
- **DataFrame.groupby**
[**DataFrame.groupby**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.groupby.html)

| 參數       | 描述                                                         |
| ---------- | ------------------------------------------------------------ |
| by         | 映射，功能，標籤或標籤列表，用於確定groupby的組。如果by是函數，則調用對象索引的每個值。如果傳遞了dict或Series，則將使用Series或dict   VALUES來確定組（系列的值首先對齊;請參閱.align()方法）。如果傳遞了ndarray，則使用這些值來確定組。標籤或標籤列表可以通過列傳遞到組self。請注意，元組被解釋為（單個）鍵。 |
| axis       | int，默認值為0                                               |
| level      | int，level name或其序列，默認為None，如果軸是MultiIndex（分層），則按特定級別或級別分組 |
| as_index   | boolean，默認為True，對於聚合輸出，返回以組標籤作為索引的對象。僅與DataFrame輸入相關。as_index =   False實際上是“SQL風格”的分組輸出 |
| sort       | 布爾值，默認為True，對組鍵進行排序。關閉它可以獲得更好的性能。請注意，這不會影響每個組內的觀察順序。groupby保留每個組中的行順序。 |
| group_keys | 布爾值，默認為True，調用apply時，將組鍵添加到索引以標識片段  |
| squeeze    | boolean，默認為False，如果可能，減少返回類型的維度，否則返回一致類型 |
| observe    | 布爾值，默認為False，這僅適用於任何groupers屬於分類如果為真，如果為False：顯示分類groupers的所有值。 |
GroupBy 可以將數據分組以便後續操作。

簡單示例:GroupBy   
![使用seaborn下載數據](https://upload-images.jianshu.io/upload_images/13539817-23bf37371b831a51.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![GroupBy可以用於迭代](https://upload-images.jianshu.io/upload_images/13539817-b9714f4f3ef52025.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![以'key'columns分組將星期分組各組數量](https://upload-images.jianshu.io/upload_images/13539817-79e16736ff45c6a8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![套用計算方法(groupby不能直接套用numpy方法)](https://upload-images.jianshu.io/upload_images/13539817-4a38621538a9b954.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![只取tip列](https://upload-images.jianshu.io/upload_images/13539817-d2aad8e54ddfe4b5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![多列分組](https://upload-images.jianshu.io/upload_images/13539817-64157086d5c363a9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![取得將day的sun與sat改為hailday的數組](https://upload-images.jianshu.io/upload_images/13539817-24fb54f2d3889cef.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![sun與sat改為hailday的數組](https://upload-images.jianshu.io/upload_images/13539817-c0d4b5d5e716776f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![自訂義分組](https://upload-images.jianshu.io/upload_images/13539817-6cd3e12d85807f87.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![將索引重新對應](https://upload-images.jianshu.io/upload_images/13539817-57278f95333e7856.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![多重索引資料建立](https://upload-images.jianshu.io/upload_images/13539817-d8cb162a8644d54c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![多重索引資料分組](https://upload-images.jianshu.io/upload_images/13539817-2bb4fc410f465a3a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![若要按index可以使用.T轉置資料](https://upload-images.jianshu.io/upload_images/13539817-87dc1aed3e73723e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


##### Aggregation聚合(匯集) #####
[**DataFrame.aggregate**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.aggregate.html)
DataFrame.aggregate（func，axis = 0，* args，** kwargs ）
![aggregate操作](https://upload-images.jianshu.io/upload_images/13539817-a55c0033a86e68cf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### Applying(函數應用) #####
[**DataFrame.apply**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.apply.html)
DataFrame.apply（func，axis = 0，broadcast = None，raw = False，reduce = None，result_type = None，args =（），** kwds ）
![建立數據](https://upload-images.jianshu.io/upload_images/13539817-3b43c0981e0b77ab.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![apply操作1](https://upload-images.jianshu.io/upload_images/13539817-1173705314f30ac6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![apply操作2](https://upload-images.jianshu.io/upload_images/13539817-9502da5c61ad50d3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![apply的lambda操作(x=a,y=10,z=0)](https://upload-images.jianshu.io/upload_images/13539817-f5f0babc22a13b24.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


##### Transformation(轉換) #####
分組或列上的轉換返回索引大小與被分組的索引相同的對象。轉換應該返回與數據大小相同的結果。
[**DataFrame.transform**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.transform.html)
DataFrame.transform(func, *args, **kwargs)
![建立數據](https://upload-images.jianshu.io/upload_images/13539817-122a894372cd3419.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![transform操作1](https://upload-images.jianshu.io/upload_images/13539817-d28f65af44f86711.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![transform操作2](https://upload-images.jianshu.io/upload_images/13539817-07314d55542b4fd3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### Categorical(分類) ###
[**pandas.Categorical**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Categorical.html)
pandas.Categorical(values, categories=None, ordered=None, dtype=None, fastpath=False)
- **創建**
![創建分類1](https://upload-images.jianshu.io/upload_images/13539817-63bc7936c80656da.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![創建分類2](https://upload-images.jianshu.io/upload_images/13539817-0f76ed41dc64699f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![有序分類排序](https://upload-images.jianshu.io/upload_images/13539817-e4a791963b210e19.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![分類屬性操作](https://upload-images.jianshu.io/upload_images/13539817-834967fcee19848c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### string(字串) ###
Pandas的字串處理大部分接受[**正則表達式**](http://www.runoob.com/python3/python3-reg-expressions.html)([**另一個連結**](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/00143193331387014ccd1040c814dee8b2164bb4f064cff000))，Pandas提供了很多字串處理函數，如下:
| String   handling                                            |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Series.str.capitalize()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.capitalize.html#pandas.Series.str.capitalize) | 將Series / Index中的字符串轉換為大寫。                       |
| [Series.str.cat([others, sep, na_rep, join])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.cat.html#pandas.Series.str.cat) | 使用給定的分隔符連接Series / Index中的字符串。               |
| [Series.str.center(width[, fillchar])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.center.html#pandas.Series.str.center) | 使用附加字符填充系列/索引中字符串的左側和右側。              |
| [Series.str.contains(pat[, case, flags, na, …])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.contains.html#pandas.Series.str.contains) | 測試模式或正則表達式是否包含在系列或索引的字符串中。         |
| [Series.str.count(pat[, flags])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.count.html#pandas.Series.str.count) | 計算系列/索引的每個字符串中模式的出現次數。                  |
| [Series.str.decode(encoding[, errors])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.decode.html#pandas.Series.str.decode) | 使用指定的編碼解碼系列/索引中的字符串。                      |
| [Series.str.encode(encoding[, errors])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.encode.html#pandas.Series.str.encode) | 使用指定的編碼對系列/索引中的字符串進行編碼。                |
| [Series.str.endswith(pat[, na])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.endswith.html#pandas.Series.str.endswith) | 測試每個字符串元素的結尾是否與模式匹配。                     |
| [Series.str.extract(pat[, flags, expand])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.extract.html#pandas.Series.str.extract) | 對於系列中的每個主題字符串，從正則表達式pat的第一個匹配中提取組。 |
| [Series.str.extractall(pat[, flags])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.extractall.html#pandas.Series.str.extractall) | 對於系列中的每個主題字符串，從正則表達式pat的所有匹配中提取組。 |
| [Series.str.find(sub[, start, end])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.find.html#pandas.Series.str.find) | 返回Series / Index中每個字符串中的最低索引，其中子字符串完全包含在[start：end]之間。 |
| [Series.str.findall(pat[, flags])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.findall.html#pandas.Series.str.findall) | 在系列/索引中查找所有出現的模式或正則表達式。                |
| [Series.str.get(i)](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.get.html#pandas.Series.str.get) | 從指定位置的每個組件中提取元素。                             |
| [Series.str.index(sub[, start, end])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.index.html#pandas.Series.str.index) | 返回每個字符串中的最低索引，其中子字符串完全包含在[start：end]之間。 |
| [Series.str.join(sep)](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.join.html#pandas.Series.str.join) | 使用傳遞的分隔符連接包含在Series / Index中的元素的列表。     |
| [Series.str.len()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.len.html#pandas.Series.str.len) | 計算系列/索引中每個字符串的長度。                            |
| [Series.str.ljust(width[, fillchar])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.ljust.html#pandas.Series.str.ljust) | 使用附加字符填充系列/索引中字符串的右側。                    |
| [Series.str.lower()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.lower.html#pandas.Series.str.lower) | 將Series / Index中的字符串轉換為小寫。                       |
| [Series.str.lstrip([to_strip])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.lstrip.html#pandas.Series.str.lstrip) | 從左側的系列/索引中的每個字符串中刪除空格（包括換行符）。    |
| [Series.str.match(pat[, case, flags, na, …])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.match.html#pandas.Series.str.match) | 確定每個字符串是否與正則表達式匹配。                         |
| [Series.str.normalize(form)](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.normalize.html#pandas.Series.str.normalize) | 返回Series / Index中字符串的Unicode普通表單。                |
| [Series.str.pad(width[, side, fillchar])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.pad.html#pandas.Series.str.pad) | 在系列/索引中填充字符串，並在指定的一側添加一個字符。        |
| [Series.str.partition([pat, expand])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.partition.html#pandas.Series.str.partition) | 在第一次出現sep時拆分字符串，並返回包含分隔符之前的部分的3個元素，分隔符本身以及分隔符之後的部分。 |
| [Series.str.repeat(repeats)](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.repeat.html#pandas.Series.str.repeat) | 按指定的次數複製系列/索引中的每個字符串。                    |
| [Series.str.replace(pat, repl[, n, case, …])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.replace.html#pandas.Series.str.replace) | 用一些其他字符串替換Series / Index中出現的pattern / regex。  |
| [Series.str.rfind(sub[, start, end])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.rfind.html#pandas.Series.str.rfind) | 返回Series / Index中每個字符串中的最高索引，其中子字符串完全包含在[start：end]之間。 |
| [Series.str.rindex(sub[, start, end])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.rindex.html#pandas.Series.str.rindex) | 返回每個字符串中的最高索引，其中子字符串完全包含在[start：end]之間。 |
| [Series.str.rjust(width[, fillchar])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.rjust.html#pandas.Series.str.rjust) | 使用附加字符填充系列/索引中字符串的左側。                    |
| [Series.str.rpartition([pat, expand])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.rpartition.html#pandas.Series.str.rpartition) | 在最後一次出現sep時拆分字符串，並返回包含分隔符之前的部分的3個元素，分隔符本身以及分隔符之後的部分。 |
| [Series.str.rstrip([to_strip])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.rstrip.html#pandas.Series.str.rstrip) | 從右側的系列/索引中的每個字符串中刪除空格（包括換行符）。    |
| [Series.str.slice([start, stop, step])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.slice.html#pandas.Series.str.slice) | 從系列/索引中的每個元素切片子串                              |
| [Series.str.slice_replace([start, stop, repl])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.slice_replace.html#pandas.Series.str.slice_replace) | 用另一個值替換字符串的位置切片。                             |
| [Series.str.split([pat, n, expand])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.split.html#pandas.Series.str.split) | 在給定的分隔符/分隔符周圍拆分字符串。                        |
| [Series.str.rsplit([pat, n, expand])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.rsplit.html#pandas.Series.str.rsplit) | 通過給定的分隔符字符串拆分Series / Index中的每個字符串，從字符串的末尾開始並向前工作。 |
| [Series.str.startswith(pat[, na])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.startswith.html#pandas.Series.str.startswith) | 測試每個字符串元素的開頭是否與模式匹配。                     |
| [Series.str.strip([to_strip])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.strip.html#pandas.Series.str.strip) | 從左側和右側剝離系列/索引中每個字符串的空白（包括換行符）。  |
| [Series.str.swapcase()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.swapcase.html#pandas.Series.str.swapcase) | 將Series / Index中的字符串轉換為swapcased。                  |
| [Series.str.title()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.title.html#pandas.Series.str.title) | 將系列/索引中的字符串轉換為標題。                            |
| [Series.str.translate(table[, deletechars])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.translate.html#pandas.Series.str.translate) | 通過給定的映射表映射字符串中的所有字符。                     |
| [Series.str.upper()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.upper.html#pandas.Series.str.upper) | 將Series / Index中的字符串轉換為大寫。                       |
| [Series.str.wrap(width, **kwargs)](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.wrap.html#pandas.Series.str.wrap) | 將Series / Index中的長字符串換行，以長度小於給定寬度的段落格式化。 |
| [Series.str.zfill(width)](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.zfill.html#pandas.Series.str.zfill) | 使用0填充Series / Index中字符串的左側。                      |
| [Series.str.isalnum()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.isalnum.html#pandas.Series.str.isalnum) | 檢查Series / Index中每個字符串中的所有字符是否為字母數字。   |
| [Series.str.isalpha()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.isalpha.html#pandas.Series.str.isalpha) | 檢查Series / Index中每個字符串中的所有字符是否都是字母。     |
| [Series.str.isdigit()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.isdigit.html#pandas.Series.str.isdigit) | 檢查Series / Index中每個字符串中的所有字符是否為數字。       |
| [Series.str.isspace()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.isspace.html#pandas.Series.str.isspace) | 檢查Series / Index中每個字符串中的所有字符是否都是空格。     |
| [Series.str.islower()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.islower.html#pandas.Series.str.islower) | 檢查Series / Index中每個字符串中的所有字符是否都是小寫。     |
| [Series.str.isupper()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.isupper.html#pandas.Series.str.isupper) | 檢查Series / Index中每個字符串中的所有字符是否都是大寫。     |
| [Series.str.istitle()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.istitle.html#pandas.Series.str.istitle) | 檢查Series / Index中每個字符串中的所有字符是否都是標題。     |
| [Series.str.isnumeric()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.isnumeric.html#pandas.Series.str.isnumeric) | 檢查Series / Index中每個字符串中的所有字符是否都是數字。     |
| [Series.str.isdecimal()](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.isdecimal.html#pandas.Series.str.isdecimal) | 檢查Series / Index中每個字符串中的所有字符是否為十進制。     |
| [Series.str.get_dummies([sep])](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.str.get_dummies.html#pandas.Series.str.get_dummies) | 用sep拆分Series中的每個字符串，並返回一個虛擬/指示變量框。   |

![範例](https://upload-images.jianshu.io/upload_images/13539817-274de469cb60170e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



### Date(日期) ###
[**python的Date和Time功能**](http://www.runoob.com/python3/python3-date-time.html)
[**python的Date和Time官方文檔1**](https://docs.python.org/3/library/datetime.html)
[**python的Date和Time官方文檔2**](https://docs.python.org/3/library/time.html)
[**numpy日期**](https://www.jianshu.com/writer#/notebooks/28728259/notes/33244811/preview)
[**pandas時間序列/日期功能**](https://pandas.pydata.org/pandas-docs/stable/timeseries.html)
- 時間類型    
![時間類型](https://upload-images.jianshu.io/upload_images/13539817-5a79ab6c7b6b0001.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 時間偏移週期

| 別名     | 描述                       |
| -------- | -------------------------- |
| B        | 工作日頻率                 |
| C        | 自定義工作日頻率           |
| D        | 日曆日頻率                 |
| W        | 每週頻率                   |
| M        | 月末頻率                   |
| SM       | 半月結束頻率（15日和月末） |
| BM       | 營業月結束頻率             |
| CBM      | 自定義營業月結束頻率       |
| MS       | 月開始頻率                 |
| SMS      | 半月開始頻率（第1和第15）  |
| BMS      | 營業月開始頻率             |
| CBMS     | 自定義營業月開始頻率       |
| Q        | 四分之一結束頻率           |
| BQ       | 業務季度結束頻率           |
| QS       | 季度開始頻率               |
| BQS      | 業務季開始頻率             |
| A, Y     | 年終頻率                   |
| BA, BY   | 業務年度結束頻率           |
| AS, YS   | 年開始頻率                 |
| BAS, BYS | 營業年度開始頻率           |
| BH       | 營業時間頻率               |
| H        | 每小時頻率                 |
| T, min   | 每分鐘的頻率                 |
| S        | 每秒頻率                     |
| L, ms    | 毫秒                       |
| U, us    | 微秒                       |
| N        | 納秒                       |

- 建立    
![創建日期1](https://upload-images.jianshu.io/upload_images/13539817-24885af33fa451e6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![創建日期2](https://upload-images.jianshu.io/upload_images/13539817-4ac57751ce8dd1b7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 轉換
![轉換日期1](https://upload-images.jianshu.io/upload_images/13539817-c7e01dd168758eb3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![轉換日期2](https://upload-images.jianshu.io/upload_images/13539817-f8fe318ecc03dedc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 讀寫檔案 ###    
[**Pandas讀寫文檔**](http://pandas.pydata.org/pandas-docs/stable/io.html)
| Format   Type | Data Description                                             | Reader                                                       | Writer                                                       |
| ------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| text          | [CSV](https://en.wikipedia.org/wiki/Comma-separated_values)  | [read_csv](http://pandas.pydata.org/pandas-docs/stable/io.html#io-read-csv-table) | [to_csv](http://pandas.pydata.org/pandas-docs/stable/io.html#io-store-in-csv) |
| text          | [JSON](http://www.json.org/)                                 | [read_json](http://pandas.pydata.org/pandas-docs/stable/io.html#io-json-reader) | [to_json](http://pandas.pydata.org/pandas-docs/stable/io.html#io-json-writer) |
| text          | [HTML](https://en.wikipedia.org/wiki/HTML)                   | [read_html](http://pandas.pydata.org/pandas-docs/stable/io.html#io-read-html) | [to_html](http://pandas.pydata.org/pandas-docs/stable/io.html#io-html) |
| text          | Local   clipboard                                            | [read_clipboard](http://pandas.pydata.org/pandas-docs/stable/io.html#io-clipboard) | [to_clipboard](http://pandas.pydata.org/pandas-docs/stable/io.html#io-clipboard) |
| binary        | [MS Excel](https://en.wikipedia.org/wiki/Microsoft_Excel)    | [read_excel](http://pandas.pydata.org/pandas-docs/stable/io.html#io-excel-reader) | [to_excel](http://pandas.pydata.org/pandas-docs/stable/io.html#io-excel-writer) |
| binary        | [HDF5 Format](https://support.hdfgroup.org/HDF5/whatishdf5.html) | [read_hdf](http://pandas.pydata.org/pandas-docs/stable/io.html#io-hdf5) | [to_hdf](http://pandas.pydata.org/pandas-docs/stable/io.html#io-hdf5) |
| binary        | [Feather Format](https://github.com/wesm/feather)            | [read_feather](http://pandas.pydata.org/pandas-docs/stable/io.html#io-feather) | [to_feather](http://pandas.pydata.org/pandas-docs/stable/io.html#io-feather) |
| binary        | [Parquet Format](https://parquet.apache.org/)                | [read_parquet](http://pandas.pydata.org/pandas-docs/stable/io.html#io-parquet) | [to_parquet](http://pandas.pydata.org/pandas-docs/stable/io.html#io-parquet) |
| binary        | [Msgpack](http://msgpack.org/index.html)                     | [read_msgpack](http://pandas.pydata.org/pandas-docs/stable/io.html#io-msgpack) | [to_msgpack](http://pandas.pydata.org/pandas-docs/stable/io.html#io-msgpack) |
| binary        | [Stata](https://en.wikipedia.org/wiki/Stata)                 | [read_stata](http://pandas.pydata.org/pandas-docs/stable/io.html#io-stata-reader) | [to_stata](http://pandas.pydata.org/pandas-docs/stable/io.html#io-stata-writer) |
| binary        | [SAS](https://en.wikipedia.org/wiki/SAS_(software))          | [read_sas](http://pandas.pydata.org/pandas-docs/stable/io.html#io-sas-reader) |                                                              |
| binary        | [Python Pickle Format](https://docs.python.org/3/library/pickle.html) | [read_pickle](http://pandas.pydata.org/pandas-docs/stable/io.html#io-pickle) | [to_pickle](http://pandas.pydata.org/pandas-docs/stable/io.html#io-pickle) |
| SQL           | [SQL](https://en.wikipedia.org/wiki/SQL)                     | [read_sql](http://pandas.pydata.org/pandas-docs/stable/io.html#io-sql) | [to_sql](http://pandas.pydata.org/pandas-docs/stable/io.html#io-sql) |
| SQL           | [Google Big Query](https://en.wikipedia.org/wiki/BigQuery)   | [read_gbq](http://pandas.pydata.org/pandas-docs/stable/io.html#io-bigquery) | [to_gbq](http://pandas.pydata.org/pandas-docs/stable/io.html#io-bigquery) |

##### csv #####
1)讀
[**pandas.read_csv**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.read_csv.html)
pandas.read_csv(filepath_or_buffer, sep=', ', delimiter=None, header='infer', names=None, index_col=None, usecols=None, squeeze=False, prefix=None, mangle_dupe_cols=True, dtype=None, engine=None, converters=None, true_values=None, false_values=None, skipinitialspace=False, skiprows=None, nrows=None, na_values=None, keep_default_na=True, na_filter=True, verbose=False, skip_blank_lines=True, parse_dates=False, infer_datetime_format=False, keep_date_col=False, date_parser=None, dayfirst=False, iterator=False, chunksize=None, compression='infer', thousands=None, decimal=b'.', lineterminator=None, quotechar='"', quoting=0, escapechar=None, comment=None, encoding=None, dialect=None, tupleize_cols=None, error_bad_lines=True, warn_bad_lines=True, skipfooter=0, doublequote=True, delim_whitespace=False, low_memory=True, memory_map=False, float_precision=None)

2)寫
[**DataFrame.to_csv**](https://pandas.pydata.org/pandas-docs/version/0.23/generated/pandas.DataFrame.to_csv.html)
DataFrame.to_csv(path_or_buf=None, sep=', ', na_rep='', float_format=None, columns=None, header=True, index=True, index_label=None, mode='w', encoding=None, compression=None, quoting=None, quotechar='"', line_terminator='\n', chunksize=None, tupleize_cols=None, date_format=None, doublequote=True, escapechar=None, decimal='.')
[**Series.to_csv**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.to_csv.html)
Series.to_csv(path=None, index=True, sep=', ', na_rep='', float_format=None, header=False, index_label=None, mode='w', encoding=None, compression=None, date_format=None, decimal='.')

3)讀寫範例
原始資料:     
![原始資料:](https://upload-images.jianshu.io/upload_images/13539817-86141a7ff8fc7dcb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

讀取資料:    
![讀取資料](https://upload-images.jianshu.io/upload_images/13539817-cd1f1730cfc30374.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

轉成直式:
![轉成直式](https://upload-images.jianshu.io/upload_images/13539817-c30a6c35b27e7b25.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

刪除重複值、排序、計數:
>np.unique(df,return_counts=True)
np.unique(刪除重覆值)，return_counts=True(計數)
>輸出一個元組(整理後的值，對應的計數)    

![刪除重複值、排序、計數](https://upload-images.jianshu.io/upload_images/13539817-e6e6e51a6ffda64a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

加上columns:     
![加上columns標題](https://upload-images.jianshu.io/upload_images/13539817-b93e59bbb53f5fcf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

輸出csv檔:     
![輸出csv檔](https://upload-images.jianshu.io/upload_images/13539817-b9970d6323134dbf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![輸出完成](https://upload-images.jianshu.io/upload_images/13539817-da0c33d8fe68191a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)










