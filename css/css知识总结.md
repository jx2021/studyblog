[TOC]

# summary

## 1. 浏览器渲染原理
DOM 树与 CSSOM 树合并后形成渲染树。
渲染树只包含渲染网页所需的节点。
布局计算每个对象的精确位置和大小。
最后一步是绘制，使用最终渲染树将像素渲染到屏幕上。

## 2. css动画的两种做法

### transition
```
where 
<single-transition> = [ none | <single-transition-property> ] || <time> || <easing-function> || <time>

where 
<single-transition-property> = all | <custom-ident>
<easing-function> = linear | <cubic-bezier-timing-function> | <step-timing-function>

where 
<cubic-bezier-timing-function> = ease | ease-in | ease-out | ease-in-out | cubic-bezier([0,1]>, <number>, [0,1]>, <number>)
<step-timing-function> = step-start | step-end | steps(<integer>[, <step-position>]?)

where 
<step-position> = jump-start | jump-end | jump-none | jump-both | start | end
```
* 不是所有属性都能过度
  display: none => block 没法过渡
  一般改成visibility:hidden => visible
### animation
@keyframes
```
@keyframes slidein {
  from {
    transform: translateX(0%);
  }

  to {
    transform: translateX(100%);
  }
}
```

```
@keyframes identifier {
  0% { top: 0; left: 0; }
  30% { top: 50px; }
  68%, 72% { left: 50px; }
  100% { top: 100px; left: 100%; }
}
```

animation: 时长| 过渡方式 | 延迟 | 次数 | 方向 | 填充模式 | 是否暂停 | 动画名；
* 时长：1s或者1000ms
* 过渡方式：跟transition取值一样
* 次数： 3， 2.4
* 方向：reverse | alternate | alternate-reverse
* 填充模式：none | forwards | backwards | both
* 是否暂停： paused | running
* 以上属性都有对应的单独属性
```
<single-animation>#
where 
<single-animation> = <time> || <easing-function> || <time> || <single-animation-iteration-count> || <single-animation-direction> || <single-animation-fill-mode> || <single-animation-play-state> || [ none | <keyframes-name> ]

where 
<easing-function> = linear | <cubic-bezier-timing-function> | <step-timing-function>
<single-animation-iteration-count> = infinite | <number>
<single-animation-direction> = normal | reverse | alternate | alternate-reverse
<single-animation-fill-mode> = none | forwards | backwards | both
<single-animation-play-state> = running | paused
<keyframes-name> = <custom-ident> | <string>

where 
<cubic-bezier-timing-function> = ease | ease-in | ease-out | ease-in-out | cubic-bezier([0,1]>, <number>, [0,1]>, <number>)
<step-timing-function> = step-start | step-end | steps(<integer>[, <step-position>]?)

where 
<step-position> = jump-start | jump-end | jump-none | jump-both | start | end
```