[numpy1](https://www.jianshu.com/p/166e04e7b659)
[numpy2](https://www.jianshu.com/p/520084e85f2d)
[numpy3](https://www.jianshu.com/p/98deb28eacbe)
### 數組的操作 ###
##### 基本索引array[ ] #####
**一.**  [一維(由0開始數)][二維(由0開始數)]
![](https://upload-images.jianshu.io/upload_images/13539817-0213fcca0799ae61.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![](https://upload-images.jianshu.io/upload_images/13539817-86a36970d870e6c8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**二.**  [負號表示由後往回數第幾個(由1開始數)]
![](https://upload-images.jianshu.io/upload_images/13539817-dcfa978ddd454612.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**三.**  由索引修改數組的值
![](https://upload-images.jianshu.io/upload_images/13539817-7634fec71b7d34f1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**四.**返回數組中的非零索引的展開。
[numpy.flatnonzero](https://docs.scipy.org/doc/numpy/reference/generated/numpy.flatnonzero.html#numpy-flatnonzero)
[numpy.nonzero](https://docs.scipy.org/doc/numpy/reference/generated/numpy.nonzero.html#numpy-nonzero)
![](https://upload-images.jianshu.io/upload_images/13539817-bdcd94d7d1df7d0d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


##### 切片array[::] #####
- 切片array[::]
使用切片時並非重新複製資料，而是傳回子陣列的視圖，想重新複製出資料須使用array[::].copy()。
注意：row、column都以0為起始列。
注意：[:]以及[::]的不同，[::-1]第3個值-1表示翻轉。  
![1](https://upload-images.jianshu.io/upload_images/13539817-a8f361deb0b74046.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![1](https://upload-images.jianshu.io/upload_images/13539817-1b9b6b67bf94dce5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![2](https://upload-images.jianshu.io/upload_images/13539817-c763ff280cc93f73.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
- 切片array[[ ]]  
![指定某row、column索引](https://upload-images.jianshu.io/upload_images/13539817-a3c34bd252be96cc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![使用bool索引，必須傳入相應的shape](https://upload-images.jianshu.io/upload_images/13539817-80618a53baa2bd01.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- mask與條件切片
條件切片會傳回一個bool數組，也可以搭配[numpy.flatnonzero](https://docs.scipy.org/doc/numpy/reference/generated/numpy.flatnonzero.html#numpy-flatnonzero)及[numpy.where](https://docs.scipy.org/doc/numpy/reference/generated/numpy.where.html#numpy-where)索引指定條件的切片。
*什麼是掩碼數組？*
[mask](https://docs.scipy.org/doc/numpy/reference/maskedarray.html)
在許多情況下，數據集可能不完整或因無效數據的存在而受到污染。例如，傳感器可能無法記錄數據或記錄無效值。該`numpy.ma`模塊通過引入掩碼數組提供了一種解決此問題的便捷方法。  
![條件索引與mask](https://upload-images.jianshu.io/upload_images/13539817-dbd1f2b005778213.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![條件索引](https://upload-images.jianshu.io/upload_images/13539817-cb96fedbe39fe4b1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![條件索引](https://upload-images.jianshu.io/upload_images/13539817-e265e7834293df38.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     
- 查找NAN值
np.nan需要使用[numpy.isnan](https://docs.scipy.org/doc/numpy/reference/generated/numpy.isnan.html#numpy-isnan)查詢。
![查找nan值](https://upload-images.jianshu.io/upload_images/13539817-5fbbf995b877a64a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![修改nan值](https://upload-images.jianshu.io/upload_images/13539817-83d6c71826856d5a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### 重塑 #####
1) [np.reshape()](https://docs.scipy.org/doc/numpy/reference/generated/numpy.reshape.html)  
![](https://upload-images.jianshu.io/upload_images/13539817-56e7fce114e5f29d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2) [np.ndarray.flatten](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ndarray.flatten.html)(order='C')
order：'C'  按行，'F'  按列，'A'  原順序展開成一維。  
![](https://upload-images.jianshu.io/upload_images/13539817-64cc0c6ac076183e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
3) [np.transpose](https://docs.scipy.org/doc/numpy/reference/generated/numpy.transpose.html)(arr, axes)
與reshape不同，依照原本維度改變形狀。  
arr：要轉置的數組
axes：整數的列表，對應維度，默認所有維度都會翻轉。
![](https://upload-images.jianshu.io/upload_images/13539817-b8f101b8e9071070.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![](https://upload-images.jianshu.io/upload_images/13539817-1f4c03e978d6d0c5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
4) [numpy.matrix](https://docs.scipy.org/doc/numpy/reference/generated/numpy.matrix.html)
5) [numpy.asarray](https://docs.scipy.org/doc/numpy/reference/generated/numpy.asarray.html#numpy-asarray)


##### 轉置(翻轉) #####
1) [np.transpose](https://docs.scipy.org/doc/numpy/reference/generated/numpy.transpose.html)(arr, axes)
arr：要轉置的數組
axes：整數的列表，對應維度，默認所有維度都會翻轉。  
![](https://upload-images.jianshu.io/upload_images/13539817-9a0a7a3b1f5ddcff.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2) ndarray.T  
![](https://upload-images.jianshu.io/upload_images/13539817-28c4f743cf59ec5b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### 組合與分割 #####
- **串接**:多維數組連接的過程中要注意連接軸的大小相同。
1) [np.concatenate()](https://docs.scipy.org/doc/numpy/reference/generated/numpy.concatenate.html)  
- 一維  
![](https://upload-images.jianshu.io/upload_images/13539817-98170f2886326021.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 二維  
![](https://upload-images.jianshu.io/upload_images/13539817-4fbd3004026b416f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2) [np.row_stack](https://docs.scipy.org/doc/numpy/reference/generated/numpy.ma.row_stack.html) 與 [np.column_stack](https://docs.scipy.org/doc/numpy/reference/generated/numpy.column_stack.html)  
![](https://upload-images.jianshu.io/upload_images/13539817-e6b4383a241a8568.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3) [np.hstack](https://docs.scipy.org/doc/numpy/reference/generated/numpy.hstack.html) 與 [np.vstack](https://docs.scipy.org/doc/numpy/reference/generated/numpy.vstack.html)  
![](https://upload-images.jianshu.io/upload_images/13539817-9c0e013500acbc2f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- **分割**
1) [numpy.split](https://docs.scipy.org/doc/numpy/reference/generated/numpy.split.html)(ary, indices_or_sections, axis)
ary：被分割的輸入數組
indices_or_sections：此參數為整數，表示要分割為幾分等大小數組。此參數為一維數組，則表示要分割的位置。
axis：默認為 0  
![1](https://upload-images.jianshu.io/upload_images/13539817-3ee8891acc13e1a8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![2](https://upload-images.jianshu.io/upload_images/13539817-60a0b9fae690a5aa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### 重複 #####
- 重複
[numpy.tile](https://docs.scipy.org/doc/numpy/reference/generated/numpy.tile.html#numpy-tile)
[numpy.repeat](https://docs.scipy.org/doc/numpy/reference/generated/numpy.repeat.html#numpy-repeat)
![沿著axis重複[第一個值重複的次數,第二個值重複的次數]](https://upload-images.jianshu.io/upload_images/13539817-a7e03fd08b1966f7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![由內而外(第三層重複的次數,第二層重複的次數,第一層重複的次數)](https://upload-images.jianshu.io/upload_images/13539817-49441c5ce729552b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### 添加和插入和刪除 #####
- **添加**
1) [np.append](https://docs.scipy.org/doc/numpy-1.13.0/reference/generated/numpy.append.html)(arr, values, axis)
添加數組中某個位置或某軸的值
arr：輸入數組
values：要添加的值
axis：沿著它完成操作的軸。如果未提供，則輸入數組會被展開   
![](https://upload-images.jianshu.io/upload_images/13539817-5a0666f4e91c9b93.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- **插入**
插入數組中某個位置或某軸的值
1) [numpy.insert](https://docs.scipy.org/doc/numpy/reference/generated/numpy.insert.html)(arr, obj, values, axis)
arr：輸入數組
obj：在其之前插入值的索引
values：要插入的值
axis：沿著它插入的軸，如果未提供，則輸入數組會被展開   
![](https://upload-images.jianshu.io/upload_images/13539817-f4895bf6fa9908cb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- **刪除**
1) [Numpy.delete](https://docs.scipy.org/doc/numpy/reference/generated/numpy.delete.html)(arr, obj, axis)
刪除數組中某個位置或某軸的值
arr：輸入數組
obj：可以使用切片，整數或者整數數組，表示要從輸入數組刪除的子數組
axis：沿著它刪除給定子數組的軸，如果未提供，則輸入數組會被展開    
![](https://upload-images.jianshu.io/upload_images/13539817-314bbc5cf7aee415.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2) [numpy.unique](https://docs.scipy.org/doc/numpy/reference/generated/numpy.unique.html)(arr, return_index, return_inverse, return_counts)
結果為刪除**重複(重覆)**數組，並排列。
arr：輸入數組，如果不是一維數組則會展開
return_index：如果為true，返回結果(新數組)以及結果對應原數組的原數組索引
return_inverse：如果為true，返回結果以及結果的新數組對應原數組的新數組索引
return_counts：如果為true，返回結果以及結果的重複次數  
![](https://upload-images.jianshu.io/upload_images/13539817-76703c6c4d3fbc6e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### 網格 #####
1) [np.meshgrid()](https://docs.scipy.org/doc/numpy/reference/generated/numpy.meshgrid.html)
通常使用在數據的矢量化上。它適用於生成網格型數據，可以接受兩個一維數組生成兩個二維矩陣，對應兩個數組中所有的(x,y)對。
2) [np.mgrid()](https://docs.scipy.org/doc/numpy/reference/generated/numpy.mgrid.html)
與meshgrid類似，但可以處理多維。

$f(x,y)=3x^2+5y+16,(1≤x≤3),(4≤y≤6)$
$f(a,b)=3a^2+5b+16,(1≤a≤3),(4≤b≤6)$  
- meshgrid  
![1](https://upload-images.jianshu.io/upload_images/13539817-d47d7a0bf09eb4c6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![2](https://upload-images.jianshu.io/upload_images/13539817-a856053c6a13a79f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![z=x+y](https://upload-images.jianshu.io/upload_images/13539817-35ec0a93b6f83ba1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- mgrid  
![1](https://upload-images.jianshu.io/upload_images/13539817-d64d1874c46f2373.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![2](https://upload-images.jianshu.io/upload_images/13539817-bd6b1c48438931f2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![3](https://upload-images.jianshu.io/upload_images/13539817-1b7f365cb84b18de.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


##### 排序 #####
NumPy中提供了各種排序相關功能。這些排序函數實現不同的排序算法，每個排序算法的特徵在於執行速度，最壞情況性能，所需的工作空間和算法的穩定性。下表顯示了三種排序算法的比較。
| 種類                    | 速度 | 最壞情況    | 工作空間 | 穩定性 |
| ----------------------- | ---- | ----------- | -------- | ------ |
| 'quicksort'（[快速排序](http://alrightchiu.github.io/SecondRound/comparison-sort-quick-sortkuai-su-pai-xu-fa.html)） | 1    | O(n^2)      | 0        | 否     |
| 'mergesort'（[歸併排序](http://alrightchiu.github.io/SecondRound/comparison-sort-merge-sorthe-bing-pai-xu-fa.html)(混排)）  | 2    | O(n*log(n)) | ~n/2     | 是     |
| 'heapsort'（[堆排序](http://alrightchiu.github.io/SecondRound/comparison-sort-heap-sortdui-ji-pai-xu-fa.html)）    | 3    | O(n*log(n)) | 0        | 否     |

1) [numpy.sort](https://docs.scipy.org/doc/numpy/reference/generated/numpy.sort.html)(a, axis, kind, order)
將數組進行排序，返回排序好的數組
a:要排序的陣列
axis:沿著它排序陣列的軸，如果沒有陣列會被展開，沿著最後的軸排序
kind:默認為'quicksort'（快速排序）
order:如果陣列dtype包含'names'，則是要排序dtype的'names'   
![1](https://upload-images.jianshu.io/upload_images/13539817-592fa998f08d9a36.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![2](https://upload-images.jianshu.io/upload_images/13539817-2781e57599792c2b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2) [numpy.argsort](https://docs.scipy.org/doc/numpy/reference/generated/numpy.argsort.html)(a, axis, kind, order)
將數組進行排序，返回排序好結果對應原數組的原數組索引
a:要排序的陣列
axis:沿著它排序陣列的軸，如果沒有陣列會被展開，沿著最後的軸排序
kind:默認為'quicksort'（快速排序）
order:如果陣列dtype包含'names'，則是要排序dtype的'names'    
![1](https://upload-images.jianshu.io/upload_images/13539817-92c26ff4b9ffdbbf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  ![2](https://upload-images.jianshu.io/upload_images/13539817-1f0398a245b2596f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3) [numpy.partition()](https://docs.scipy.org/doc/numpy/reference/generated/numpy.partition.html)  
選定一個pivot只進行一次的快速排序，以pivot進行分區。輸入pivot為排序後的第幾個數，傳回分區好的數組。   
![](https://upload-images.jianshu.io/upload_images/13539817-32e12eeea18c6b7b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

4) [numpy.argpartition()](https://docs.scipy.org/doc/numpy/reference/generated/numpy.argpartition.html)  
選定一個pivot只進行一次的快速排序，以pivot進行分區。輸入pivot為排序後的第幾個數，傳回分區好的結果對應原數組的原數組索引。 
![](https://upload-images.jianshu.io/upload_images/13539817-69dde5d86e6e75c7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

5) [numpy.searchsorted](https://docs.scipy.org/doc/numpy/reference/generated/numpy.searchsorted.html)(a, v, side='left', sorter=None)
a：所需排序的數組
v：待查詢索引的元素值
side：查詢索引時的方向，其中：′left′為從左至右；′right′為從右至左
sorter：一個字符串或列表，可以設置按照某個屬性進行排序   
![](https://upload-images.jianshu.io/upload_images/13539817-193fd8fbfeac534f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)                                                **另類用法:將數值分組**    
利用searchsorted特性可以用來分組以及計數
![](https://upload-images.jianshu.io/upload_images/13539817-718c6892803a4341.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 計數 ###
- **計數**
1) 一般我們常用使用Python內建[collections.Counter](https://docs.python.org/2/library/collections.html#collections.Counter)   
![](https://upload-images.jianshu.io/upload_images/13539817-72f844ca2760332a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2) [np.count_nonzero](https://docs.scipy.org/doc/numpy/reference/generated/numpy.count_nonzero.html)  
![](https://upload-images.jianshu.io/upload_images/13539817-c4ac63e74356ebc4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3) [np.add.at()](https://docs.scipy.org/doc/numpy-1.15.0/reference/generated/numpy.ufunc.at.html)  
![](https://upload-images.jianshu.io/upload_images/13539817-8859139bf71e72d5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

