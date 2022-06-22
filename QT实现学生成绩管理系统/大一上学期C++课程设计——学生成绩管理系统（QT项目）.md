## **这里是一个大一的萌新！仅做学习分享**

近期整理了一下大一上学期的课程设计报告作为学习总结，使用的软件是Qt Creator，主界面效果如下图

![在这里插入图片描述](https://img-blog.csdnimg.cn/9e83d21009224d27b246609eab6bb73f.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)




——————————以下为课程设计报告———————————

# ***\*学生成绩管理系统设计\****

## 1 基本功能描述

学生成绩管理系统包括以下功能

（1）添加功能：程序能够添加不同学生的记录，提供选择界面供用户选择所要添加的类别，要求学号要唯一，如果添加了重复学号的记录时，则提示数据添加重复并取消添加。

（2）查询功能：可根据学号、姓名等信息对已添加的学生记录进行查询，如果未找到，给出相应的提示信息，如果找到，则显示相应的记录信息。

（3）显示功能：可显示当前系统中所有学生的记录，每条记录占据一行。

（4）编辑功能：可根据查询结果对相应的记录进行修改，修改时注意学号的唯一性。

（5）删除功能：主要实现对已添加的学生记录进行删除。如果当前系统中没有相应的记录，则提示“记录为空！”并返回操作。

（6）统计功能：能根据多种参数进行统计。能统计学生人数、总分、单科的平均分等。

（7）保存功能：可将当前系统中各类记录存入文件中，存入方式任意。

（8）读取功能：可将保存在文件中的信息读入到当前系统中，供用户进行使用。

（9）排序功能：可按总分和单科成绩排名次。

 

## **2 设计思路**

如图是整个学生成绩管理系统的流程图，本程序使用QT来设计图形界面。

如流程图所示，在主函数中先创建一个主窗口类来作为功能导航，操作者可以在主窗口选择点击添加信息、查询和修改、统计和操作进入对应的子窗口来进行各项功能的使用

在添加学生窗口类中可以进行学生信息的录入，学号重复会有提示

在查询和修改窗口类中可以点击对应查询的条目显示出对应学号信息并选择修改或者删除，点击修改会进入到修改子窗口进行信息的修改

在统计和排序窗口类中可以查看到对应学生的各种信息和计算得到的平均分总分等，并能通过点击排序按钮进行排序

（每一个窗口类都涉及到读文件和传递字符串到显示model上的操作、对存入信息是否合法的判断、清空界面、修改显示内容等等保证功能实现的成员函数，具体请看代码）



![在这里插入图片描述](https://img-blog.csdnimg.cn/06fadf6dfd5e4bc4b5a6814a4b64dd1a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)


图1 流程图



![在这里插入图片描述](https://img-blog.csdnimg.cn/039ab99a7b7e4e8aafa8c9ac87a46e39.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
 

图2 主窗口

## 3 软件设计

### **3.1 设计步骤**

打开Qt Creator,在文件中点击新建，在弹出框内选择Application的QT widgets模板，输入工程名stumanager及其所在位置，点击确定，如图3所示。   

![在这里插入图片描述](https://img-blog.csdnimg.cn/56adb7799cc34bf1995e9a93b4cfbdce.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
 

图3 新建QT工程

将弹出的对话框，选择主窗口mainwindow类，点击下一步，如图4所示。
![在这里插入图片描述](https://img-blog.csdnimg.cn/f4e68d9869244ff78e23eac70722e18b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)


图4 基本对话框

这样，Qt Creator就建立了一个基于主窗口的程序框架，如图5所示。

![在这里插入图片描述](https://img-blog.csdnimg.cn/b65a3b754fe24190bfbd36d6db0ee171.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)


图5 新建的主窗口框

### ***3.2 界面设计***

1、创建控件

在图5所示的Forms选项卡中双击打开ui界面，在窗口左边。开始摆放控件，包括编辑框和按钮的创建。按钮的创建以“添加学生”为例进行介绍，其他按钮的创建可参照此进行操作。

![在这里插入图片描述](https://img-blog.csdnimg.cn/2b2633d0ffee4d408c2c45b9b50ab898.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_10,color_FFFFFF,t_70,g_se,x_16#pic_center)


图6 选择ui设计界面

![在这里插入图片描述](https://img-blog.csdnimg.cn/30df8c24e65a44978fca463f7905d929.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)


图7 UI设计界面

1）在图6中左侧列表选择合适的控件拖拽到设计界面中间进行摆放。 

2）在图6中“Buttons”按钮上单击鼠标左键，在对话框上的合适的位置上按下鼠标左键并拖动鼠标画出一个大小合适的下压式按钮。在按钮上单击鼠标右键，在弹出的快捷菜单中选择属性选项，此时也弹出Push Button属性对话框，如图7所示，在该对话框中输入控件的ID值和标题属性。

![在这里插入图片描述](https://img-blog.csdnimg.cn/c5f6ef55275247848bcec842e9457075.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_11,color_FFFFFF,t_70,g_se,x_16#pic_center)
 

图8 Push Button属性

按照上面的操作过程编辑其他按钮和编辑框等对象的属性。

 

 

**表1 添加学生类中** **各按钮和编辑框等对象的属性**

| 对象     | ID        | 标题或说明      |
| -------- | --------- | --------------- |
| 编辑框   | lid       | 输入学号        |
| 按钮     | btnok     | 确认按钮        |
| 按钮     | btncancel | 取消按钮        |
| 下拉列表 | lage      | 选择年龄        |
| 按钮组   | stuchoose | 选择小中大学生  |
| ......   | .....     | 控件实在太多... |

完成后界面如图8所示。

 

![在这里插入图片描述](https://img-blog.csdnimg.cn/93124a1e5bb142fdb769d5c409911cf5.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
 

图9添加学生界面

2、连接变量和代码

\1) 给按钮连接变量。在按钮上单击鼠标右键，在弹出菜单中选择转到槽，就可以给该窗口类添加一个槽函数来进行点击输入等事件的操作，如图9所示。 

![在这里插入图片描述](https://img-blog.csdnimg.cn/8ec573cda1454ef6ba57e26719f76e3f.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
 

图10 转到槽

在转到槽列表框中选择信号clicked()，就能添加该事件对应的槽函数如图11所示

![在这里插入图片描述](https://img-blog.csdnimg.cn/f914fd5d41bf4164bff7df5723b3de1f.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)


图11 新建的槽函数

创建成功后，在槽函数中写下实现相应功能的代码即可

 

 

### ***3.3 关键功能的实现***

1）学生信息的输入

编辑框所关联的变量为lid,lname等，还有按钮组、下拉列表等实现信息填入的控件，当点击确认按钮且信息合法时，将进行录入信息函数

2）查询功能的实现

一开始和添加功能类似，先将选择搜索的对应信息存入key字符串，读取文件后作为关键字在文件中搜索出对应条目，点击时会显示对应学号供操作者修改或删除对应信息

3）删除和修改的实现

由于学号有唯一性，所以按照学号来对对应信息条目进行删除和修改，点击删除后弹框提醒确认删除后进行删除操作，点击修改则弹出修改子窗口进行信息的更改

删除功能：将对应信息作为字符串存起来，遍历存储信息的list容器进行覆盖存储文件，当遍历到要删除的信息时不存储即可

修改功能：将要修改的信息存储起来填到修改信息窗口上给操作者进行修改，注意此处由于学号唯一，学号不可修改，若有需要则在删除操作中删除对应学号信息

4）统计和排序的实现

当选择小中大学生时按默认顺序显示全部学生信息，在传入list容器时直接计算统计后显示各科平均分等，选择对应排序条件后点击排序按钮，将使用tableview类中自带的排序方法对数据进行排序

 

## ***4 结论与心得体会***

经过长时间的调试修改，得出结论该学生成绩管理系统符合题目所需要求

心得体会：花费了一整周时间来学习QT来设计自己的图形界面实现课设所需功能，最终实现用了自己喜欢的图案完成程序，真的很有成就感，也实现了自己在程序设计上的一个小目标——写出自己的第一个设计项目（虽然还比较简单）。

在编写过程中遇到非常多的困难，一般都是通过搜索对应问题和上CSDN看大佬的博客解决，掌握了学习程序设计遇到困难的解决办法、也收获了大量的编程知识

## ***5 参考文献***

[1] 谭浩强 C++程序设计（第3版）清华大学出版社 2015

[2] [Henrik-Yao](https://blog.csdn.net/qq_50216270) C++的QT项目打包成独立可执行和发布的exe文件

CSDN网址：https://blog.csdn.net/qq_50216270/article/details/121374493

 

## ***6 附录***

### ***6.1 调试报告***

1、编译时提示错误：

E:\Code\QT\classwork\StudentManager\main.cpp:31: error: expected ';' before 'return'

   return a.exec();//涓昏繍琛屽惊鐜

   ^

原因为分号是在中文输入法状态下输入，将其改为英文输入状态下了分号即可。

2、添加学生后出现信息重复学号写入的问题，在成员函数中添加一个判断添加信息是否合法的判断：即信息是否与之前重复，若重复则弹出窗口提示操作者

3、统计和排序显示时切换小中大学生会出现小学生也有地理历史成绩的情况，解决方法为添加一个槽函数，当下拉列表对应的文本改变时，清空tableview显示再继续进行显示信息

### ***6.2 测试结果***

主窗口如下

![在这里插入图片描述](https://img-blog.csdnimg.cn/c72bebc6109941f481a31996b80d2939.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_17,color_FFFFFF,t_70,g_se,x_16#pic_center)
图12 主窗口
 

1.在主窗口点击添加信息，输入各种学生信息，并点击确认按钮，得到结果如图13。

![在这里插入图片描述](https://img-blog.csdnimg.cn/b6a0edf96efa4a74a100e2c14ef55f1e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_13,color_FFFFFF,t_70,g_se,x_16#pic_center)
 

图13 结果图一

在主窗口点击统计和排序，在统计和排序中可看到存入的信息如图14（学生名：测试）

并且该窗口下方显示的即为统计得到的信息，处理成功

 

![在这里插入图片描述](https://img-blog.csdnimg.cn/eb7faa73f8b14fe5a70a7459d3c42093.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
 

图14 结果图二

2.选择按英语成绩排序、升序，点击排序按钮，结果如图15.

![在这里插入图片描述](https://img-blog.csdnimg.cn/0334dfab36ee46a6a1a83d5d94eb1084.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
 

图15 结果图三

可以看到成功实现排序且左侧有子列显示当前所排序的项的成绩信息

3.在主窗口中点击查询和修改，选择学生就读情况，搜索对应信息学生名字“测试”

![在这里插入图片描述](https://img-blog.csdnimg.cn/22d3966e65e3493c87ea66cd88fc023c.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)
 

图16 结果图四

成功显示搜索结果，证明搜索功能实现正常。

4.点击搜索结果行，在下方显示出对应学号，按搜索出的学号进行修改或删除

![在这里插入图片描述](https://img-blog.csdnimg.cn/43f0e2c28054405492bc5ed762344001.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_12,color_FFFFFF,t_70,g_se,x_16#pic_center)
 

图17 结果图五

点击修改，弹出修改信息框进行修改如图17

![在这里插入图片描述](https://img-blog.csdnimg.cn/6d5a5007d0714c5fa528742f2410fbf8.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA5rW36JuLMjMzMw==,size_17,color_FFFFFF,t_70,g_se,x_16#pic_center)
 

图18 结果图六

点击删除，如图18点击确认删除后，提示成功删除信息

在统计和排序中再次查看信息发现信息均成功修改或删除，实现成功

5.添加学生时输入作者名字海蛋作为学生姓名，将弹出小彩蛋

 

 

### ***6.3 关键源代码***

#### ***\*1.主函数main\****

```cpp
int main(int argc, char *argv[])

{

  QApplication a(argc, argv);//创建QT实例

 

  MainWindow w;

  w.show();

  return a.exec();//主运行循环

}
```

 

#### ***\*2.读写文件的操作函数（基本每个窗口类都有）\****

```cpp
int addstu::readFile()//读文件

{

  QFile file("stu.txt");

  if(!file.**open**(QIODevice::ReadOnly|QIODevice::Text))//打开不成功

  {

​    return -1;

  }

  QTextStream in(&file);

 

  while(!in.atEnd())//没读到文件尾则继续读

  {

​     QString line =in.readLine();//读取一行

​     stu_lines.append(line);//每行都存放到list中

  }

  file.**close**();//关闭

  return 0;//读取成功

}

//读写文件：

void addstu::writeToFile(QString cnt)//保存学生信息

{

  QFile file("stu.txt");

  if(!file.**open**(QIODevice::Append|QIODevice::Text))

  {

​    QMessageBox::warning(this,"错误","文件打开失败，信息未保存","确定");

​    return;

  }

  QTextStream out(&file);

  out<<cnt;//写cnt进文件中

  file.**close**();

}
```


#### ***\*3.实现统计和排序函数\****

```cpp
void sortstu::on_sortbtn_clicked()//点击排序

{

  int flag;//要排的列，升序或降序

  //已经获取过what了

  flag=ui->sortflag->currentIndex();//

  int way=ui->sortway->currentIndex();

  if(way==0||what==0)

  {

​    QMessageBox::warning(this,"提示","请选择排序方式");

​    return;

  }

  if(what==1)//小学生

  {

​    Student *stu=new StudentS;//建一个学生类指针

​    col=stu->sortTable(way);//得到要排的序号

​    delete stu;

  }

  else if(what==2)//中学生

  {

​    Student *stu=new StudentM;//建一个学生类指针

​    col=stu->sortTable(way);

​    delete stu;

  }

  else if(what==3)//大学生

  {

​    Student *stu=new StudentL;//建一个学生类指针

​    col=stu->sortTable(way);

​    delete stu;

  }

 

  //设置对应搜索条件的表头

  this->model3->

  setHorizontalHeaderItem(0,new QStandardItem(this->model->**headerData**(col,Qt::Horizontal).toString()));

  docopy();//复制对应列

  //排序在这里!!!!!!!!!!!!!!!!!!!!!---------------------------------------------------------------

  if(flag==1)//降序

  {

​    this->model->**sort**(col,Qt::DescendingOrder);

​    this->model3->**sort**(0,Qt::DescendingOrder);

 

  }

  else if(flag==0)//升序

  {

​    this->model->**sort**(col,Qt::AscendingOrder);

​    this->model3->**sort**(0,Qt::AscendingOrder);

  }

 

}
```

基本上全部重要的代码都附上了，但因为代码量过大无法一一CV过来，若要深入研究可查看工程文件


**上传日期：22.4.10
作者：海蛋**
