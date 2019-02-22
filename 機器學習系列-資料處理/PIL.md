[英文手冊](https://pillow.readthedocs.io)
[中文手冊](https://pillow-zh-cn.readthedocs.io/zh_CN/latest/index.html)

## 基本概念 ##
Python Imaging Library可以處理光柵圖像，也就是矩形的像素。

- 頻段
一個圖片允許包含一個或多個頻段。 Python Imaging Library允許你在單個圖像中存儲多個頻段。包括原圖像的尺寸和大小。舉個例子，一個PNG圖片可能包含'R'，'G'，'B'，和'A'頻段來表示紅，綠，藍和alpha透明值。有許多對應頻段的操作。例如：直方圖。它常常用來處理不同像素的每個頻段的值。

要想獲得圖像的頻段的數量和名稱，使用getbands（）方法。

- 模式
圖像的 mode 定義了這個圖像每一個像素點的大小. 目前版本支持以下標準模式：

| 1     | 1-bit的像素點   | 黑白,一個1bit的像素點還是佔用一個byte                        |
| ----- | --------------- | ------------------------------------------------------------ |
| L     | 8-bit的像素點   | 黑白                                                         |
| P     | 8-bit的像素點   | 使用調色板來映射其他模式                                     |
| RGB   | 3x8-bit的像素點 | 真彩                                                         |
| RGBA  | 4x8-bit的像素點 | 帶有透明標記的真彩                                           |
| CMYK  | 4x8-bit的像素點 | 分色                                                         |
| YCbCr | 3x8-bit的像素點 | 圖像視頻格式,值得注意的是這個屬於JPEG,而並不是ITU-RBT.2020, standard |
| LAB   | 3x8-bit的像素點 | L*a*b色彩空間                                                |
| HSV   | 3x8-bit的像素點 | Hue,Saturation,Value色彩空間                                 |
| I     | 32-bit的像素點  | 有符號整數像素                                               |
| F     | 32-bit的像素點  | 浮點像素                                                     |

PIL 同樣支持一些不常用的模式, 包括LA (L with alpha), RGBX (true color with padding) and RGBa (true color with premultiplied alpha). 然而, PIL 不支持用戶自定義模式; 如果你需要使用上述沒有提到的模式, 則需要使用圖像對象序列.
你可以通過 mode 屬性獲取圖像的模式. 這是一個字符串類型的值.

- 尺寸
你可以通過size屬性讀取到圖像的大小。這是一個由兩個元素組成的元組，其中第一個元素代表長，第二個則代表寬，單位是像素。

- 坐標系
Python Imaging Library使用笛卡爾坐標系，使用（0,0）表示左上角。值得注意的是，坐標點表示的是一個像素的左上角，而表示像素的中央則是（0.5,0.5）。

坐標系通常使用含有兩個元素的元組進行交互。表示矩形則使用以左上角的坐標打頭的包含四個元素的元組，例如，一個800x600像素可以表示為（0,0,800,600）。

- 調色板
（P）模式使用調色板來為每一個像素指定實際的顏色。

- 摘要
你可以通過info屬性來獲取圖片的摘要信息。這是一個字典對象。
在讀取和寫入圖像文件的時候涉及到的信息取決於文件模式。大多讀取的時候會獲得info屬性，但是在保存的時候不會獲得。

- 過濾
當你需要對圖像進行幾何操作的時候，Python Imaging Library提供了一些不同的濾鏡。
`NEAREST`
從輸入圖像中選擇最近的像素。忽略所有其他輸入像素。
`BILINEAR`
對於調整大小，使用可能有助於輸出值的所有像素上的線性插值來計算輸出像素值。對於其他變換，使用輸入圖像中2x2環境的線性插值。
`BICUBIC`
對於調整大小，使用可能有助於輸出值的所有像素上的三次插值來計算輸出像素值。對於其他變換，使用輸入圖像中的4×4環境的三次插值。
`LANCZOS`
使用可能有助於輸出值的所有像素上的高質量Lanczos濾波器（截斷的sinc）計算輸出像素值。在當前版本的PIL中，此過濾器只能與調整大小和縮略圖方法一起使用。

## 載入模塊 ##
`from PIL import Image`

## 圖片讀寫 ##
### matplotlib(圖片內聯 jupyter 方便) ###
matplotlib.imshow()也可以直接讀取PIL.Image.Image物件，也可以讀取不同mode圖片陣列，`imshow`顯示灰階圖時，若顯示不正常`matplotlib.pyplot.imshow`的`cmap`參數需設為`'gray' `。
[matplotlib](https://www.jianshu.com/p/adb3bdcfd887)
[matplotlib.pyplot.imread](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.imread.html)
[matplotlib.pyplot.imshow](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.imshow.html#matplotlib.pyplot.imshow)
![](https://upload-images.jianshu.io/upload_images/13539817-81aeed30a1b8274b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![](https://upload-images.jianshu.io/upload_images/13539817-10d91bc51c1a63ca.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### PIL ###
[Image.open](https://pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.open)
`format`這個屬性代表圖片文件的擴展名，如果圖片文件打開失敗，則其值為無。 `size`這個屬性代表圖片的大小，以像素為單位，使用包含兩個元素的元組來返回。`info`以字典形式返回示例的信息。 `mode`這個屬性代表圖片的band屬性，一般情況（黑白）下為“L”，當圖片是彩色的時候是“RGB”，如果圖片經過壓縮，則是“CMYK”。
![](https://upload-images.jianshu.io/upload_images/13539817-138b8641a7e9a53c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
[Image.getdata](https://pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.Image.getdata)
[numpy.asarray](https://docs.scipy.org/doc/numpy/reference/generated/numpy.asarray.html)
[Image.fromarray](https://pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.fromarray)
[Image.save](https://pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.Image.save)
![](https://upload-images.jianshu.io/upload_images/13539817-d757d7eaad8ce283.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![切片索引只有2通道，不符合彩色模式fromarray將會轉換成黑白](https://upload-images.jianshu.io/upload_images/13539817-6ab096037729e033.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![索引RGB通道捨，棄透明度通道，然後R、G通道設為zero](https://upload-images.jianshu.io/upload_images/13539817-e51d65c771261296.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![存檔](https://upload-images.jianshu.io/upload_images/13539817-97bef4359d8c70bb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## PIL與matplotlib合用 ##
![](https://upload-images.jianshu.io/upload_images/13539817-ac8d635456cc4945.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 圖片裁剪 ##
[Image.crop](https://pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.Image.crop)
![](https://upload-images.jianshu.io/upload_images/13539817-962b46e25ad76b50.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![](https://upload-images.jianshu.io/upload_images/13539817-0e4ceb26a41b0810.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 圖片黏貼 ##
[Image.paste](https://pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.Image.paste)
![](https://upload-images.jianshu.io/upload_images/13539817-6330390ef8e02a94.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 圖片縮放 ##
[Image.thumbnail](https://pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.Image.thumbnail)     
[Image.resize](https://pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.Image.resize)
![](https://upload-images.jianshu.io/upload_images/13539817-c1fe40ed8abc1f23.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![](https://upload-images.jianshu.io/upload_images/13539817-3ea20647249bb4a3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 分割與合併波段 ##
Python Imaging Library 同樣允許你操作多波段的圖片, 比如RGB圖片. split 方法會創建一個圖片集合, 每一個表示了這個圖片的一個波段. merge 方法需要傳入一個mode參數和一個圖片的元組, 然後融合這個圖像.
[Image.split](https://pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.Image.split)
[Image.merge](https://pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.merge)    
![](https://upload-images.jianshu.io/upload_images/13539817-e7c3ae36c8cfbab2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 旋轉 ##
[Image.rotate](https://pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.Image.rotate)
[Image.transpose](https://pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.Image.transpose)
![](https://upload-images.jianshu.io/upload_images/13539817-248070be48f83cb9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240) ![](https://upload-images.jianshu.io/upload_images/13539817-86ff91cf87172961.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![](https://upload-images.jianshu.io/upload_images/13539817-936c86795d743a43.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 模式轉換 ##
[Image.convert](https://pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.Image.convert)
![](https://upload-images.jianshu.io/upload_images/13539817-8189b56f09ceaa34.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![](https://upload-images.jianshu.io/upload_images/13539817-60efa1336409f684.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 圖像效果 ##
濾鏡：[ImageFilter](https://pillow.readthedocs.io/en/stable/reference/ImageFilter.html)
![](https://upload-images.jianshu.io/upload_images/13539817-1aee07b4b570d6e8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    
效果增強：[ImageEnhance](https://pillow.readthedocs.io/en/stable/reference/ImageEnhance.html)
![](https://upload-images.jianshu.io/upload_images/13539817-d18637e1d6f2c149.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   ![](https://upload-images.jianshu.io/upload_images/13539817-41c7df09a2402395.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 指定幀 ##
[Image.seek](https://pillow.readthedocs.io/en/stable/reference/Image.html#PIL.Image.Image.seek)
