# 第十八章 人工智能

本章主要介绍人工智能的入门知识

> 本章知识较为入门且大部分知识并不是目前主流人工智能的知识

## 人工智能简介

人工智能是对程序系统的研究，该程序系统在一定程度上能模仿人类的活动，如感知、思考、学习和反应。

用于验证一个机器是否具有只能的方法是**图灵测试**，也就是由人同时向另一个人和AI提出若干问题，人事先不知道对面哪个是人哪个是AI，然后如果这个提问的人从回答中分不出来哪个是人哪个是AI的话，就说明这个AI具有智能，也就是通过了图灵测试。

### 智能体

智能体分为两大类：

* 软件智能体：指的是能够协助人类在计算机上工作的程序，例如说自动垃圾邮件分类程序。
* 硬件智能体：指的是物理层面上能够完成某些任务的硬件体，例如说机器人。

## 知识表示

在计算机中有4种常见的知识表示方法：

* 语义网
* 框架
* 谓词逻辑
* 基于规则的系统

### 语义网

将实体作为点，实体间的关系作为边，组成的有向图被称为语义网。

例如【狗属于动物】就可以看作是两个点（狗，动物）和一条边（狗指向动物，边值为【属于】）

### 框架

不同于语义网，框架将每个实体看作是一个对象，其原本作为语义网的边则变成对象的属性（在这里称为槽）

例如【狗属于动物】就可以看作是【狗】这个对象中包含一个属性为超类的槽，其值为【动物】

### 谓词逻辑

简单的讲就是将表述知识的句子按谓词关系切分逻辑，并用命题逻辑的方式进行存储。

这样的好处是可以借助说明式模式语言（例如PROLOG）进行逻辑推理。

#### 命题逻辑

命题逻辑有五种运算符：与，或，非，如果...那么（当前仅当前提为T结论为F时为F，否则为T），当且仅当（反的异或）。

于是利用命题逻辑的运算符就可以将命题语句翻译成逻辑表达式，便可以进行逻辑推理等操作。

#### 谓词逻辑

谓词逻辑将带谓词的语句变成函数，然后将其当做命题处理。

例如说【A是B的父亲】就可以变成【父亲\(A, B\)】

### 基于规则的系统

基于规则的系统由三部分组成：

* 知识库：存放规则，这些规则能从给定的事实中得出结论
* 事实库：存放事实用于推理
* 解释器：负责推理

其推理模式有两种：

* 正向推理：通过事实库中已有的事实和知识库的规则进行推理，推理得出的事实放入事实库中。
* 反向推理：利用外部给定的事实倒推其是否成立（也就是在知识库的规则逆向之后能否最终指向事实库中的事实）。

## 专家系统

专家系统是使用上面讲过的知识表示方法，构建一个包含某个领域的知识的系统。

但其知识系统的构建十分困难，难点就在于如何从真实的专家身上抽取知识。

其体系结构包括如下部分：

* 用户：使用专家系统的个体
* 用户界面：与用户交互的系统
* 推理机：通过知识库和事实库进行推理
* 知识库：存储知识
* 事实库：存储事实
* 解释系统：非必须，用于解释推理机得出的结论的合理性
* 知识编辑器：非必须，用于编辑知识

## 感知

人工智能也有感知外部世界的信息并学习/处理的能力。这里仅讨论图像处理和语言理解。

图像处理包括以下几个步骤：

* 边缘探测
* 分段
* 查找深度
* 查找方向
* 对象识别

语言理解包括以下几个步骤：

* 语音识别
* 语法分析
* 语义分析
* 语用分析

## 搜索

人工智能可以通过对某个问题的所有可能的解进行搜索来得到正确的解。

搜索包括DFS、BFS、启发式搜索

## 神经网络

借助仿生学的理念，我们可以通过构建类似生物的神经网络系统来让程序也有自己的神经网络，并依靠神经网络进行学习。

神经网络由许多感知器组成，感知器接收多个输入，并产生一个0或1的输出。

其本质是一个可以改变激活函数的逻辑回归。

