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
