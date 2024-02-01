# 2.1 啥都没有的模组
## 最后一个参数的调整
还记得在[设置章节](../build-environment/settings.md)中我们有一个参数没有设置嘛，也就是`mod_group_id`。

我们需要将这个参数的值改为我们的Mod所在的包名，如果你不理解的话，可以理解为我们Mod所在的文件夹路径。

那么，在我们的项目中，我们将这个值改为`moe.gensoukyo.thirst`。

也就是说，我们的Mod的所有相关的源代码文件都在`src/main/java/moe/gensoukyo/thirst`这个文件夹下。
## 入口
如果你学过Java，你应该知道，对于一个程序，应当有一个入口，那个入口看起来长这样：

```java
public class Main {
    public static void main(String[] args) {
        // ...
    }
}
```

如果没学过，你也可以将它简单理解为“一个程序开始的地方”。

很遗憾，在模组开发中你找不到这样的入口。

但是很明显，我们需要告诉Forge，我们的Mod的入口在哪里，否则它凭什么能够识别到我们的Mod呢？

那么，我们来创建一个入口类吧。哦对了，你下载的MDK里面有一个`ExampleMod`，你可以作为参考，不过我们在这里就给它删掉啦，毕竟它也只是个示例而已。

我们在`src/main/java/moe/gensoukyo/thirst`下创建一个名为`Thirst`的类，然后我们需要告诉Forge，我们的Mod的入口在这里，写法就像这样：

```java
@Mod("thirst")
public class Thirst {
    // ...
}
```

这样就好啦，我们的Mod的入口就是`Thirst`这个类啦。

然后我们再做点别的什么操作，比如说我们为我们的Mod添加一个`logger`，让我们可以在控制台看到我们的Mod的一些信息。

另外，"thirst"作为我们的Mod的ID，我们肯定会用到它很多次的，所以我们可以将它定义为一个常量，这样我们就不用每次都写一遍了。

最后，这个什么都没有的Mod就长这样：

```java
@Mod(Thirst.MODID)
public class Thirst {
    public static final String MODID = "thirst";
    private static final Logger LOGGER = LogUtils.getLogger();
}

```

如果没有学过Java的话，建议去学点入门的内容，我会在遇到的时候简单讲解下这里面的内容，但是不会讲得很详细。

## 代码讲解
### 注解
在上面的代码中，我们使用了一个注解，也就是`@Mod`，这个注解可以简单理解为对我们的类的一个说明，这个说明会被编译器读取，然后做一些事情。

在这里，`@Mod`注解的作用是告诉Forge，我们的Mod的入口在哪里，也就是我们的Mod的主类。

### 类
在上面的代码中，我们创建了一个类，也就是`Thirst`，这个类是我们的Mod的主类，也就是我们的Mod的入口。

我们在之后会大量应用到类这一个概念，你需要知道的是，类就像一个包装盒，里面可以有很多东西，比如说变量、方法等等，我们在编写代码的时候可以通过类来访问这些东西。

### 变量
在上面的代码中，我们创建了两个变量，一个是`MODID`，一个是`LOGGER`。

变量就是类这个包装盒中的一种物件，它可以存储一些数据，比如说数字、字符串等等。

变量的创建格式是`关键字 类型 变量名`，比如说`public static final String MODID`，这里的`public`、`static`、`final`都是关键字，`String`代表了变量的类型，`MODID`是变量名。

变量的类型有很多种，这里我们用到的是字符串类型，也就是`String`，字符串类型的变量可以存储一串字符，比如说`"thirst"`。

这个类型自然也可以使用我们自己创建的类。

### 对象
在使用类创建所谓的变量，我们称它为对象。

### 关键字
在上面的代码中，我们使用了一些关键字，比如说`public`、`static`、`final`、`private`等等。

- `public`代表这个变量是公开的，其他类可以访问这个变量。
- `static`代表这个变量是静态的，这个变量不属于某个对象，而是属于类，我们可以通过类来访问这个变量。
- `final`代表这个变量是不可变的，我们不能修改这个变量的值。
- `private`代表这个变量是私有的，其他类不能访问这个变量。