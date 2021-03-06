title: cocos2d-js 制作 2048
date: 2016-02-22 22:41:33
tags:
---

由于已经长时间没有使用 cocos2d-js 开发，再加上 cocos2d-js 已从当初的 alpha2 迭代到现在的 3.0，许多接口都有颠覆性的改变，要从新熟悉 cocos2d-js 必须自我制作一款简单的游戏作为实践。

### 步骤一：
前期准备工作。（包括：下载 cocos2d-js 源码，准备好 api 文档，准备好教程用例），源码可以从 github 上下载，项目里头包括了相关的 api 文档，同时项目里也拥有了教程用例，前期算是非常的顺利。
    
### 步骤二：
搭建 2048 项目。接住 cocos2d-js 线上的星球大战作为基础，可以搭建出一个基本的游戏框架。删除多余文件，以及资源，可以开始编码开发。
    
### 步骤三：
需求分析。《2048》是一款碎石类游戏，通过合并相同数字的方块，最终组合成 2048。每一次移动同时会随即生成一个 2 或 4 的方块。
    
### 步骤四：
技术预研究。需要生成多个layer层，在每个layer层上配置数字信息。通过键盘控制方块移动。过程中要了解 layer 的生成，文字的生成，坐标世界观，动画播放，键盘事件绑定等。
   
### 步骤五：
逻辑编写。整个工程需要有2个主要类，

* 一个为游戏场景，
* 一个为方块类。
在过程中，首先要渲染出底层最主要的游戏场景。其次，分步骤按逻辑生成带有数字的方块，并根据玩家操作，将方块进行合并。

* 一个对象数组，每项里面记录每个方块的位置，当前是否已经被有方块，以及方块对象。
* 一个适配对象，记录每个数字类型的字体颜色，以及方块背景颜色，方便生成方块。             * 一套生成方块的算法，算法的原则是，在空白处生成2或4的方块。
* 每次移动过程后，记录下全局的所有空白格子，并且随机在这些格子上生成方块。
       * 一套判断移动算法:该算法是一套递归过程，每个方格移动的时候需要判断2种情况：
            * 如果该方向上有其他方块，我要知道该方块最终能移动到的位置。
            * 如果该方向上无其他方块，则将当前方块移动到棋盘边界。
       * 一套检测合并的算法。
             * 每次移动操作过后，遍历全局，开是否有重复的方块出现在同一个格子出，如果有，则移除其中一个方块，并将另外一块方块的数值乘以2。
* 编写键盘回调，这个过程需要找出，键盘上每个键对应的键码，测试后得出，上：38，左：37，下：40，右：39。
    
项目地址：https://github.com/fsiaonma/2048
