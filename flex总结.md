---
title: flex总结
categories: css
---

### flex布局原理
* 当父盒子设置为flex布局后，子元素的float，clear，和vertical-align属性将失效。
* 通过给父盒子添加flex属性，来控制子盒子的位置和排列方式。

### flex布局父盒子常见属性

+ flex-direction: 设置主轴的方向
  - row 左到右
  - row-reverse 右到左
  - column 上到下
  - column-reverse 下到上
+ justify-content: 设置主轴上的子元素排列方式
  - flex-start 从头部开始排列
  - flex-end 从尾部开始排列
  - center 居中对齐
  - space-around 平分剩余空间
  - space-between 先两边贴边 再平分剩余空间
+ flex-wrap: 设置了子元素是否换行
  - nowrap 不换行
  - wrap 换行
+ align-content: 设置侧轴上的子元素的排列方式（多行）
  - flex-start 从头部开始排列
  - flex-end 从尾部开始排列
  - center 居中对齐
  - space-around 平分剩余空间
  - space-between 先两边贴边 再平分剩余空间
  - stretch 子元素高度平分父元素高度（默认值）
+ align-items: 设置侧轴上的子元素排列方式（单行）
  - flex-start 从头部开始排列
  - flex-end 从尾部开始排列
  - center 居中对齐
  - stretch 沿着侧轴拉伸，但是子盒子不要给高度
  - baseline 项目的第一行文字的基线对齐
+ flex-flow: 复合属性，相当于设置了flex-direction和flex-wrap

### flex布局子项常见属性
+  flex-grow 定义子项的放大比例，默认是0，即如果存在剩余空间，也不放大
+  flex-shrink 定义子项的缩小比例，默认是1，即如果空间不足，子项将缩小
+  flex-basis 定了再分配多余空间之前，子项占据的主轴空间，默认为auto，即子项的本来大小
+  flex flex-grow,flex-shrink,flex-basis简写
+  align-self 控制子项自己再侧轴的排列方式，默认集成父元素的align-items
+  order 定义子项目的排列顺序，默认是0