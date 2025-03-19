# 11.4 小贴士

## record
于Java16中添加的特性，用来取代之前繁琐的私有字段和配套一大堆get set方法的JavaBean，可以极大的简化代码

## 规范化
IDEA提供了`重新设置文件格式`的功能，用于整理代码，清理无用的import，可以在这里设置快捷键`主菜单 | 代码 | 代码格式设置操作 | 重新设置文件格式…`

## 漏注册
在遇到`Trying to access unbound value: ResourceKey[]`这样的报错时，大概率是漏掉了注册部分。

## 网络包方向
可能注册的时候图个方便，直接注册的双向`playBidirectional`，但是这样在写的时候在遇到发错方向的时候不容易检查出错误，可以单独注册`playToClient`或者`playToServer`
当然，在debug的时候，也可以查看该断点运行时的线程是RenderThread客户端线程还是ServerThread服务端线程

## 题外话
最后，遇到棘手且卡了很久不知道怎么解决的问题的时候，最好可以向有一定经验的开发者求助，可能只是一些新手没有注意到的问题