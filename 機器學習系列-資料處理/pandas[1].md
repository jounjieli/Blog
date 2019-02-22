[pandas1](https://www.jianshu.com/p/5114db1e603f)
[pandas2](https://www.jianshu.com/p/58d5ae4b848f)
---
### 匯入模組 ###
```python
import numpy as np
import pandas as pd
```
Pandas是建立在numpy的一個資料處理套件。
---
### Pandas 數據結構 ###
**1) Series**
**2) DataFrame**
##### ♦Series 物件 #####
| 常用的屬性或方法 | 描述                            |
| ---------- | ------------------------------- |
| axes       | 返回行軸標籤的列表。            |
| dtype      | 返回對象的dtype。               |
| empty      | 如果系列為空，則返回True。      |
| ndim       | 根據定義1，返回基礎數據的維數。 |
| size       | 返回基礎數據中的元素數。        |
| values     | 將系列返回為ndarray。           |
| head()     | 返回前n行。                     |
| tail()     | 返回最後n行。                   |

- 建立
[**pandas.Series**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.html)
Pandas Series是被索引資料的一維數組，他可以使用Array、Dict、Scalar value or constant來建立。

pandas.Series(data=None, index=None, dtype=None, name=None, copy=False, fastpath=False)    
| 參數    | 描述                                                         |
| ------- | ------------------------------------------------------------ |
| 1.data  | 數據採用各種形式，如ndarray，list，常量                      |
| 2.index | 索引值必須是唯一且可清除的，與數據長度相同。如果沒有傳遞索引，則默認為np.arrange（n）。 |
| 3.dtype | dtype用於數據類型。如果為None，則將推斷數據類型              |
| 4.copy  | 複製數據。默認為False                                        |
![Series建立及索引](https://upload-images.jianshu.io/upload_images/13539817-33c21bf44834ff90.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![Series索引](https://upload-images.jianshu.io/upload_images/13539817-3c8f68f824d627c9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![以dict建立](https://upload-images.jianshu.io/upload_images/13539817-1ecceb54a86b6d0b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 映射 (map與one hot encoding)
[**pandas.Series.map**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Series.map.html#pandas.Series.map)
[**pandas.get_dummies**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.get_dummies.html)
![範例](https://upload-images.jianshu.io/upload_images/13539817-d67661692eca1e2a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![範例](https://upload-images.jianshu.io/upload_images/13539817-1063451f7d8e7f19.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 重置
[DataFrame.reset_index](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.reset_index.html)
[Series.reset_index](https://pandas-docs.github.io/pandas-docs-travis/generated/pandas.Series.reset_index.html)
![範例](https://upload-images.jianshu.io/upload_images/13539817-ce933660efb4f7eb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![範例](https://upload-images.jianshu.io/upload_images/13539817-514f60d27c0c9716.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### ♦DataFrame 物件 #####
| 常用的屬性或方法 | 描述                                                         |
| ---------------- | ------------------------------------------------------------ |
| T                | 轉置行和列。                                                 |
| axes             | 返回一個列表，其中行軸標籤和列軸標籤為唯一成員。             |
| dtypes           | 返回此對像中的dtypes。                                       |
| empty            | 如果NDFrame完全為空，則為True [無項目]; 如果任何軸的長度為0。 |
| ndim             | 軸數/數組尺寸。                                              |
| shape            | 返回表示DataFrame維度的元組。                                |
| size             | NDFrame中的元素數。                                          |
| values           | NDFrame的Numpy表示。                                         |
| head()           | 返回前n行。                                                  |
| tail()           | 返回最後n行。                                                |

可以使用各種輸入創建pandas DataFrame，包括 Lists、dict、Series、Numpy ndarrays、另一個 DataFrame
[**pandas.DataFrame**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html)
pandas.DataFrame(data=None, index=None, columns=None, dtype=None, copy=False)
| 參數    | 描述                                                         |
| ------- | ------------------------------------------------------------ |
| data    | 數據採用各種形式，如ndarray，系列，地圖，列表，字典，常量以及另一個DataFrame。 |
| index   | 對於行標籤，如果沒有傳遞索引，則用於結果幀的索引是Optional   Default np.arrange（n）。 |
| columns | 對於列標籤，可選的默認語法是 -   np.arrange（n）。僅當沒有傳遞索引時才會出現這種情況。 |
| dtype   | 每列的數據類型。                                             |
| copy    | 如果默認值為False，則此命令（或其他任何命令）用於復制數據。  |
- 建立  
![以list(or ndarray)及tuple建立](https://upload-images.jianshu.io/upload_images/13539817-f5b770e575777b08.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![以dict建立](https://upload-images.jianshu.io/upload_images/13539817-c404a62c80fdd457.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![以Series建立](https://upload-images.jianshu.io/upload_images/13539817-3056cee6fc65c45f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
- 索引、添加、修改    
 ![簡單索引示例](https://upload-images.jianshu.io/upload_images/13539817-ecc9a4e06fccf302.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![添加](https://upload-images.jianshu.io/upload_images/13539817-3c142c5a85a54293.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![修改](https://upload-images.jianshu.io/upload_images/13539817-35ce0779b9548c23.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![使用切片索引修改值](https://upload-images.jianshu.io/upload_images/13539817-a63d2b120a86d940.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 刪除    
[**DataFrame.drop**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.drop.html)
DataFrame.drop(labels=None,axis=0, index=None, columns=None, inplace=False)

| 參數           | 描述                                                         |
| -------------- | ------------------------------------------------------------ |
| labels         | 要刪除的索引標籤或列標籤。                                   |
| axis           | {0或'index'，1或'columns'}，默認為0                          |
| index, columns | 要刪除的索引標籤跟列標籤。                                   |
| level          | int或level   name，可選，對於MultiIndex，將從中刪除標籤的級別。 |
| inplace        | bool，默認為False，如果為True，則進行就地操作並返回None。    |
| errors         | {‘ignore’, ‘raise’},   默認‘raise’，如果“忽略”，則禁止錯誤，僅刪除現有標籤。 |
![資料建立](https://upload-images.jianshu.io/upload_images/13539817-3ccc679aba5bbb75.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![刪除演示](https://upload-images.jianshu.io/upload_images/13539817-f9f79394edd46f4a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 查找及刪除重複
[DataFrame.duplicated](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.duplicated.html)
[DataFrame.drop_duplicates](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.drop_duplicates.html)     
![](https://upload-images.jianshu.io/upload_images/13539817-6139dd2b0b4c58fc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)      ![查找重複](https://upload-images.jianshu.io/upload_images/13539817-0b7bb90184bcca2f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![刪除重複](https://upload-images.jianshu.io/upload_images/13539817-002a1614eb3c69b7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 加入、合併    
[**pandas合併**](https://pandas.pydata.org/pandas-docs/stable/merging.html)   
1) [**DataFrame.append**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.copy.html)
DataFrame.append(other, ignore_index=False, verify_integrity=False, sort=None)

| 參數             | 描述                                                         |
| ---------------- | ------------------------------------------------------------ |
| other            | DataFrame或Series / dict-like對象，或者這些對象的列表。(要追加的數據) |
| ignore_index     | boolean，默認為False，如果為True，請不要使用索引標籤。       |
| verify_integrity | boolean，默認為False，如果為True，則在創建具有重複項的索引時引發ValueError。 |
| sort             | boolean, 默認為   None，如果self和other的列未對齊，請對列進行排序。不推薦使用默認排序，並將在未來版本的pandas中更改為not-sorting。   顯式傳遞sort = True以使警告靜音並排序。 顯式傳遞sort = False以使警告靜音而不進行排序。 |
![加入演示](https://upload-images.jianshu.io/upload_images/13539817-f6591af0f7cb482c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![使用ignore_index忽略原索引](https://upload-images.jianshu.io/upload_images/13539817-d99f1c914826bf76.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2) [**pandas.concat**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.concat.html)
pandas.concat(objs, axis=0, join='outer', join_axes=None, ignore_index=False, keys=None, levels=None, names=None, verify_integrity=False, sort=None, copy=True)

| 參數             | 描述                                                         |
| ---------------- | ------------------------------------------------------------ |
| objs             | Series，DataFrame或Panel對象的序列或映射，如果傳遞了dict，則排序的鍵將用作keys   參數，除非它被傳遞，在這種情況下將選擇值（見下文）。任何None對像都將以靜默方式刪除，除非它們都是None，在這種情況下將引發ValueError |
| axis             | {0 /'index'，1 /'columns'}，默認為0，軸連接起來              |
| join             | {'inner'，'outer'}，默認'outer'，如何處理其他軸上的索引(inner使用交集、outer使用聯集)       |
| join_axes        | 索引對象列表，用於其他n - 1軸的特定索引，而不是執行內部/外部設置邏輯 |
| ignore_index     | boolean，默認為False，如果為True，請不要使用串聯軸上的索引值。生成的軸將標記為0，...，n -   1.如果要連接並置軸沒有有意義的索引信息的對象，這將非常有用。請注意，在連接中仍然遵循其他軸上的索引值。 |
| keys             | 序列，默認None，如果傳遞了多個級別，則應包含元組。使用傳遞的鍵作為最外層來構造層次索引 |
| levels           | 要判斷的序列列表，默認為None，用於構造MultiIndex的特定級別（唯一值）。否則，他們將從鍵中推斷出來 |
| names            | list，默認None，生成的分層索引中的級別的名稱                 |
| verify_integrity | boolean，默認為False，檢查新的連鎖軸是否包含重複項。相對於實際數據連接，這可能非常昂貴 |
| sort             | boolean, 默認 None，如果在連接 為“外部”   時尚未對齊，則對非連接軸進行排序。不推薦使用當前的排序默認值，並且將在未來版本的pandas中更改為not-sorting。明確地傳遞sort=True警告並排序。明確地通過sort=False沉默警告而不是排序。當join='inner'已經保留非連接軸的順序時，這沒有效果。版本0.23.0中的新功能。 |
| copy             | boolean，默認為True，如果為False，則不要複制數據             |

![axis參數演示](https://upload-images.jianshu.io/upload_images/13539817-dab7bbb33555cee2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![ignore_index、verify_integrity(如果有重複像則報錯)演示](https://upload-images.jianshu.io/upload_images/13539817-64ac4d041092d116.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![keys](https://upload-images.jianshu.io/upload_images/13539817-816a8a9678ba9c59.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![建立資料](https://upload-images.jianshu.io/upload_images/13539817-db21b17f9d420ca6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![sort、join](https://upload-images.jianshu.io/upload_images/13539817-88e369a0cb37c76d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![join_axes](https://upload-images.jianshu.io/upload_images/13539817-2d8810fc3c4163d1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3) [**DataFrame.merge**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.merge.html)
默認會自動對應相同欄位內容進行合併。
DataFrame.merge(right, how='inner', on=None, left_on=None, right_on=None, left_index=False, right_index=False, sort=False, suffixes=('_x', '_y'), copy=True, indicator=False, validate=None)

| 參數        | 描述                                                         |
| ----------- | ------------------------------------------------------------ |
| right       | DataFrame                                                    |
| how         | {‘left’, ‘right’, ‘outer’, ‘inner’}, default   ‘inner’，left：僅使用左框架中的鍵，類似於SQL左外連接; 保留關鍵順序，right：僅使用右框架中的鍵，類似於SQL右外連接;   保留關鍵順序，outer：使用來自兩個幀的鍵的並集，類似於SQL全外連接; 按字典順序排序鍵，inner：使用兩個幀的鍵交集，類似於SQL內連接;   保留左鍵的順序。 |
| on          | 標籤或列表，要加入的列或索引級別名稱。這些必須在兩個DataFrame中找到。如果on為None且未合併索引，則默認為兩個DataFrame中列的交集。 |
| left_on     | 標籤或列表，或類似數組，要在左側DataFrame中連接的列級或索引級別名稱。也可以是左數據幀長度的數組或數組列表。這些數組被視為列。 |
| right_on    | 標籤或列表，或類似數組，要在右側DataFrame中連接的列級或索引級別名稱。也可以是右側DataFrame長度的數組或數組列表。這些數組被視為列。 |
| left_index  | 布爾值，默認為False，使用左側DataFrame中的索引作為連接鍵。如果是MultiIndex，則其他DataFrame中的鍵數（索引或列數）必須與級別數相匹配 |
| right_index | 布爾值，默認為False，使用右側DataFrame中的索引作為連接鍵。與left_index相同的警告 |
| sort        | 布爾值，默認為False，在結果DataFrame中按字典順序對連接鍵進行排序。如果為False，則連接鍵的順序取決於連接類型（關鍵字如何） |
| suffixes    | 2長度序列（元組，列表，...），後綴分別應用於左側和右側的重疊列名稱 |
| copy        | boolean，默認為True，如果為False，則不要不必要地複制數據     |
| indicator   | 布爾值或字符串，默認為False，如果為True，則添加一列以輸出名為“_merge”的DataFrame，其中包含每行源的信息。如果string，具有每行源的信息的列將被添加到輸出DataFrame，並且列將被命名為string的值。信息列為分類型，對於其合併鍵僅出現在“左”DataFrame中的觀察值為“left_only”，對於其合併鍵僅出現在“右”DataFrame中的觀察值為“right_only”，如果為觀察的合併密鑰在兩者中找到。 |
| validate    | string, default   None，如果指定，則檢查merge是否為指定類型。one_to_one”或“1：1”檢查合併鍵是否在左右數據集中都是唯一的。 “one_to_many”或“1：m”檢查合併鍵在左數據集中是否唯一。 “many_to_one”或“m：1”檢查合併鍵在右側數據集中是否唯一。 “many_to_many”或“m：m”允許，但不會導致檢查。 |
![資料建立](https://upload-images.jianshu.io/upload_images/13539817-2f43932754d95421.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![merge直接操作及資料建立](https://upload-images.jianshu.io/upload_images/13539817-39a5acfd19ea78ac.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![on演示及資料建立](https://upload-images.jianshu.io/upload_images/13539817-fc8ccd1cbc7b159c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![left_on、right_on、left_index、right_index演示](https://upload-images.jianshu.io/upload_images/13539817-cef37ec3e253f975.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![suffixes演示](https://upload-images.jianshu.io/upload_images/13539817-2dca7b00d0bd896e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![資料建立](https://upload-images.jianshu.io/upload_images/13539817-ca97b0d39c1d98f7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![how演示](https://upload-images.jianshu.io/upload_images/13539817-3bb9bf0a2dd4df10.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

4) [**DataFrame.join**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.join.html)
DataFrame.join(other, on=None, how='left', lsuffix='', rsuffix='', sort=False)    

| 參數    | 描述                                                         |
| ------- | ------------------------------------------------------------ |
| other   | DataFrame，具有名稱字段集的系列或DataFrame列表，索引應該類似於此列中的一列。如果傳遞了Series，則必須設置其name屬性，並將其用作生成的連接DataFrame中的列名 |
| on      | name，tuple / names of   list或array-like，調用者中的列或索引級別名稱，用於連接其他索引，否則加入index-on-index。如果給定多個值，則另一個   DataFrame必須具有MultiIndex。如果數組尚未包含在調用DataFrame中，則可以將數組作為連接鍵傳遞。像Excel   VLOOKUP操作一樣 |
| how     | {‘left’, ‘right’, ‘outer’,   ‘inner’}, default   ‘left’，如何處理這兩個對象的操作。left：使用調用框架的索引（如果指定了on，則使用列），right：使用其他框架的索引，outer：調用框架索引的形式聯合（或指定的列，如果指定）與其他框架的索引，並按字典順序對其進行排序，inner：調用框架索引（或指定的列，如果指定）與其他框架索引的形式交集，保留調用框架的索引順序 |
| lsuffix | string，從左框架的重疊列使用的後綴                           |
| rsuffix | string，從右框架的重疊列使用後綴                             |
| sort    | 布爾值，默認為False，按連接鍵按字典順序排序結果DataFrame。如果為False，則連接鍵的順序取決於連接類型（關鍵字如何） |

- 索引調換
[**DataFrame.reindex**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.reindex.html#pandas.DataFrame.reindex)
DataFrame.reindex(labels=None, index=None, columns=None, axis=None, method=None, copy=True, level=None, fill_value=nan, limit=None, tolerance=None)
![範例](https://upload-images.jianshu.io/upload_images/13539817-57cee1ec5b46d9e9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![範例2](https://upload-images.jianshu.io/upload_images/13539817-79f71be6defb6d17.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


- 複製   
複製DataFrame以及DataFrame切片(與numpy相同切片是原DataFrame視圖，需要維新資料時須使用.copy() )資料。
[**DataFrame.copy**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.copy.html)
DataFrame.copy(deep=True)
![copy方法](https://upload-images.jianshu.io/upload_images/13539817-59446b4b6204000a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 遍歷(iterrows)
[DataFrame.iterrows](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.iterrows.html#pandas-dataframe-iterrows)
![](https://upload-images.jianshu.io/upload_images/13539817-179c2c596602c89c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![](https://upload-images.jianshu.io/upload_images/13539817-6c6a2a5994622215.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![](https://upload-images.jianshu.io/upload_images/13539817-024afb1a039b9649.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

---
### Index、column 索引 ###
##### ♦Index 物件 #####
Index 、columns都是[**Index**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.Index.html)物件。    
![Index 、columns索引及修改](https://upload-images.jianshu.io/upload_images/13539817-3704bb27c0465f3b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### ♦索引操作 #####  
- [**loc**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.loc.html)、[**iloc**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.iloc.html)
loc可傳入index或column名稱，iloc可傳入index或column代號(數字)，loc也可傳入相應形狀的bool值(1維)，多維需要直接使用[]。
![建立資料及比較操作(傳回真值表)](https://upload-images.jianshu.io/upload_images/13539817-4409802790261444.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![loc及iloc操作](https://upload-images.jianshu.io/upload_images/13539817-22ddb1e5df044e5b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![不連續直接索引](https://upload-images.jianshu.io/upload_images/13539817-a5feb6dcf6a14e77.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![混和運用](https://upload-images.jianshu.io/upload_images/13539817-9b260b3f2bb93d93.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![混和運用 (與 ［filter3 , :］同義)，可以直接使用[ ] ](https://upload-images.jianshu.io/upload_images/13539817-832ee9a0c8025580.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![混和運用](https://upload-images.jianshu.io/upload_images/13539817-bf240e4bbba00f5e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![配合flatnonzero](https://upload-images.jianshu.io/upload_images/13539817-6925bfdfe54190e7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![配合flatnonzero](https://upload-images.jianshu.io/upload_images/13539817-eae34e8bea693316.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     
- 查找NAN值
np.nan需要使用[pandas.isnull](https://pandas.pydata.org/pandas-docs/version/0.23.4/generated/pandas.isnull.html#pandas-isnull)查找。     
![查找nan值](https://upload-images.jianshu.io/upload_images/13539817-ae565df1f7609def.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![修改nan值](https://upload-images.jianshu.io/upload_images/13539817-336930f4a8011b87.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 最大直索引(常用於one hot reverse)
[pandas.DataFrame.idxmax](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.idxmax.html#pandas-dataframe-idxmax)
![](https://upload-images.jianshu.io/upload_images/13539817-fd23715d1d45b8d4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

---
### 計算 ###
##### ♦基本運算 #####
![運算符的使用](https://upload-images.jianshu.io/upload_images/13539817-a7e3d8eed26bce06.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![運算符的使用及使用numpy計算方法](https://upload-images.jianshu.io/upload_images/13539817-ad88c3962eb3b3a1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![describe方法](https://upload-images.jianshu.io/upload_images/13539817-feed678364b081f4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![計算密度](https://upload-images.jianshu.io/upload_images/13539817-3989a6a1ce7bd532.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


##### ♦Broadcasting(廣播) #####
numpy的Broadcasting特性:    
![array的Broadcasting特性](https://upload-images.jianshu.io/upload_images/13539817-84725ea4175ba774.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![pandas的Broadcasting特性](https://upload-images.jianshu.io/upload_images/13539817-d34ba6f0db85f571.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

---
### 缺失資料 ###
##### ♦類型 #####
pandas使用NaN與None來表示空值。
- None
有None資料，只能維python的Object形式，會降低整個資料的運算效率。
*補充:pandas的字串是以Object形式儲存的。
![](https://upload-images.jianshu.io/upload_images/13539817-130ac21f75c9d0fc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- NaN
NaN是一個IEEE浮點數的一個特殊值，NaN做運算=NaN。
![](https://upload-images.jianshu.io/upload_images/13539817-8813323a4faadc90.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### ♦Null值操作(NA值) #####
1) isnull()
2) notnull()
3) dropna()
4) fillna()

- [**isnull()**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.isnull.html)
[**notnull()**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.notnull.html)   
傳回空值或非空值的布林值。
![1](https://upload-images.jianshu.io/upload_images/13539817-ea0cdc56e39b6d58.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- [**dropna()**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.dropna.html)
移除空值的欄或列。    
![1](https://upload-images.jianshu.io/upload_images/13539817-63e04975c59a9554.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![2](https://upload-images.jianshu.io/upload_images/13539817-cff182b8c676e0a1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- [**fillna()**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.fillna.html)
填入空值。   
![1](https://upload-images.jianshu.io/upload_images/13539817-f4f9e3df5148daac.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![2](https://upload-images.jianshu.io/upload_images/13539817-b422c1ba47bffbc3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

---
### 階層(多重)索引 ###
類似pandas.panel，但panel以棄用，pandas建議使用多重索引方式來表示。
##### ♦MultiIndex 物件 #####
[**MultiIndex**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.MultiIndex.html)
| [MultiIndex.from_arrays](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.MultiIndex.from_arrays.html#pandas.MultiIndex.from_arrays) |
| ------------------------------------------------------------ |
| 將數組列表轉換為MultiIndex                                   |
| [MultiIndex.from_product](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.MultiIndex.from_product.html#pandas.MultiIndex.from_product) |
| 從迭代的笛卡爾積中創建一個MultiIndex                         |
| [MultiIndex.from_tuples](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.MultiIndex.from_tuples.html#pandas.MultiIndex.from_tuples) |
| 將元組列表轉換為MultiIndex                                   |
- **建立**  
![MultiIndex建立](https://upload-images.jianshu.io/upload_images/13539817-ea4c56deb695225c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![MultiIndex建立](https://upload-images.jianshu.io/upload_images/13539817-71ce001147266e9f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   

-**刪除**    
![刪除](https://upload-images.jianshu.io/upload_images/13539817-43daa3b28a57ec87.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- **添加索引名稱**  
![建立資料](https://upload-images.jianshu.io/upload_images/13539817-34081375a4f8ce7c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![添加索引名稱index](https://upload-images.jianshu.io/upload_images/13539817-e6ddec364eb959ba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![添加索引名稱columns](https://upload-images.jianshu.io/upload_images/13539817-bcd5cf27325df36a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- **多重索引切片**
![多重索引切片](https://upload-images.jianshu.io/upload_images/13539817-c6d276370efe590e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- **多重索引排序**
Pandas索引若無進行排序，使用切片取連續資料會出現錯誤，可使用numpy方法或下面介紹的pandas方法進行排序。
::錯誤示例::  ![錯誤示例](https://upload-images.jianshu.io/upload_images/13539817-6efb48ab0143057a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
1) DataFrame.sort_index()　：按照索引排序。   
[**DataFrame.sort_index**](https://pandas.pydata.org/pandas-docs/version/0.22/generated/pandas.DataFrame.sort_index.html)
![資料建立](https://upload-images.jianshu.io/upload_images/13539817-4a6f88781c648e0b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![按照索引排序](https://upload-images.jianshu.io/upload_images/13539817-2f7f4206b7b8879b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2) DataFrame.sort_values()　：按照內容(值)排序。
[**DataFrame.sort_values**](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.sort_values.html)
![資料建立](https://upload-images.jianshu.io/upload_images/13539817-de0f8e920f645b9d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![按照內容(值)排序(單欄)](https://upload-images.jianshu.io/upload_images/13539817-4e299f4a02f87030.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![按照內容(值)排序(多欄)](https://upload-images.jianshu.io/upload_images/13539817-02360797c6962c43.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![按照內容(值)排序(行)](https://upload-images.jianshu.io/upload_images/13539817-4dc21f01b36a7855.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- **快速轉換**  
1) 單層    
![資料建立](https://upload-images.jianshu.io/upload_images/13539817-1cb327eb020beafe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![stack()](https://upload-images.jianshu.io/upload_images/13539817-128b301c2fcf3a6a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![unstack()](https://upload-images.jianshu.io/upload_images/13539817-62443ade48765a53.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2) 多層    
![unstack()](https://upload-images.jianshu.io/upload_images/13539817-469ced2840acfe16.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![stack()](https://upload-images.jianshu.io/upload_images/13539817-d9e9ccbfd3cd0713.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)





