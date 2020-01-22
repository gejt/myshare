---
layout: post
title:  Markdown基础知识
author: GEJT
image: assets/images/avatar.jpg
category: Markdown
tags: [markdown]
dateTime: 2019年12月26日
excerpt: 本文介绍了Markdown语法基础知识，能让我们快速上手markdown,编写自己的文章。
permalink: /markdown/01
---
Markdown 是一种方便记忆、书写的纯文本标记语言，用户可以使用这些标记符号以最小的输入代价生成极富表现力的文档：譬如您正在阅读的这份文档。它使用简单的符号标记不同的标题，分割不同的段落，**粗体** 或者 *斜体* 某些文字，更棒的是，它还可以

### 1. 标题

示例：

```
# 这是一级标题
## 这是二级标题
### 这是三级标题
#### 这是四级标题
##### 这是五级标题
###### 这是六级标题
```

效果如下：

# 这是一级标题
## 这是二级标题
### 这是三级标题
#### 这是四级标题
##### 这是五级标题
###### 这是六级标题

### 2. 字体

```
**这是加粗的文字**
*这是倾斜的文字*`
***这是斜体加粗的文字***
~~这是加删除线的文字~~
```

效果如下：

**这是加粗的文字**
*这是倾斜的文字*`
***这是斜体加粗的文字***
~~这是加删除线的文字~~

### 3. 引用

示例：

```
>这是引用的内容
>>这是引用的内容
>>>>>>>>>>这是引用的内容
```

效果如下：
>这是引用的内容
>>这是引用的内容
>>>>>>>>>>这是引用的内容

### 4. 分割线

示例：

```
---
----
***
*****
```

效果如下：

---
----
***
*****

### 5. 图片

示例：

```
![图片alt](图片地址 ''图片title'')

图片alt就是显示在图片下面的文字，相当于对图片内容的解释。
图片title是图片的标题，当鼠标移到图片上时显示的内容。title可加可不加

![blockchain](https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/
u=702257389,1274025419&fm=27&gp=0.jpg "区块链")
```


效果如下：

![blockchain](https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/
u=702257389,1274025419&fm=27&gp=0.jpg "区块链")

### 6. 超链接

示例：

```
[超链接名](超链接地址 "超链接title")
title可加可不加

[简书](http://jianshu.com)
[百度](http://baidu.com)
```

效果如下：

[简书](http://jianshu.com)
[百度](http://baidu.com)

### 7. 列表


示例：

```
无序列表用 - + * 任何一种都可以
- 列表内容
+ 列表内容
* 列表内容

注意：- + * 跟内容之间都要有一个空格
有序列表

1. 列表内容
2. 列表内容
3. 列表内容

注意：序号跟内容之间要有空格
```

效果如下：

- 列表内容
+ 列表内容
* 列表内容

1. 列表内容
2. 列表内容
3. 列表内容

### 8. 表格

示例：

```
表头|表头|表头
---|:--:|---:
内容|内容|内容
内容|内容|内容

第二行分割表头和内容。
- 有一个就行，为了对齐，多加了几个
文字默认居左
-两边加：表示文字居中
-右边加：表示文字居右
注：原生的语法两边都要用 | 包起来。此处省略

姓名|技能|排行
--|:--:|--:
刘备|哭|大哥
关羽|打|二哥
张飞|骂|三弟
```

效果如下：

姓名|技能|排行
--|:--:|--:
刘备|哭|大哥
关羽|打|二哥
张飞|骂|三弟

### 9. 代码

示例：

<pre>

 `代码内容`

 ```
  代码...
  代码...
  代码...
```
</pre>

效果如下：

`代码内容`
 
```
  代码...
  代码...
  代码...
```




