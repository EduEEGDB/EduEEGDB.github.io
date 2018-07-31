---
layout: post
title: 数据集摘要
subtitle: 脑电实验数据集
---


本实验的数据集共包括两个部分：

1. 测试图片。测试图片包括两个部分的静态图片数据，用来通过视觉刺激大脑产生相应的困惑/非困惑情绪。两个部分分别为10张平和的风景图片（用来刺激产生非困惑情绪），48张复杂的推理问题图片（用来刺激产生困惑情绪）。
2. 脑电波数据。在实验者观察图片时，头部的八个传感器以250Hz的频率采集其脑电波数据，每次测试项目形成单个数据集文件。本实验包含25组测试项目，共25组脑电波数据集，分别来自25个实验者。





## 测试图片

整个测试图片集包括58张图片，分别为10张风景图片和48张推理问题图片。

* 风景图片的选取原则是图片画面开阔，颜色缓和，光线颜色较为明亮，给实验则以舒适，平静的感觉。内容包括：沙滩、夕阳、山峰、河谷、湖泊等。

<img src="风景图.jpg" width="400px">

* 推理问题图片来自瑞文推理测验，每张图片为一道规律推理题，共48道题，分为12道标准难度问题和36道高级难度问题。选取问题图片的标准是图片清晰，试题内容相对复杂，从而使实验者需要进行一定的思考，保证持续一定时间的困惑情绪。


测试流程时间大约在15分钟左右，分为三个部分。

第一部分展示风景图片，每张图片的持续时间为10秒，连续播放中间不停顿。

第二部分展示推理问题图片，在实验者示意后开始，每张图片的最长持续时间为10秒，如果实验者选择出答案，会立即跳转到下一张图片，否则在10秒后跳转。

第三部分是置信度测试，按照顺序重新回放第二部分的推理图片，实验者根据是否想出答案选择困惑或者非困惑的选项，以检测实验者在该问题图片测试中是否保持困惑情绪状态。



## 脑电波数据

* **原始数据**

本实验共包括25组脑电波数据，每组数据为一个单独的文件。数据内容以一行为一个采集记录，每秒的时间段内包括250行数据记录（采集频率为250Hz）。原始数据中每一个采集记录包括11列，第一列为每秒内记录的序号（0 - 255），第二至九列为8个传感器在这一时间点采集到的数据，第十列为图片跳转的标记信号（每次图片跳转时产生一个标记脉冲），第十一列为采集时间。

* **预处理数据**

对于每一条采集记录，去掉第一列和第十一列（对实验过程不影响）。根据第十列的标记信号，将数据按照每张图片进行分割。第一组到第十组设置为非困惑组。第十一组到第五十八组中，实验者对题目没有作答的直接设为困惑组，有作答的根据置信度进行判断，选出可信的困惑组，其余的数据作丢弃处理。根据已经设置好的困惑组和非困惑组可以进行下一步的训练处理。
