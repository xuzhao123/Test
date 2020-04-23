---
title: markdown语法
categories: linux
---

Markdown 是格式化文本的一种语法，具有易写易读的特点。

## 标题

文章的多级标题，采用在行首添加一个或多个#表示。

```md
# 一级标题
## 二级标题
### 三级标题
```

## 粗体 & 斜体

如果**强调**某段文字，可以在它前后加上两个星号。

```md
如果**强调**某段文字，可以在它前后加上两个星号。
```

如果想显示为*斜体*，就在它前后分别加上一根下划线。

```md
如果想显示为*斜体*，就在它前后分别加上一个*。
```

## 链接
如果想添加[超级链接](https://xuzhao123.com/blog)，就采用下面的写法。
[博客](https://xuzhao123.com/blog)

## 图片

插入图片采用下面的语法。

![](https://gw.alipayobjects.com/os/rmsportal/psicBBTYxADJXsiGgLsN.png)

```md
![](https://gw.alipayobjects.com/os/rmsportal/psicBBTYxADJXsiGgLsN.png)
```

默认情况下，图片左对齐。如果想居中显示，设置图片大小，可以使用html。

<div align="center">    
<img src="https://img-blog.csdn.net/20180305105631792?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzU0NTE1NzI=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70" width ="100" height ="100" />
</div>

```md
<div align="center">    
<img src="https://img-blog.csdn.net/20180305105631792?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXFfMzU0NTE1NzI=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70" width ="100" height ="100" />
</div></div>
```

## 列表

如果想将内容显示为一个无序清单，可以采用下面的写法。

- A
- B
- C

```md
- A
- B
- C
```

如果想采用有序清单，可以采用下面的写法。

1. A
2. B
3. C

```md
1. A
2. B
3. C
```

## 引用

引用其他资料，需要在行首加入>号。引用还可以嵌套。

> 哈哈哈哈，我笑了

```md
> 哈哈哈哈，我笑了
```

## 代码嵌入

如果在行内嵌入代码，需要用反引号注明，比如`let x = 1`。

```md
`let x = 1`
```

如果嵌入的是一个代码区块，需要用三个反引号（```）注明区块的开始和结束位置。行首起始的三个反引号后面，还可以加上语言的名称，表示代码区块包含的是何种语言。这样可以实现代码的高亮效果。

```js
let x = 1;
console.log(x);
```

## 删除线

~~这段文字被删除了。~~

```md
~~这段文字被删除了。~~
```

## 上标 & 下标

19^th^

```md
19^th^
```

H~2~0

```md
H~2~0
```

## 文字的高亮

文字可以有==高亮显示==

```md
文字可以有==高亮显示==
```