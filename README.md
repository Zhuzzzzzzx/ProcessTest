# 一个安卓自定义流程图

### 先上效果图：

![](http://upload-images.jianshu.io/upload_images/3944777-aaba2399d478785c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

如图，可实现设置：总流程数、已完进度程数、已完成颜色、各个流程点击事件、各个标题

***

### 使用方法

1.导入compile 'com.github.pavlospt:circleview:1.3'依赖包（因为用到了CircleView）

2.直接把这两个文件一个
[xml](https://github.com/Zhuzzzzzzx/ProcessTest/blob/master/app/src/main/res/layout/process_img.xml)
一个
[java](https://github.com/Zhuzzzzzzx/ProcessTest/blob/master/app/src/main/java/com/zxzhu/processtest/Common/ProcessImg.java)
，复制粘贴进项目（代码放在了文章最后，暂时还没弄成开源库，有时间直接做成依赖包倒进去）

* 在xml中写入ProcessImg控件

* 在java文件中实例化ProcessImg对象

* 根据需要调用几个方法

**1.对象.setColor( int color )**

设置已完成的进度的颜色，传入颜色的整型值

**2.对象.setProcess( int total ,  int process )**

设置总流程数和已完成进度数，第一个参数为总流程数（1~6，因为超过6个堆在一排很难看），第二个为已完成数，均为整型变量

**3.对象.setTitle( int position , String text )**

设置各流程的标题，第一个参数为标题对应的流程数（1~total），第二个参数为String格式标题文本

**4.对象.setClick( int position , Click click ) **
设置各流程的点击事件，第一个参数是点击的流程（1~total），第二个参数为点击后的回调方法。

***
### 使用实例
```
        processImg.setColor(Color.parseColor("#FFFF8C56"));
        processImg.setProcess(3,2);
        processImg.setTitle(1,"title1");
        processImg.setTitle(2,"title2");
        processImg.setTitle(3,"title3");
        processImg.setClick(1, new ProcessImg.Click() {
            @Override
            public void click() {
                Toast.makeText(MainActivity.this, "点击第1项", Toast.LENGTH_SHORT).show();
            }
        });
        processImg.setClick(2, new ProcessImg.Click() {
            @Override
            public void click() {
                Toast.makeText(MainActivity.this, "点击第2项", Toast.LENGTH_SHORT).show();
            }
        });
        processImg.setClick(3, new ProcessImg.Click() {
            @Override
            public void click() {
                Toast.makeText(MainActivity.this, "点击第3项", Toast.LENGTH_SHORT).show();
            }
        });
        
```
```
        <com.zxzhu.processtest.Common.ProcessImg
                android:id="@+id/process"
                android:layout_margin="10dp"
                android:layout_gravity="center"
                android:layout_width="match_parent"
                android:layout_height="wrap_content">
        </com.zxzhu.processtest.Common.ProcessImg>
```
