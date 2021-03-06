# Dom事件模型

## 1. Dom事件的级别

DOM级别一共可以分为四个级别：DOM0级、DOM1级、DOM2级和DOM3级。而DOM事件分为3个级别：DOM 0级事件处理，DOM 2级事件处理和DOM 3级事件处理。由于DOM 1级中没有事件的相关内容，所以没有DOM 1级事件。

* 0级是最早的，而且目前所有的浏览器仍支持0级DOM模型。缺点是一个事件的处理程序只能对应一个函数。删除DOM0事件处理程序，只要将对应事件属性置为null即可。

* 在2级模型中可以为特定对象的事件注册多个事件监听。

2级事件的删除

```
removeEventListener("click",function(){},false);
```

* 3级事件的操作方式和2级事件是一样的。DOM3级事件模块在DOM2级事件的基础上重新定义了这些事件，也添加了一些新事件。

## 2. 事件流

DOM事件模型分为捕获和冒泡。一个事件发生后，会在子元素和父元素之间传播（propagation）。这种传播分成三个阶段。

（1）捕获阶段：事件从window对象自上而下向目标节点传播的阶段；

（2）目标阶段：真正的目标节点正在处理事件的阶段；

（3）冒泡阶段：事件从目标节点自下而上向window对象传播的阶段。

DOM事件捕获的具体流程

捕获是从上到下，事件先从window对象，然后再到document（对象），然后是html标签（通过document.documentElement获取html标签），然后是body标签（通过document.body获取body标签），然后按照普通的html结构一层一层往下传，最后到达目标元素。

而事件冒泡的流程刚好是事件捕获的逆过程。

## 3. Event对象的常见应用

1. event.preventDefault()

　　此方法用来阻止默认的事件，比如阻止a标签的跳转。用法：
```
dom.addEventListener('click',function(event){
   event.preventDefault()
},false)
```

2. event.stopPropagation()

　　阻止冒泡；让事件停留在当前dom而不会向上传递，

3. event.stopImmediatePropagation()

　　stopImmediatePropagation()函数用于阻止剩余的事件处理函数的执行，并防止当前事件在DOM树上冒泡。

4. event.target

　　target 事件属性可返回事件的目标节点（触发该事件的节点），如生成事件的元素、文档或窗口。

5. event.currentTarget

　　currentTarget 事件属性返回其监听器触发事件的节点，即当前处理该事件的元素、文档或窗口。

　　在捕获和起泡阶段，该属性是非常有用的，因为在这两个节点，它不同于 target 属性。

　　与event.target的区别: event.currentTarget指向事件所绑定的元素，而event.
　　
## 4. 事件代理(事件委托)

由于事件会在冒泡阶段向上传播到父节点，因此可以把子节点的监听函数定义在父节点上，由父节点的监听函数统一处理多个子元素的事件。这种方法叫做事件的代理（delegation）。

* 优点

1. 减少内存消耗，提高性能
假设有一个列表，列表之中有大量的列表项，我们需要在点击每个列表项的时候响应一个事件。如果给每个列表项一一都绑定一个函数，那对于内存消耗是非常大的，效率上需要消耗很多性能。借助事件代理，我们只需要给父容器ul绑定方法即可，这样不管点击的是哪一个后代元素，都会根据冒泡传播的传递机制，把容器的click行为触发，然后把对应的方法执行，根据事件源，我们可以知道点击的是谁，从而完成不同的事。

2. 动态绑定事件
在很多时候，我们需要通过用户操作动态的增删列表项元素，如果一开始给每个子元素绑定事件，那么在列表发生变化时，就需要重新给新增的元素绑定事件，给即将删去的元素解绑事件，如果用事件代理就会省去很多这样麻烦。


