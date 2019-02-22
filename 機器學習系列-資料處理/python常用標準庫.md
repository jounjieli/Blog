- **os模組**
Python 的 os 模組封裝了常見的檔和目錄操作，這裡只列出部分常用的方法，更多的方法可以查看[官方文檔](https://docs.python.org/3/library/os.path.html)。

下面是部分常見的用法：
| 方法             | 說明                         |
| ---------------- | ---------------------------- |
| os.mkdir()         | 創建目錄                     |
| os.rmdir()         | 刪除目錄                     |
| os.rename()        | 重命名                       |
| os.remove()        | 刪除檔                       |
| os.getcwd()        | 獲取當前工作路徑             |
| os.walk()          | 遍歷目錄                     |
| os.path.join()     | 連接目錄與檔案名             |
| os.path.split()    | 分割檔案名與目錄             |
| os.path.abspath()  | 獲取絕對路徑                 |
| os.path.dirname()  | 獲取路徑                     |
| os.path.basename() | 獲取檔案名或資料夾名         |
| os.path.splitext() | 分離檔案名與副檔名           |
| os.path.isfile()   | 判斷給出的路徑是否是一個檔   |
| os.path.isdir()    | 判斷給出的路徑是否是一個目錄 |

- **socket**

| service              |                                                              |
| -------------------- | ------------------------------------------------------------ |
| socket.bind()        | 綁定(主機,埠號)到通訊端                                      |
| socket.listen()      | 開始TCP監聽                                                  |
| socket.accept()      | 被動接受TCP客戶的連接,(阻塞式)等待連接的到來                 |
| **client**               |                                                              |
| socket.connect()     | 主動初始化TCP伺服器連接                                      |
| socket.connect_ex()  | connect()函數的擴展版本,出錯時返回出錯碼,而不是拋出異常      |
| **共用**                 |                                                              |
| socket.recv()        | 接收TCP資料                                                  |
| socket.send()        | 發送TCP資料(send在待發送資料量大於己端緩存區剩餘空間時,資料丟失,不會發完) |
| socket.sendall()     | 發送完整的TCP資料(本質就是迴圈調用send,sendall在待發送資料量大於己端緩存區剩餘空間時,資料不丟失,迴圈調用send直到發完) |
| socket.recvfrom()    | 接收UDP資料                                                  |
| socket.sendto()      | 發送UDP資料                                                  |
| socket.getpeername() | 連接到當前通訊端的遠端的位址                                 |
| socket.getsockname() | 當前通訊端的地址                                             |
| socket.getsockopt()  | 返回指定通訊端的參數                                         |
| socket.setsockopt()  | 設置指定通訊端的參數                                         |
| socket.close()       | 關閉通訊端                                                   |
| **其他設置**             |                                                              |
| socket.setblocking() | 設置通訊端的阻塞與非阻塞模式                                 |
| socket.settimeout()  | 設置阻塞通訊端操作的超時時間                                 |
| socket.gettimeout()  | 得到阻塞通訊端操作的超時時間                                 |
| socket.fileno()      | 通訊端的檔描述符                                             |
| socket.makefile()    | 創建一個與該通訊端相關的檔                                   |

範例:
1(https://gist.github.com/jounjieli/18aa9556640fa877bf17b05e595b5fc5)，2(https://gist.github.com/jounjieli/ddf28b9e4c2b98a0725e4790605b3da7)

- [with as](https://openhome.cc/Gossip/Python/WithAs.html)
with as用法
- [urllib.request.urlretrieve](https://docs.python.org/3/library/urllib.request.html?highlight=urlretrieve#urllib.request.urlretrieve)
檔案下載
- [struct](https://docs.python.org/3/library/struct.html#module-struct)
資料結構(常用於2進制文件處理)
- [gzip](https://docs.python.org/3/library/gzip.html#module-gzip)
讀寫gz文件
- [zipfile](https://docs.python.org/3/library/zipfile.html#module-zipfile)
讀寫zip文件
- [io](https://docs.python.org/3/library/io.html#module-io)
內存中的數據要進行IO讀寫可以使用StringIO和BytesIO
- [shutil](https://docs.python.org/3/library/shutil.html#module-shutil)
移動、復制、打包、壓縮、解壓等操作。

(這比較雜有時間再更新)
