---
[官網範例](https://matplotlib.org/gallery/index.html)
### 圖的概念 ###
![圖的概念](https://upload-images.jianshu.io/upload_images/13539817-0923382df220fd19.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 匯入模組 ###   
![匯入模組](https://upload-images.jianshu.io/upload_images/13539817-f90dbd0c387b1355.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 圖表顯示操作 ###
- 使用腳本:
若在腳本中運行matplotlib的話顯示繪圖需要使用`plt.show()`，若顯示繪圖後變更繪圖而繪圖沒有更新則使用`plt.draw()`。
- 使用Ipython notebook:
使用Ipython notebook`不需要使用plt.show()`繪圖運行時會自動顯示，若顯示繪圖後變更繪圖而繪圖沒有更新則使用`plt.draw()`，可以使用`%matplotlib notebook`使用交互模式(3D圖可以旋轉等功能)，使用`%matplotlib inline`則使用靜態模式(靜態圖形)。

### Latex功能 ###
[Latex](https://matplotlib.org/users/usetex.html)
matplotlib在字串中支持Latex功能，較複雜的LaTeX 需使用 LaTeX 渲染，`需要安裝 LaTeX 和 Ghostscript`，否則一直會報錯：FileNotFoundError: [WinError 2] 系統找不到指定的文件，若Latex式子不複雜有時可以不開啟LaTeX渲染。
[proTeXt - 基於MiKTeX的Windows發行版](https://www.tug.org/protext/)
[Ghostscript ](https://www.ghostscript.com/)
- 打開Latex功能      
![](https://upload-images.jianshu.io/upload_images/13539817-2f385a1f6d90d0d9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- path設置    
![](https://upload-images.jianshu.io/upload_images/13539817-f88b686e6dbd5607.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 若安裝完成也設置好path報錯:     
嘗試刪除您的`.matplotlib/tex.cache`目錄。如果您不知道在哪裡找到`.matplotlib`，請參閱[matplotlib配置和緩存目錄位置](https://matplotlib.org/faq/troubleshooting_faq.html#locating-matplotlib-config-dir)
- 範例:         
![Latex顯示對數分布函數](https://upload-images.jianshu.io/upload_images/13539817-70463dbb46c5c652.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![範例](https://upload-images.jianshu.io/upload_images/13539817-84a75c7feeb66e8a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 顯示中文 ###
matplotlib無法正常顯示中文需要在使用到中文的圖表前修改matlinplot字型設定，輸出圖表後在修改回來，修改後不可與特殊符號混用（中文不支持一些特殊符號），腳本在`plt.show()`前修改，若是在Ipython notebook或同視窗執行，則一次只能套用一種設定。
```python
plt.rcParams['font.sans-serif'] = ['SimHei']  # 用來正常顯示中文標籤(修改默認字型)
plt.rcParams['axes.unicode_minus'] = False   # 用來正常顯示負號(修改設定)
plt.rcParams['font.sans-serif'] = ['DejaVu Sans']  # 用來正常顯示中文標籤(回復默認字型)
plt.rcParams['axes.unicode_minus'] = True  # 用來正常顯示負號(回復默認設定)
#在參數加fontproperties='SimHei'，不用回復默認字型
set_ylabel("$L(\mu,\Sigma)$對$\mu$",fontproperties='SimHei')
```       
![範例](https://upload-images.jianshu.io/upload_images/13539817-8ae8a88154b2e555.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![範例](https://upload-images.jianshu.io/upload_images/13539817-b25f5922ca39e435.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 圖與子圖控制 ###
當子圖有指定變數時(例如a=subplot(111))，pyplot.xxx方法大多可以呼叫a.set_xxx或a.xxx方法，細部設定建議使用此方法。
[詳細參數請參考官方API文檔](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.html#module-matplotlib.pyplot)
[**matplotlib.pyplot.figure**](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.figure.html#matplotlib.pyplot.figure)
[**matplotlib.pyplot.subplot**](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.subplot.html#matplotlib.pyplot.subplot)
[**matplotlib.pyplot.axes**](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.axes.html#matplotlib.pyplot.axes)
[**matplotlib.gridspec.GridSpec**](https://matplotlib.org/api/_as_gen/matplotlib.gridspec.GridSpec.html)     
範例:
![參數(行、列、編號)，排列方式為:(由左至右，由上至下)](https://upload-images.jianshu.io/upload_images/13539817-d380b0534fc9d367.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![axes([x座標,y座標,圖長,圖寬])](https://upload-images.jianshu.io/upload_images/13539817-d5b0680d09bc657b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![GridSpec(行數,列數,hspace=高度間距,wspace=寬度間距)](https://upload-images.jianshu.io/upload_images/13539817-4f293e541f9101de.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)      ![GridSpec結果](https://upload-images.jianshu.io/upload_images/13539817-42c2711b180d9e47.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    

### 圖表讀寫 ###
[matplotlib.pyplot.savefig](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.savefig.html#matplotlib.pyplot.savefig)
[matplotlib.pyplot.imsave](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.imsave.html#matplotlib.pyplot.imsave)
[matplotlib.pyplot.imread](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.imread.html)
[matplotlib.pyplot.imshow](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.imshow.html#matplotlib.pyplot.imshow)

![例1](https://upload-images.jianshu.io/upload_images/13539817-122c5eca763dbf80.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![例2](https://upload-images.jianshu.io/upload_images/13539817-9737f4c61d646b4b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![結果1](https://upload-images.jianshu.io/upload_images/13539817-5836383d49985bd5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![結果2](https://upload-images.jianshu.io/upload_images/13539817-badc4060f60a6fb0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![](https://upload-images.jianshu.io/upload_images/13539817-0abf04405d1bb938.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 刻度控制 ###
主刻度(majorticks)、次刻度(minorticks)，標籤(xlabel,ylabel)，刻度值(xticks,yticks)，刻度範圍(xlim,ylim)、刻度參數(tick_params)。
- 開關次刻度
[matplotlib.pyplot.minorticks_on](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.minorticks_on.html#matplotlib.pyplot.minorticks_on)
[matplotlib.pyplot.minorticks_off](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.minorticks_off.html#matplotlib.pyplot.minorticks_off)
- 標籤設置
[matplotlib.pyplot.xlabel](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.xlabel.html#matplotlib.pyplot.xlabel)
[matplotlib.pyplot.ylabel](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.ylabel.html#matplotlib.pyplot.ylabel)
- 刻度值設置
[matplotlib.pyplot.xticks](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.xticks.html#matplotlib.pyplot.xticks)
[matplotlib.pyplot.yticks](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.yticks.html#matplotlib.pyplot.yticks)
- 刻度範圍設置
[matplotlib.pyplot.xlim](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.xlim.html#matplotlib.pyplot.xlim)
[matplotlib.pyplot.ylim](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.ylim.html#matplotlib.pyplot.ylim)
- 刻度參數設置
[matplotlib.pyplot.tick_params](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.tick_params.html#matplotlib.pyplot.tick_params)
- 隱藏刻度
隱藏刻度可以設置tick值為空(set_xticks([ ]),set_yticks([ ]))    
![範例](https://upload-images.jianshu.io/upload_images/13539817-ed9149dfa57ef0c1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)      ![結果](https://upload-images.jianshu.io/upload_images/13539817-669ca5c3e4bd1562.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 繪製刻度格線
[matplotlib.pyplot.grid](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.grid.html#matplotlib.pyplot.grid)
![範例](https://upload-images.jianshu.io/upload_images/13539817-eda40d60b254ab92.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 樣式設置 ###
- 註釋
[matplotlib.pyplot.annotate](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.annotate.html#matplotlib.pyplot.annotate)

![範例](https://upload-images.jianshu.io/upload_images/13539817-7e0eb6b2cbca0004.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 顏色刻度
[colorbar](https://matplotlib.org/api/colorbar_api.html)
[matplotlib.cm](https://matplotlib.org/api/cm_api.html)
[matplotlib.pyplot.colorbar](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.colorbar.html#matplotlib.pyplot.colorbar)
[cmap顏色參考](https://matplotlib.org/tutorials/colors/colormaps.html)
![範例](https://upload-images.jianshu.io/upload_images/13539817-bc3504c464981493.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 放置圖例
[matplotlib.pyplot.legend](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.legend.html#matplotlib.pyplot.legend)
圖例需搭配繪圖方法的label參數使用。
![範例](https://upload-images.jianshu.io/upload_images/13539817-1f4f882a9e7b4172.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)      ![結果](https://upload-images.jianshu.io/upload_images/13539817-7c515fc07a6b4a4f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 圖框與子圖樣式設定
[matplotlib.pyplot.figure](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.figure.html#matplotlib.pyplot.figure)
[matplotlib.pyplot.subplot](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.subplot.html#matplotlib.pyplot.subplot)
![範例](https://upload-images.jianshu.io/upload_images/13539817-26c20fa5604a9e3d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![結果](https://upload-images.jianshu.io/upload_images/13539817-986f6542109c147e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 樣式表
[matplotlib.style](https://matplotlib.org/api/style_api.html)
[樣式表](https://matplotlib.org/gallery/style_sheets/style_sheets_reference.html)
![plt.style.available列出可用樣式](https://upload-images.jianshu.io/upload_images/13539817-8340cd9fdb9923b8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![範例](https://upload-images.jianshu.io/upload_images/13539817-bc951d029c16633a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![結果](https://upload-images.jianshu.io/upload_images/13539817-ff06b59cb4501e4f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 2D圖 ###
- 文本
[matplotlib.pyplot.text](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.text.html#matplotlib.pyplot.text)
![範例](https://upload-images.jianshu.io/upload_images/13539817-6e4a90e6fd006889.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![範例](https://upload-images.jianshu.io/upload_images/13539817-2a6dc637ff52cf44.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 線型圖
[matplotlib.pyplot.plot](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.plot.html#matplotlib.pyplot.plot)
![範例](https://upload-images.jianshu.io/upload_images/13539817-681519829221dd72.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 散點圖
[matplotlib.pyplot.scatter](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.scatter.html#matplotlib.pyplot.scatter)
![例1](https://upload-images.jianshu.io/upload_images/13539817-bfb1b1fd9cafaf3f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![例1結果](https://upload-images.jianshu.io/upload_images/13539817-2540324ade1c4bed.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 柱狀圖
[matplotlib.pyplot.bar](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.bar.html#matplotlib.pyplot.bar)
![範例](https://upload-images.jianshu.io/upload_images/13539817-5bb6558c1c9e1846.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 餅狀圖
[matplotlib.pyplot.pie](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.pie.html#matplotlib.pyplot.pie)
![範例](https://upload-images.jianshu.io/upload_images/13539817-14a9060c049241fc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 誤差圖
[matplotlib.pyplot.errorbar](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.errorbar.html#matplotlib.pyplot.errorbar)
![範例](https://upload-images.jianshu.io/upload_images/13539817-46acf3e828065e2d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 直方圖
[matplotlib.pyplot.hist](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.hist.html#matplotlib.pyplot.hist)
![範例](https://upload-images.jianshu.io/upload_images/13539817-cc6479b987c062f8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 二維直方圖
[matplotlib.pyplot.hist2d](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.hist2d.html#matplotlib.pyplot.hist2d)
![範例](https://upload-images.jianshu.io/upload_images/13539817-811dc5cfc18b0094.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 二維六角直方圖
[matplotlib.pyplot.hexbin](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.hexbin.html#matplotlib.pyplot.hexbin)
![範例](https://upload-images.jianshu.io/upload_images/13539817-d852789443230d8b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 量場圖
[matplotlib.pyplot.quiver](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.quiver.html#matplotlib.pyplot.quiver)
[matplotlib.pyplot.quiverkey](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.quiverkey.html#matplotlib.pyplot.quiverkey)
![範例](https://upload-images.jianshu.io/upload_images/13539817-c1b603299b3cc3e7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 向量圖       
[matplotlib.pyplot.arrow](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.arrow.html#matplotlib.pyplot.arrow)
![範例](https://upload-images.jianshu.io/upload_images/13539817-dc31e2990cacfbe8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![範例](https://upload-images.jianshu.io/upload_images/13539817-5e9e83b728d5b108.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 等高線圖
[matplotlib.pyplot.contour](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.contour.html#matplotlib.pyplot.contour)
[matplotlib.pyplot.contourf](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.contourf.html#matplotlib.pyplot.contourf)
[matplotlib.pyplot.clabel](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.clabel.html#matplotlib.pyplot.clabel)
![範例](https://upload-images.jianshu.io/upload_images/13539817-0b18ac38913befca.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 圖片
[matplotlib.pyplot.imshow](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.imshow.html#matplotlib.pyplot.imshow)
[matplotlib.pyplot.imread](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.imread.html)
![範例](https://upload-images.jianshu.io/upload_images/13539817-3e0c2e0e7fa80360.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### 3D圖 ###
[**3D圖繪圖方法**](https://matplotlib.org/tutorials/toolkits/mplot3d.html#sphx-glr-tutorials-toolkits-mplot3d-py)
[**3D圖所有相關方法**](https://matplotlib.org/api/_as_gen/mpl_toolkits.mplot3d.axes3d.Axes3D.html)   

- 文字
[Axes3D.text](https://matplotlib.org/examples/mplot3d/text3d_demo.html)
- 表面圖     
Axes3D.plot_surface（X, Y, Z, *args, norm=None, vmin=None, vmax=None, lightsource=None, **kwargs）    
![z=x+y](https://upload-images.jianshu.io/upload_images/13539817-9070a23c80fecac8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)    ![範例](https://upload-images.jianshu.io/upload_images/13539817-58432e3cd6d5b70c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 線形圖    
Axes3D.plot（xs，ys，* args，zdir ='z'，** kwargs ）
![範例](https://upload-images.jianshu.io/upload_images/13539817-4583e7559117cbe7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 散點圖    
Axes3D.scatter（xs，ys，zs = 0，zdir ='z'，s = 20，c = None，depthshade = True，* args，** kwargs ）
![範例](https://upload-images.jianshu.io/upload_images/13539817-4c11751216e2f2e9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![範例](https://upload-images.jianshu.io/upload_images/13539817-475bf0e5eeb3e413.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 線框圖     
Axes3D.plot_wireframe（X，Y，Z，* args，** kwargs ）
![範例](https://upload-images.jianshu.io/upload_images/13539817-b1bff04c78bf4358.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 等高線圖      
Axes3D.contour(X, Y, Z, *args, zdir='z', offset=None, **kwargs)
![範例](https://upload-images.jianshu.io/upload_images/13539817-ea91ea014f539e0f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 填充等高線圖      
Axes3D.contourf(X, Y, Z, *args, zdir='z', offset=None, **kwargs)
![範例](https://upload-images.jianshu.io/upload_images/13539817-52dd17bf48d2de79.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 向量圖    
Axes3D.quiver（* args，length = 1，arrow_length_ratio = 0.3，pivot ='tail'，normalize = False，** kwargs ）        
![範例](https://upload-images.jianshu.io/upload_images/13539817-18fe6fad1562ba26.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

其他比較少用的方法請參考官方範例

### 動畫 ###
[動畫](https://matplotlib.org/api/animation_api.html#helper-classes)
- 匯入模組      
![](https://upload-images.jianshu.io/upload_images/13539817-a64a29a9802e7149.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 繪製及儲存
gif儲存需安裝[imagemagick](https://imagemagick.org/script/download.php#windows)
[matplotlib.animation.FuncAnimation](https://matplotlib.org/api/_as_gen/matplotlib.animation.FuncAnimation.html#matplotlib.animation.FuncAnimation)
![](https://upload-images.jianshu.io/upload_images/13539817-1f9136d0a17069b3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)      ![](https://upload-images.jianshu.io/upload_images/13539817-d626505f0cabe385.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![](https://upload-images.jianshu.io/upload_images/13539817-ffe70685b84212c0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)      ![](https://upload-images.jianshu.io/upload_images/13539817-f01ad33bb642ed35.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![](https://upload-images.jianshu.io/upload_images/13539817-e2eb553e3807d969.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)     ![](https://upload-images.jianshu.io/upload_images/13539817-f5e692db69e9eb35.gif?imageMogr2/auto-orient/strip)



### 進階應用 ###
matplotlib還有許多工具包與相關模塊套件可以使用，下面列舉其中一些，更深入可以到官網查詢以及參考一些前輩的文章。

- 地圖相關
[教程](https://github.com/jakevdp/PythonDataScienceHandbook/blob/be23269c7eb119e093a6d5ce91e464f5e686d9ab/notebooks/04.13-Geographic-Data-With-Basemap.ipynb)

-  seaborn模塊    
[官網](https://seaborn.pydata.org/#)
[簡易教程](https://github.com/jakevdp/PythonDataScienceHandbook/blob/be23269c7eb119e093a6d5ce91e464f5e686d9ab/notebooks/04.14-Visualization-With-Seaborn.ipynb)

- mayavi模塊
繪製複雜的3D圖時建議使用mayavi，matplotlib3D在重疊的3D結構顯示上並不佳。
[mayavi文檔](https://docs.enthought.com/mayavi/mayavi/index.html)
[mayavi簡易教程](https://www.jianshu.com/p/b49f8c629b38)
