这是一个不用进行数据标注，自动产生深度学习训练集（tensorflow标准数据集格式tfrecord)的脚本。
## 环境说明
- python3.6
- tensorflow-cpu 1.2.1

## 结构说明
- autoGimg文件夹用于存放程序自动产生的图片
- autoGtfrecord文件夹用于存放程序产生的tfrecord格式的训练集文件
- bimg文件夹用于存放提供给程序的背景图片，
   命名必须以连续的数字命名，格式为jpg,形如"1.jpg,2.jpg..."
- timg文件夹用于存放目标物品图片，命名遵循“标签-序号"的格式，图片格式为png。形如"AD-1.png,AD-2.png..."
- label.py 关于标签
- gen_img_tfrecord.py 主程序
- dataset_utils.py tensorflow中一些关于数据集处理的函数
## 使用说明
1.克隆项目到本地
```
git clone https://github.com/SwordLight6/auto-gen-tfrecord.git
```


2.运行gen_img_tfrecord.py

```
python gen_img_tfrecord.py -c 20 
```
起始已经提供了一些图片了，直接运行没有问题，具体的需求和配置查看函数参数的含义自行配置
（直接运行的效果是使用背景图的前10张，生成20张含有目标图的图片，以及20张生成的图片对应的tfrecord，如果自行提供图片，
还需要做如下事情：1.把你处理好的目标图（遵循命名和格式要求）放到timg文件夹下 2.把你的背景图（遵循命名和格式要求）放到bimg文件夹下）


## 生成图片的效果




![image](https://raw.githubusercontent.com/SwordLight6/auto-gen-tfrecord/master/autoGimg/000000.jpg)

![image](https://raw.githubusercontent.com/SwordLight6/auto-gen-tfrecord/master/autoGimg/000003.jpg)

![image](https://raw.githubusercontent.com/SwordLight6/auto-gen-tfrecord/master/autoGimg/000009.jpg)
![image](https://raw.githubusercontent.com/SwordLight6/auto-gen-tfrecord/master/autoGimg/000012.jpg)

## 训练模型的识别效果
使用的是tensorflow实现的SSD网络模型  
具体分别使用使用了两版模型进行训练  
1.https://github.com/balancap/SSD-Tensorflow  
2.https://github.com/HiKapok/SSD.TensorFlow  
 效果还行吧（毕竟是偷懒的结果）  
 
![image](https://raw.githubusercontent.com/SwordLight6/blog-photos/master/photos/ssd/1.jpg)
![image](https://raw.githubusercontent.com/SwordLight6/blog-photos/master/photos/ssd/2.png)
![image](https://raw.githubusercontent.com/SwordLight6/blog-photos/master/photos/ssd/3.png)
![image](https://raw.githubusercontent.com/SwordLight6/blog-photos/master/photos/ssd/4.png)

 




