# 学习Flutter和Dart记录
[帖子传送门](https://juejin.cn/post/6844903972625448973)  
![image](https://github.com/SilenceWeak/mylinux/blob/master/pictures/DartDataType.png)

> * ***需要注意的地方***
>>  * **变量默认都是public，除此之外都是private且前面加上_表示private，同时Dart里的private仅仅修饰库访问级别**
>>  * **const是编译时常量，在编译时就进行初始化了，但是final变量是当类创建的时候才初始化**
>>  * **在自定义函数上有许多不同其不支持重载函数**
```
      //要达到可选命名参数的用法，那就在定义函数的时候给参数加上 {}
      void test1Flags({bool bold, bool hidden}) => printTest("$bold , $hidden");

      //定义可选命名参数时增加默认值
      void test2Flags({bool bold = true, bool hidden = false}) => printTest("$bold ,$hidden");

      //可忽略的参数在函数定义时用[]符号指定
      void test3Flags(bool bold, [bool hidden]) => printTest("$bold ,$hidden");

      //定义可忽略参数时增加默认值
      void test4Flags(bool bold, [bool hidden = false]) => printTest("$bold ,$hidden");

      //可选命名参数函数调用
      test1Flags(bold: true, hidden: false); //true, false
      test1Flags(bold: true); //true, null
      test2Flags(bold: false); //false, false

      //可忽略参数函数调用
      test3Flags(true, false); //true, false
      test3Flags(true,); //true, null
      test4Flags(true); //true, false
      test4Flags(true,true); // true, true
```
  >> * **复用（extends,implement,mixin,on）**
  >>> * **在Dart中，对一个父类仅能同时选择一种方式：实现或继承**
```
        class TestA{
        num x,y,z;

        TestA(this.x,this.y):z =0;
        TestA.bottom(num x):this(x,0);
        TestA.top():x=3;

        void testCall() => print("($x=======,$y======)");
        }

      class TestB extends TestA{
        TestB(num x, num y) : super(x, y);

        @override
        void testCall() { //重写testCall的实现
          // TODO: implement testCall
          super.testCall();
        }
      }

      class TestC implements TestA{
        @override
        num x;

        @override
        num y;

        @override
        num z;

        @override
        void testCall() {  //必须实现该方法
          // TODO: implement testCall
        }
      }
```
>> * **使用Mixin（混入）来提高继承灵活性和复用性，简而言之，Mixin是为了解决implement无法复用父类方法而存在的，其存在意义和C++的多重继承有关，而为了实现Mixin，我们通常会使用with或on关键字。但是被“混入”的类也存在要求，即不能实现自己的构造器**
```
      class D{

        num x,y;
        D(this.x,this.y);
        void testCall() => print("($x=======,$y======)");
      }

      class E with D{  //编译失败，提示D类不能被混入，因为已经定义了构造器。

      }
```
>> * **Mixin使用on关键字：即被with的A类假如使用了on关键字作用一个B类，那么当C想要with A时必须先实现或继承了B之后才能with A**
```
      class F{

      }

      mixin G on F{

      }

      class H extends F with G{ //必须先继承F类才可以，如果F是接口，那就必须先实现接口F

      }
```
* 看看效果
      * 效果

      }
      }
