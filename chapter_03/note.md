# 第三章 数据存储

本章主要讨论如下内容：

* 数字的存储
* 其他数据的存储（文本，音频，图像，视频）

## 数据类型

数据在计算机中以不同的形式出现：如数字，文本，音频，视频和图像等。

数据在内部全部都是以**位模式**进行存储的。

## 数字的存储

数字的存储主要分两种：整数存储和实数存储

### 整数存储

整数的存储一般被看作是用小数点固定在整数最右边的二进制数字的方式存储，也就是**定点表示法**。

整数存储方式有三种：

* 无符号表示法：无视这个数字的正负，直接按其二进制存。
  * 一般用于计数或者寻址等不需要负数的场合
* 符号加绝对值表示法：首位用于存储其正负，其他位存这个数的二进制。也就是原码表示法。
* 补码表示法：不同于原码表示法的是，当首位为负（也就是1）的时候，其他位取反再加一。
  * 这个是目前带符号整数的存储方式

### 实数存储

实数使用定点表示法会有很大的局限，举个例子，在存储整数部分较长的数和小数部分较长的数的时候很难保证使用同一种定点表示法能同时在误差较小的情况下存下这两个。于是计算机使用**浮点表示法**来存储实数。

在浮点表示法中，数字的小数点是浮动的，其偏移量由指数决定。这种表示法下需要存这个数字的**符号，指数和定点数**。其实就跟二进制的科学计数法差不多。

为了**规范化**，在计算机中规定任何数字转化为浮点表示法的时候定点数必须是`1.xxx`的形式。这样每个数的二进制浮点表示法的存储就是唯一的，而且计算机在存储的时候也可以不需要存这个数的完整定点数，而只需要存其小数点后的**尾数**即可（因为整数部分都是1）。

于是计算机中的实数的存储主要就分这三个部分：

* 符号位：只有一位，用于表示其值的正负。
* 指数：用于存储该数的位移量，可以看作是整个数字的值将会是`(1.尾数)*（2^指数）`。
  * 指数使用**余码系统**存储。简单的说就是无符号整数+固定的偏移量。假设这个指数有4位，那么其无符号整数的范围就是0～15。如果我们人为定义偏移量为7的话，那么其就可以表示-7～8之间的数字了。这样这个指数就可以存带符号的整数了。
* 尾数：用于存储该数的定点数的小数点后的部分。

#### IEEE标准的浮点数存储

在IEEE标准中，浮点数存储遵循上述规则，并分成单精度和双精度两种。两种存储方式的区别在于指数和尾数的位数。其具体区别如下：

| 参数 | 单精度 | 双精度 |
| :---: | :---: | :---: |
| 内存单元大小（位数） | 32 | 64 |
| 符号大小（位数） | 1 | 1 |
| 指数大小（位数） | 8 | 11 |
| 尾数大小（位数） | 23 | 52 |
| 偏移量（整数） | 127 | 1023 |

#### 浮点数的存储错误

浮点数在存储和计算的时候会遇到的存储相关问题有：

* 上溢：当该数的绝对值足够大的时候就会发生上溢。其表现为指数溢出。
* 下溢：当该数的绝对值足够小的时候就会发生下溢。其表现同样为指数溢出。
* 无法存储零：由于规定定点数必须是`1.xxx`的形式，故这个时候无法存储零。故计算机一般规定当这个数的符号，指数，尾数均为0的时候，这个数就是0。
  * 事实上如果按浮点数存储规则强制解析这个数的时候也会发现这个是该类型能表示的最小（也就是最接近零）的正数。
* 截断错误：当一个实数转换为二进制时的**有效位数**足够多的时候，其在用浮点数存储法的时候在强制转换为`1.xxx`的格式的时候就会出现尾数过长的情况，这个时候由于尾数存储的位数时有限的，故多余的尾数就会被截断掉，这个就是截断错误。这也是浮点数计算会引入误差的原因。

## 文本的存储

文本的存储关键在于**字符的存储**，也就是怎么建立字符和数字的映射关系。简单的讲就是给字符编码。

常见的编码方式有ASCII和Unicode。现在比较常用的是UTF-8变长编码。

## 音频的存储

音频的本质是波形，也可以看作是x轴为时间，y轴为赫兹的一个函数。

但是计算机并不能存储连续的数据，只能将其转化为离散的数据存储下来。

### 采样

将连续函数转化为离散函数的通用方法就是采样。

在这里便是对波形进行**采样**，也就是取出许多个时间点的对应的赫兹存下来。例如说1秒10个采样的话那就是存下第0，0.1，0.2，0.3，0.4，。。。秒时的对应赫兹（也就是y值）。

### 量化

对于每一个采样的数据而言，其大概率会是一个小数点后有很多位的实数。这个时候为了存储方便往往会将其转化为一个**无符号整数**，这就是量化。

### 编码

根据存储格式的不同，其编码的标准也会不同。抛开其数据组织和压缩方式，其区别主要在于**每样本位**和**位率**：

* 每样本位：每一个采样出来的数占多少位。
* 位率：可以简单理解为每秒播放多少数据。假设每秒40000个采样，每样本16位的情况下，位率就是40000\*16=640000b/s=640KB/s

## 图像的存储

图像的存储分位图和矢量图两种。

位图的存储方式就是将其看作`a*b`个像素点堆成的栅格图。其中每个像素点有两种表示颜色的方法：

* 真彩色：也就是RGB值，用24位来表示一个颜色，每种颜色占8位。
* 索引色：相当于将常用颜色拿出来单独编号，并映射到真彩色。这么做是为了减少存储量。

而矢量图更像是定义一些函数来表示这个图的图案。矢量图的一个好处就是不像位图一样存在放大后失真的问题。但麻烦的地方在于数据组织方式比较麻烦，而且矢量图不适合用于存储细节较多的图片（举个例子，现实中的一张照片天知道要用多少个函数才能画出来）。

## 视频的存储

视频的存储分为图像的存储和音频的存储。

后者上面讲过了，前者则是一帧一帧的存储图像。

