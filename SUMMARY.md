# Summary

### [2018.10.26](README.md)

函数修改器

修改器可以用来轻易的改变函数的行为，比如作为函数执行前置条件使用，可以被继承和重写。我们来看一个例子：

![1540540327674](C:\Users\peter\AppData\Roaming\Typora\typora-user-images\1540540327674.png)

这是一个简单的修改器，它要求消息的发送者需要和合约拥有者一致（owner是自己定义的变量，并非全局变量）。首先可以看到require，它可以粗略翻译为java代码里面的

```java
if(msg.sender != owner) { throw Exception; }
```

就是当两个地址不一致时抛出异常。这里，我们简单提一下solidity中的异常机制，在老一点的代码中我们可能看到throw方法，但在最近的版本中已经弃用，主要用到了require和assert，区别在于asser函数只能用于测试内部错误，并检查不变量；require函数用来确保满足输入或合同状态变量的有效条件，或者验证从外部合同的调用返回值。

而下划线*表示了使用函数修改器的函数本体的位置，我们看到’*’在require之后，表示如果有一个函数使用了这个修改器，那么它的代码将在require之后执行。

### [2018.10.27](README.md)

react组件的构造方法 constructor()

constructor(props){

    super(props);
    
    this.state = {
    
    };

}

1 constructor必须用super()初始化this, 可以绑定事件到this

2 如果你在constructor中要使用this.props, 就必须给super加参数, super(props)；

3 无论有没有constructor, render中都可以使用this.props, 默认自带

4 如果组件没有声明constructor, react会默认添加一个空的constructor

5 ES6采用的是先创建父类的实例this（故要先调用 super( )方法），完后再用子类的构造函数修改this