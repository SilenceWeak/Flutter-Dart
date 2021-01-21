# 本帖子将主要用来记录安卓APK文件打包后的结构
### 什么是Dex文件?  
  *是Android系统的可执行文件，包含着应用程序的所有操作指令及运行时数据*  
### 为什么存在Dex文件？  
  *Dalvik是一种专门应对嵌入式系统设计的虚拟机，所以Dex和普通的class文件有着本质的区别，具体的关系为*  
  * Java在编译成Class文件后，需要用Dx工具将所有的class文件整合到一个Dex文件，目的是为了各个类能够共享数据，在一定程度上能降低冗余，为了能让文件更加的紧凑，实验证明Dex文件是传统的jar文件的50%左右  
  ![image](https://upload-images.jianshu.io/upload_images/1152636-8230c5995981b7c2.png?imageMogr2/auto-orient/strip|imageView2/2/w/604/format/webp)
### Dex文件结构  
  |数据名称|解释|  
  |:----:|:--:|  
  |header|dex文件头部，记录整个dex文件的相关属性|  
  |string_ids|字符串数据索引，记录了每个字符串在数据区的偏移量|
  |type_ids|类似数据索引，记录了每个类型的字符串索引|
  |proto_ids|原型数据索引，记录了方法声明的字符串，返回类型字符串，参数列表|
  |field_ids|字段数据索引，记录了所属类，类型以及方法名|
  |method_ids|类方法索引，记录方法所属类名，方法声明以及方法名等信息|
  |class_defs|类定义数据索引，记录指定类各类信息，包括接口，超类，类数据偏移量|
  |data|数据区，保存了各个类的真是数据|
  |link_data|连接数据区|  
  ```
  struct DexFile {
    const DexHeader*    pHeader;
    const DexStringId*  pStringIds;
    const DexTypeId*    pTypeIds;
    const DexFieldId*   pFieldIds;
    const DexMethodId*  pMethodIds;
    const DexProtoId*   pProtoIds;
    const DexClassDef*  pClassDefs;
    const DexLink*      pLinkData;
  }
  ```
