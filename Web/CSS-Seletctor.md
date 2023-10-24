
选择器所选择的元素，叫做“选择器的对象”。

# 元素选择器

元素选择器可以选择所有类型的HTML元素。元素选择器也称为标签或类型选择器

```
p {
  color: red;
}
```

# 类选择器

## 选择所有元素的类

在HTML中，标签可以声明class属性，表示该标签是该类的一个实例。我们可以选择某个类让该类具有同一样式。

```html
<!-- 声明了该元素是类my-class的一个实例 -->
<p class="my-class">
```
类选择器以一个句点`.`开头
```css
.my-class{
	color: red;
}
```

## 选择特定元素的类

不同的标签可以声明为同一个类

```html
<h1 class="highlight">Class selectors</h1>
<p class="highlight">
```

有时候我们会需要使用特定元素的类使用某个样式，而不是所有元素。例如我们想选择tag为h1，class为highlight的元素，而不想影响tag为p，class为highlight的元素。

> Grammer
>
> 我们可以指定`标签.class`选择特定标签的类
>
> ```css
> span.highlight {
>  background-color: yellow;
> }
> 
> h1.highlight {
>  background-color: pink;
> }
> ```

## 选择具有多个类的元素

一个元素可以被声明多个类，类名之间使用空格间隔

```css
<div class="notebox danger">
    This note shows danger!
</div>
```

上述的div元素具有两种类型，notebox 和danger

多类型的元素选择器：

```css
/*只有同时具有notebox类和danger类才会受到此规则集的影响。*/
.notebox.danger {
  border-color: red;
  font-weight: bold;
}
```



# ID选择器

在HTML中，可以对HTML元素声明一个唯一的id以区分不同的元素。

```html
<!-- 声明了该元素是类my-class的一个实例 -->
<p id="p1">
```
使用`# id`声明一个id选择器
```
#p1{
	color: red;
}
```

大多数情况下，给一个元素加个类，而不是使用 ID，会更好

# 选择器列表

如果多个选择器对象需要使用相同的样式，可以组建一个选择器列表，选择器之间使用`,`分隔。

```css
/*h1标签和 special类使用相同的样式*/
h1, .special {
  color: blue;
}
```

推荐不同的选择器占不同的行，增加可读性

```css
h1,
.special {
  color: blue;
}

```

> Grammer
>
> 当你使用选择器列表时，如果任何一个选择器无效 (存在语法错误)，那么整条规则都会被忽略
>
> ```css
> /* 类选择器存在语法错误，h1的样式会失效*/
> h1,
> ..special {
> color: blue;
> }
> 
> ```

# 全局选择器

全局选择器，是由一个星号（`*`）代指的，它选中了文档中的所有内容

```css
* {
    margin: 0;
}
```

# 层次选择器

默认情况下，HTML元素将会写在`<body>`中，因此`<body>`是所有元素的根标签。

```html
<body>
<div>  
    <p> Hello,CSS</p>
 </div>
</body>
```

body是div的父标签，div是p的父标签

## 后代选择器

**后代选择器**用于选择某个元素的后代元素，即直接或间接包含在该元素内的所有**子孙元素**。

后代选择器使用空格来分隔两个选择器。

```
element1   element2 {
    /* CSS属性和样式规则 */
}
```

- `element1`祖先元素
- `element2`后代元素

```html
<div class="container">
    <p>这是一个段落</p>
    <ul>
        <li>列表项1</li>
        <li>列表项2</li>
    </ul>
</div>
```

```css
.container li {
    /* 对.container 元素内部的 <li> 元素应用样式 */
    color: blue;
}
```



## 子选择器

子选择器用于选择一个元素的**直接子元素**，而不包括孙子元素或后代元素。子选择器使用 `>` 符号来连接两个选择器。

```css
parent > child {
    /* CSS属性和样式规则 */
}
```

可以使用多个`>`表示标签的层次关系，类似于面向对象中的`.`

```css
parent > child>me {
    /* CSS属性和样式规则 */
}
```

```html
<div class="container">
    <p>这是一个段落</p>
    <ul>
        <li>列表项1</li>
        <li>列表项2</li>
    </ul>
    <div>
            <ul>
            <li>列表项3</li>
            <li>列表项4</li>
        </ul>
    </div>
</div>
```

```css
.container>ul>li {
    /* 对.列表项1，2 应用样式 */
    color: blue;
}
```



## 相邻兄弟选择器

加号（+）是一个选择器组合符号，用于选择紧跟在另一个特定元素后面的元素。

```css
element1 + element2 {
    /* CSS属性和样式规则 */
}
```

- `element1`：这是前一个元素的选择器，它是紧邻的元素。
- `+`：这是相邻兄弟选择器。
- `element2`：这是要选择的紧跟在`element1`后面的元素的选择器。

最终结果会让`element2`使用该样式。`element1`和`element2`必须是紧邻的，具有相同的父标签（互为兄弟），且之间不能存在元素。

```html
    <p>这是一个段落</p>
    <!-- <div>这是一个div</div> -->
    <span>这是一个span<hahaha></span>
```

```
p + span {
    color: red;
}
```

div元素如果存在，该相邻兄弟选择器将不会生效

## 通用兄弟选择器

选择某个元素之后的**所有特定类型的兄弟元素**。通用兄弟选择器使用波浪号 `~` 表示

```css
p~div{
  color: yellow;
}
```

- `element1`: 这是用于选择第一个元素的选择器。
- `~`: 这是通用兄弟选择器。
- `element2`: 这是用于选择第一个元素之后的所有兄弟元素的选择器。

`element1`和`element2`是兄弟元素

```html
    <p>p2</p>
    <div>div1</div>
    <li>hello</li>
    <div>div2</div>
    <p>p1</p>
```

```css
/*选择了与p标签同为兄弟的所有div标签*/
p~div{
  color: yellow;
}
```

# 伪类选择器

伪类选择器（Pseudo-Class Selectors）是CSS选择器的一种，用于选择HTML元素的特定状态或位置，而不仅仅是元素的基本类型或属性。伪类选择器的标志是`:`

`:hover`：选择鼠标悬停在元素上的状态。常用于链接或交互元素。

```css
a:hover {
    color: red;
}
```

:first-child：第一个

```css
/*父类ul中的第一个li*/
ul li : first-child {
    color: red;
}
```

:last-child

```css
/*父类ul中的最后一个li*/
ul li : last-child {
    color: red;
}
```

# 属性选择器

设置带有特定属性或属性值的 HTML 元素的样式。属性选择器在前端中非常常用

## [attribute]

选择带有id属性的所有元素

```css
[id]{
    /* CSS属性和样式规则 */
}
```

## [attribute=value]

选择id=first的所有元素。该等于为绝对等于

`class="first box"`和`class="box"`并不相等

```css
[id="first"]{
    /* CSS属性和样式规则 */
}
```

## [attribute~=value]

选择id包含flower的所有元素

```css
[id~="flower"]{
    /* CSS属性和样式规则 */
}
```

## [attribute|=value]

`|=`用于选择带有特定前缀的value。前缀以`-`分隔

例如下列选择器，选择了带有`lang="en-US"`的标签：

```css
[lang|="en"] {
    /* CSS属性和样式规则 */
}
```

## [attribute^=value]

选择href属性以https开头的所有元素

```css
[href^="https"] {
    /* CSS属性和样式规则 */
}
```

## [attribute$=value]

选择href以`.pdf`接收的使用元素

```css
[href$=".pdf"] {
    /* CSS属性和样式规则 */
}
```

## [attribute*=value]

选择href中带有子串`"hello"`的元素

```css
[href*="hello"] {
    /* CSS属性和样式规则 */
}
```

## 指定具体元素

属性选择器可以指定为某个具体元素的属性选择器

选择href中带有子串`"hello"`的a元素：

```css
a[href*="hello"] {
    /* CSS属性和样式规则 */
}
```

