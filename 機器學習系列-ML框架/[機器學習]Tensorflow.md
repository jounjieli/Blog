Tensorflow官網：https://www.tensorflow.org/
![](https://upload-images.jianshu.io/upload_images/13539817-ded96f0824389b95.gif?imageMogr2/auto-orient/strip)

## tensorflow基本概念 ##
1. Scalar(標量)表示值(單一數字)
2. vector(向量)表示位置(1維數組)
3. Tensor(張量)表示空間(多維數組)

- 5個重要的類(Class)
`Variable`，[tf.Variable](https://www.tensorflow.org/api_docs/python/tf/Variable)
`Tensor`，[tf.Tensor](https://www.tensorflow.org/api_docs/python/tf/Tensor)
`Session`，[tf.Session](https://www.tensorflow.org/api_docs/python/tf/Session)
`Graph`，[tf.Graph](https://www.tensorflow.org/api_docs/python/tf/Graph)
`Operation`，[tf.Operation](https://www.tensorflow.org/api_docs/python/tf/Operation)

- 常用函數
`tf.Variable`傳回一個Variable實例。
`tf.constant`傳回一個constant的Tensor實例。
`tf.placeholder`一個尚未存在(佔位)的Tensor實例。

### Graph ###
TensorFlow的運算，被表示為一個data flow Graph ，data flow Graph 中的節點(Nodes)被用來表示數學運算，而邊(Edges)則用來表示在節點之間的相互聯繫，是一種對數學運算過程的可視化方法。

### Session ###
而Session就是負責讓這個圖運算起來，Session持有並管理TensorFlow程序運行時的所有資源。

### Variable、Tensor ###
1. 在運行Variable之前，需要初始化Variable。在定義Variable時提供初始值，但必須調用其  初始化函數才能在Session 中實際分配此值，然後使用Variable。

2. 因為Tensor、Variable都是class無法直接像Python變量那樣操作更新賦值的，運算都是在Session中運行的，而賦值需要使用tf.assign函數，tf.assign函數只能對Variable賦值，tf.assign更新後的值不能改變原本Variable的shape跟dtype。

3. Variable是會顯示分配內存空間（既可以是內存，也可以是顯存），由Session管理，可以進行存儲、讀取、更改(tf.assign)等操作。Tensor，是記錄在Graph中，所以沒有單獨的內存空間；而由Variable、Tensor運算得來的值則是只會在程序運行中間出現，除非你將它賦值給python變量或賦值給Variable然後保存模型，通常Variable使用於weight、bias等需要更新的參數。

### 基本操作 ###
[tf.Variable](https://www.tensorflow.org/api_docs/python/tf/Variable)
[tf.constant](https://www.tensorflow.org/api_docs/python/tf/constant)
[tf.placeholder](https://www.tensorflow.org/api_docs/python/tf/placeholder)
[tf.initializers.variables](https://www.tensorflow.org/api_docs/python/tf/initializers/variables)
[tf.global_variables](https://www.tensorflow.org/api_docs/python/tf/global_variables)
[tf.Session](https://www.tensorflow.org/api_docs/python/tf/Session)
[tf.math.add](https://www.tensorflow.org/api_docs/python/tf/math/add)
[tf.assign](https://www.tensorflow.org/api_docs/python/tf/assign)

![](https://upload-images.jianshu.io/upload_images/13539817-4253b95feaf850be.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![](https://upload-images.jianshu.io/upload_images/13539817-3e33172cce26bd2f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![](https://upload-images.jianshu.io/upload_images/13539817-1dffff81fe661217.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 線性回歸 ###
當tensorflow溢位時會得到nan導致訓練失敗，所以使用sklearn將data先進行zero mean normalization。
[tf.train.GradientDescentOptimizer](https://www.tensorflow.org/api_docs/python/tf/train/GradientDescentOptimizer)
[sklearn.preprocessing](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.preprocessing)     
![](https://upload-images.jianshu.io/upload_images/13539817-a1e81695ff8d20b9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![](https://upload-images.jianshu.io/upload_images/13539817-52b26642b6cede62.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![](https://upload-images.jianshu.io/upload_images/13539817-afa32bb99837c3ce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![](https://upload-images.jianshu.io/upload_images/13539817-62c869b50412e0ac.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### deep非線性回歸 ###
這邊建立了4層的neural network，輸入(輸出)層1個NN，中間層12個NN，這邊可以看出當DNN越複雜可以擬合越複雜的函數(當然也越容易過擬合overfitting)，訓練時間也越長。    
![](https://upload-images.jianshu.io/upload_images/13539817-7bdb3fa44e250649.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![](https://upload-images.jianshu.io/upload_images/13539817-dcef5289b18dc2a0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![](https://upload-images.jianshu.io/upload_images/13539817-7a0e19488fc1b9ff.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![](https://upload-images.jianshu.io/upload_images/13539817-fd922ee6621c1319.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     

### 尋找model最小值(或最大值) ###
找最大值將model乘上一個負號即可，此篇模型接續上一段deep非線性回歸，因為這是一個非凸函數，所以選取一個範圍隨機取feature，把最低點記錄下來。    
![](https://upload-images.jianshu.io/upload_images/13539817-926743d4dd051dcf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![](https://upload-images.jianshu.io/upload_images/13539817-21f2b6381d7df9eb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![](https://upload-images.jianshu.io/upload_images/13539817-0b95a69d79cddc03.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![這邊-2~2過擬合了，需要dropout或regularization](https://upload-images.jianshu.io/upload_images/13539817-427a6601d788b470.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### deep分類 ###
Gist:
https://gist.github.com/jounjieli/95818266b18ecfa46dddb9ece0c068e3

### CNN ###
Gist:
https://gist.github.com/jounjieli/7d31a6ddd50a1a03605534326e294e86

### tensorboard ###
- 架構摘要
呼叫指令:路徑輸入FileWriter指定的路徑。   
![](https://upload-images.jianshu.io/upload_images/13539817-2449789454e170b8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)       
[tf.summary.FileWriter](https://www.tensorflow.org/api_docs/python/tf/summary/FileWriter)
![](https://upload-images.jianshu.io/upload_images/13539817-54d469bb5fc8a68b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
以CNN代碼為例我們呼叫tensorboard 可以得到此架構圖。
![](https://upload-images.jianshu.io/upload_images/13539817-73eec4ed8c0222a7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 數據摘要
可以參考此篇:
https://ithelp.ithome.com.tw/articles/10187814
