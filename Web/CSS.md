# Start

Cascading Stylesheets 层叠样式表

## 引入CSS

### 内部样式表

不使用外部css文件，将CSS声明在HTML的head处。使用`<style>`声明

```css
<head>    
	<style>
        h1{
            color: #000;
        }
    </style>
</head>
```

### 外部样式表

将CSS保存在.css文件中，在HTML中使用`<link>`引用

```html
<head>
    <link rel="stylesheet" href="../CSS/style.css">
    <title>CSS</title>
</head>
```

- href：CSS的路径
- rel：stylesheet（样式表）

### 行内样式表

仅影响当前的元素，在HTML元素中声明style属性

```html
    <div style="color: blue;">
        hello
    </div>
```

### CSS2风格

在head处使用`@import`引入CSS文件。但已经被CSS3的link所取代

```html
<head>
	<style>
        @import url("../CSS/style.css");
    </style>
</head>
```



## Hot key

VScode中输入.red将创建该类型的div标签

```
.red
```

```html
<div class= "red"> </div>
```



# CSS规则集

除了选择器部分，每个规则集都应该在`{}`中

```css
p {
  color: red;
}
```

<img src="https://developer.mozilla.org/zh-CN/docs/Learn/Getting_started_with_the_web/CSS_basics/css-declaration-small.png" alt="CSS p 声明，其中 color 为 red" style="zoom:33%;" />

- Selector选择器

  选择需要添加样式的HTML元素的名称

- Property

  color就是一个property（属性）

- Value

  property具有多个value

- Declaration 声明

  例如`color:red;`，用来添加样式元素的属性。不同的声明之间需要使用`;`分隔

> 选择多个元素，元素之间使用`,`分隔
>
> ```css
> p,
> li,
> h1 {
>   color: red;
> }
> 
> ```


# 层叠样式

## 选择器的精确性

```css
.notebox {
  border-color: blue;
  font-weight: bold;
}
.notebox.danger {
  border-color: red;
  font-weight: bold;
}
```

```html
<div class="notebox">
    This is an informational note.
</div>

<div class="notebox danger">
    This note shows danger!
</div>

```

class="notebox danger"的div将会生效`.notebox.danger`选择器的风格，虽然存在notebox类选择器，但是`.notebox.danger`选择器更加**精确**，假设不存在`.notebox.danger`选择器，样式将会采用`notebox`选择器的风格

## 多个类的标签的应用

```css
.red{
    background-color: red;
    height: 150px;
    width: 100px;
}
.green{
    background-color: green;
    height: 150px;
    width: 100px;
}
```

```
    <div class="red">
RED
    </div>
    <div class="green">
GREEN
    </div>
```

当样式具有相同的声明，我们可以将其提取成一个单独的类选择器（封装为父类）。这样设计有利于修改

```css
.box{
  height: 150px;
  width: 100px;
}
.red{
    background-color: red;

}
.green{
    background-color: green;
}
```

```html
    <div class="red box">
RED
    </div>
    <div class="green box">
GREEN
    </div>
```

因此在设计标签时，可以遵从面向接口的思想。

