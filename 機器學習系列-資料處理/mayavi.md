參考:
[matplotlib](https://www.jianshu.com/p/adb3bdcfd887)
[mayavi文檔](https://docs.enthought.com/mayavi/mayavi/index.html)
[tvtk文檔](http://docs.enthought.com/mayavi/tvtk/index.html#)
[北京大學MOOC](http://www.icourse163.org/learn/BIT-1001871001?from=study#/learn/announce)
## 安裝 ##
[官方文檔](https://docs.enthought.com/mayavi/mayavi/installation.html)
建議使用Anaconda進行安裝較為方便，版本:python3.6，Mayavi：`conda install -c viscid-hub mayavi`，若要使用ivtk需要使用python2.7版本。

## TVTK ##
#### TVTK 基礎 ####
##### 查詢、導入 #####
- 文檔查詢工具
```python
from tvtk.tools import tvtk_doc
tvtk_doc.main()
```
![](https://upload-images.jianshu.io/upload_images/13539817-1a6b31e11ce76792.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 導入
```python
from tvtk.api import tvtk
from tvtk.tools import ivtk
from pyface.api import GUI
```
##### tvtk.CubeSource #####
- 屬性    
![屬性](https://upload-images.jianshu.io/upload_images/13539817-28914ed3ecfeb157.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 查看屬性      
![查看屬性](https://upload-images.jianshu.io/upload_images/13539817-f8cca91f41175b00.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 對象方法
其他請查詢官方文檔或文檔查詢工具       
![對象方法](https://upload-images.jianshu.io/upload_images/13539817-5f6508eda28366d4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### TVTK基本對象 #####
其他請查詢官方文檔或文檔查詢工具       
![TVTK基本對象](https://upload-images.jianshu.io/upload_images/13539817-0f5b60e87d14e9a3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### 顯示對象 ######
![顯示對象](https://upload-images.jianshu.io/upload_images/13539817-75654bfd7b0807ce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


## mayavi ##
[MLab參考](https://docs.enthought.com/mayavi/mayavi/auto/mlab_reference.html)
[其他MLab參考](http://docs.enthought.com/mayavi/mayavi/auto/mlab_pipeline_other_functions.html?highlight=pipeline%20image_plane_widget#)
[Mayavi API參考](https://docs.enthought.com/mayavi/mayavi/api/index.html)
- 層級      
![](https://upload-images.jianshu.io/upload_images/13539817-0afaf00c25aa5793.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 打開mayavi2  
也可以從此介面打開文檔查詢工具。         
![](https://upload-images.jianshu.io/upload_images/13539817-c503a3504de800e2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![文檔](https://upload-images.jianshu.io/upload_images/13539817-756f00fe411e9ff5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    
- 由程式顯示圖像時開啟      
![](https://upload-images.jianshu.io/upload_images/13539817-65ffefa6b782ae95.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- mayavi2操作錄製
此功能可以錄製你所有在mayavi2操作並轉成python，可以寫到python執行，可以使用`mlab.get_engine()`取得engine，取得後設置給engine變量可以省略腳本前面的第一段。     
 ![](https://upload-images.jianshu.io/upload_images/13539817-14b34b26a95101c5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)      ![將Surface設為透明，並且將視角拉近](https://upload-images.jianshu.io/upload_images/13539817-9223844a2ae83b63.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 範例
gist: https://gist.github.com/jounjieli/d4e534190e3da77f4f7c0fce6acf1982)
