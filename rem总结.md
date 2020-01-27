---
title: rem总结
categories: css
---

### rem 单位

rem是一个相对单位，类似于em，rem的基准是相对于html元素的字体大小。

rem的优点就是可以通过修改html里面的文字大小改变页面中元素的大小可以整体控制。

### 媒体查询

媒体查询可以根据不同的屏幕尺寸改变不同的样式

```css
@media mediatype and|not|only (media feature) {
    css-code;
}
```

mediatype: all, print, screen
media feature: width, min-width(>=), max-width(<=)

* 媒体查询引入资源

```html
<link rel="stylesheet" media="mediatype and|not|only (media feature)" href="style.css">
```

### rem适配方案

#### rem + 媒体查询 + sass/less

动态设置html标签font-size大小
例如：
    1. 假设设计稿是750px，把页面分成15等份。
    2. html字体在750时， 字体大小设置为 750/15 = 50px
    3. html字体在320时， 字体大小设置为 320/15 = 21.33px
    4. 100\*100像素的元素，就设置为2rem\*2rem
    5. 那么在320屏幕下，就变成了2*21.33 = 42.66px大小
    6. 这样就实现了再不同屏幕下，大小自动适配的方案v

```css
/* 以视觉稿750px，划分15等分为例 */

html{
    font-size: 50px;
}

@media screen and (min-width: 320px) {
    html {
        font-size: 21.33px;
    }
}

@media screen and (min-width: 750px) {
    html {
        font-size: 50px;
    }
}
/* 把所有关心的尺寸都罗列出来 */
```

#### rem + flexible.js

flexianle.js 把页面分成了10等分，然后根据页面宽度，通过js动态的设置html的font-size。
