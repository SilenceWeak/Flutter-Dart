# 本帖子将主要用来记录安卓APK文件打包后的结构
* **zip文件格式讲解链接**  
  * [帖子传送门](https://blog.csdn.net/a200710716/article/details/51644421)  
  * *zip文件地址偏移*  
    ![image](https://github.com/SilenceWeak/Flutter-Dart/blob/main/Picture/image.png)  
  * 这里只考虑最简单的一种场景，只包括一个文本文件的压缩文件。  
    新建一个名为123.txt的文本文件，内容为123456  
    将123.txt压缩为123.zip  
    使用winhex打开123.zip（注：winhex是以小端模式展示数据的）
    ![image](https://github.com/SilenceWeak/Flutter-Dart/blob/main/Picture/sampleZip.jpg)  
    ***对于这里的结果有***
    ![image](https://github.com/SilenceWeak/Flutter-Dart/blob/main/Picture/WX20210121-111417%402x.png)  
    ![image](https://github.com/SilenceWeak/Flutter-Dart/blob/main/Picture/WX20210121-111446%402x.png)  
    ![image](https://github.com/SilenceWeak/Flutter-Dart/blob/main/Picture/WX20210121-111500%402x.png)  

* **APK文件格式讲解链接**  
  * [帖子传送门](https://juejin.cn/post/6844903780253712397)  
  * APK在签名（V2/V3签名）之后，会在数据区和中央目录区之间插入APK签名区（APK Signing Block）  
   ![image](https://github.com/SilenceWeak/Flutter-Dart/blob/main/Picture/1690e1d9a37b9ea7.jpg)  
  * APK签名区的构成结构如下  
   ![image](https://github.com/SilenceWeak/Flutter-Dart/blob/main/Picture/1690b94da301ef99.jpg)  
  * 其表格展示如下：  
    * Block长度：APK签名块总长度，包括后面三个部分  
    * ID-Value序列  
    * Block长度：同上  
    * 魔数：APK Sig Block 42，hex大端表示的话就是：41 50 4b 20 3 69 67 20 42 6c 6f 63 6b 20 34 32  
   ![image](https://github.com/SilenceWeak/Flutter-Dart/blob/main/Picture/1690b957a28439b9.jpg)  
  * ID-Value里面存储着ID-Value列表，其序列的结构如下图所示  
   ![image](https://github.com/SilenceWeak/Flutter-Dart/blob/main/Picture/1690e1c184e2c5fa.jpg)  
  * 列表的每个Item由三部分组成（8字节长度+4字节ID+内容）。其中APK的签名信息就是其中的某一块，其ID为0x7109871a
   ![image](https://github.com/SilenceWeak/Flutter-Dart/blob/main/Picture/1690e1c51087a6bf.jpg)  
  * Android怎么将计算签名信息插入到Item里及校验APK的完整性见[APK签名机制之——V2签名机制详解](https://www.jianshu.com/p/308515c94dc6)
  
