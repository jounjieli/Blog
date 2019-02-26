基本上Scikit-Learn的使用非常簡單，比較像是工具包，大多是需要了解原理直接調用不同函數，這篇做一些基本的介紹，大致熟悉一下，使用時直接查詢**[手冊目錄](https://scikit-learn.org/stable/user_guide.html)**的介紹與範例即可。

 # Scikit-Learn #
[**Scikit-Learn官網**](http://scikit-learn.org/stable/)
[**Scikit-Learn英文文檔**](https://scikit-learn.org/stable/documentation.html#documentation-of-scikit-learn-version)
[**Scikit-Learn中文文檔**](http://sklearn.apachecn.org/)

## 選擇正確的評估器(Choosing the right estimator)
[Flow Chart](https://scikit-learn.org/stable/tutorial/machine_learning_map/index.html)
![](https://upload-images.jianshu.io/upload_images/13539817-dee1ae39d2a43eac.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 加載數據集 ##
數據集可以從外存讀取後做資料前處理，Scikit-Learn本身也提供一些整理好的數據集可以下載，以及提供一些數據生成器可以用來用來生成數據，匯入模組`import sklearn.datasets`，詳細數據格式及加載說明請參考[API](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.datasets)、[文檔](https://scikit-learn.org/stable/datasets/index.html#dataset-loading-utilities)。

## 線性回歸 ##
[Ordinary Least Squares](https://gist.github.com/jounjieli/a59b6185461ce2fe07e4c024583d46ba)
OLS(普通最小二乘)線性回歸中有2種求解法，一種是`直接法`，求解涉及到矩陣的求逆，當特徵矩陣數據量過大，求逆是一個很耗時的過程，我們可以使用先對特徵矩陣做奇異值分解(SVD)後再求廣義逆，但通常是使用另一種`梯度下降法`繞過求逆的過程。
OLS算法使用的前提是必須滿足數據集無多重共線性，因為它是無偏估計，這也使它非常懼怕多重共線性問題，會使矩陣近似於奇異矩陣，使得它往往得到的權重參數Variance大而造成overfitting現象，是一個不穩定的回歸算法，可以使用regularization或Dimension Reduction等等方法來解決。

## z score normalization ##
[Preprocessing data](https://scikit-learn.org/stable/modules/preprocessing.html)
[StandardScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html#sklearn-preprocessing-standardscaler)

![](https://upload-images.jianshu.io/upload_images/13539817-2823edae4396cef8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](https://upload-images.jianshu.io/upload_images/13539817-6415270c760c2bff.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## Confusion matrix ##
[confusion_matrix](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html#sklearn-metrics-confusion-matrix)
[Confusion matrix](https://scikit-learn.org/stable/auto_examples/model_selection/plot_confusion_matrix.html#confusion-matrix)
