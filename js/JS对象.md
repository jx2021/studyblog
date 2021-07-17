# JS对象

## 声明对象的两种语法

let obj = { 'name': 'xxx', 'age': 17}
let obj = new Object({ 'name': 'xxx', 'age': 17})

* Object.keys(obj)可以得到obj的所有key

## 如何删除对象的属性

* 两种方式
  delete obj.xxx
  delete obj['xxx']

* 请区分「属性值为 undefined」和「不含属性名」

  不含属性名   'xxx' in obj === false
  
  含有属性名，但是值为 undefined  'xxx' in obj && obj.xxx === undefined
  
  注意 obj.xxx === undefined  不能断定 'xxx' 是否为 obj 的属性

## 如何查看对象的属性

* 查看自身所有属性

  Object.values(obj)
  
  Object.keys(obj)
  
  Object.entries(obj)
  
* 查看自身+共有属性

  console.dir(obj)
  
  或者自己依次用 Object.keys 打印出 obj.__proto__

* 判断一个属性是自身的还是共有的

  obj.hasOwnProperty('toString')

* 查看属性
  
    中括号语法：obj['key'] 

    点语法：obj.key


## 如何修改或增加对象的属性

* 删

delete obj['name']

'name' in obj // false

obj.hasOwnProperty('name')  // false

* 查

Object.keys(obj)

console.dir(obj)

obj['name']

obj.name // 记住这里的 name 是字符串

obj[name]  // 记住这里的 name 是变量

* 改

改自身 obj['name'] = 'jack'

批量改自身 Object.assign(obj, {age:18, ...})

改共有属性 obj.__proto__['toString'] = 'xxx'

改共有属性 Object.prototype['toString'] = 'xxx'

改原型 obj.__proto__ = common

改原型 let obj = Object.create(common)

注：所有 __proto__ 代码都是强烈不推荐写的

* 增

基本同上：已有属性则改；没有属性则增。


## 'name' in obj和obj.hasOwnProperty('name') 的区别

'name' in obj 判断该属性名是否为obj的属性

obj.hasOwnProperty('name') 判断该属性名是否为obj自身的属性

