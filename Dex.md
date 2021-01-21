# 本帖子将主要用来记录安卓APK文件打包后的结构
### 什么是Dex文件?  
  *是Android系统的可执行文件，包含着应用程序的所有操作指令及运行时数据*  
### 为什么存在Dex文件？  
  *Dalvik是一种专门应对嵌入式系统设计的虚拟机，所以Dex和普通的class文件有着本质的区别，具体的关系为*  
  * Java在编译成Class文件后，需要用Dx工具将所有的class文件整合到一个Dex文件，目的是为了各个类能够共享数据，在一定程度上能降低冗余，为了能让文件更加的紧凑，实验证明Dex文件是传统的jar文件的50%左右  
  ![image](https://upload-images.jianshu.io/upload_images/1152636-8230c5995981b7c2.png?imageMogr2/auto-orient/strip|imageView2/2/w/604/format/webp)
### Dex文件结构  
  |数据名称||解释|  
  |:----:||:--:|  
  |测试||测试|  
