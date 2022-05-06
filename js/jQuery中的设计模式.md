# jQuery 如何获取元素

jQuery的基本设计思想和主要用法，就是"选择某个网页元素，然后对其进行某种操作"。使用jQuery的第一步，往往就是将一个选择表达式，放进构造函数jQuery()（简写为$），然后得到被选中的元素。

1. 选择表达式可以是CSS选择器：
```
$(document) //选择整个文档对象

$('#myId') //选择ID为myId的网页元素

$('div.myClass') // 选择class为myClass的div元素

$('input[name=first]') // 选择name属性等于first的input元素
```
2. 也可以是jQuery特有的表达式：

```
　　$('a:first') //选择网页中第一个a元素

　　$('tr:odd') //选择表格的奇数行

　　$('#myForm :input') // 选择表单中的input元素

　　$('div:visible') //选择可见的div元素

　　$('div:gt(2)') // 选择所有的div元素，除了前三个

　　$('div:animated') // 选择当前处于动画状态的div元素
```

# jQuery 的链式操作是怎样的

jQuery在最终选中网页元素以后，可以对它进行一系列操作，并且所有操作可以连接在一起，以链条的形式写出来，比如：$('div').find('h3').eq(2).html('Hello'); 它的原理在于每一步的jQuery操作，返回的都是一个jQuery对象，所以不同操作可以连在一起。jQuery还提供了.end()方法，使得结果集可以后退一步。

# jQuery 如何创建元素

1. 复制元素使用.clone()。

2. 删除元素使用.remove()和.detach()。两者的区别在于，前者不保留被删除元素的事件，后者保留，有利于重新插入文档时使用。

3. 清空元素内容（但是不删除该元素）使用.empty()。

4. 创建新元素的方法非常简单，只要把新元素直接传入jQuery的构造函数就行了：
```
　$('<p>Hello</p>');
　$('<li class="new">new list item</li>');
　$('ul').append('<li>list item</li>');
```

# jQuery 如何移动元素

jQuery提供两组方法，来操作元素在网页中的位置移动。一组方法是直接移动该元素，另一组方法是移动其他元素，使得目标元素达到我们想要的位置。

假定我们选中了一个div元素，需要把它移动到p元素后面。

第一种方法是使用.insertAfter()，把div元素移动p元素后面：
```
$('div').insertAfter($('p'));
```
第二种方法是使用.after()，把p元素加到div元素前面：
```
$('p').after($('div'));
```

使用这种模式的操作方法，一共有四对：
```
　　.insertAfter()和.after()：在现存元素的外部，从后面插入元素
　　.insertBefore()和.before()：在现存元素的外部，从前面插入元素
　　.appendTo()和.append()：在现存元素的内部，从后面插入元素
　　.prependTo()和.prepend()：在现存元素的内部，从前面插入元素
```

# jQuery 如何修改元素的属性

```
$div.text(?) 读写文本内容
$div.html(?) 读写 HTML 内容
$div.attr('title', ?) //1. 可以写两个参数:属性,属性值; 2. 只写了一个参数,获取该元素的这个属性的值
$div.css({color: 'red'}) 读写 style
$div.addClass('blue')
$div.on('click', fn) 
$div.off('click', fn)

```