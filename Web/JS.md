# 基础语法

## script

script标签具有如下属性

- type 脚本中属于什么文本，默认值为text/javascript

Javascript可以被嵌入到网页中的任何位置。但是根据W3C标准，script标签应该放在`<body>`或`<head>`标签

内，且放置在最后。

JavaScript注释和Java相同。

分号作为每条语句的结尾

对象：`{ }`

数组：`[ ]`

## 输出

- 浏览器警告信息

```js
window.alert("This is a msg")
```
- 输出信息到浏览器控制台终端

```js
console.log("This is a msg")
```
- 写入信息至指定HTML元素内部

```js
<p id="demo">Here</p>
//将在demo元素中输出7
<script>
document.getElementById("demo").innerHTML = 6+1;
</script>
```

> 7
- 直接在HTML中页面中输出信息
```js
<script>
document.write("hello world");
</script>
```

## 输入

```js
    <script>
        let name=prompt("请输入姓名")
        document.write(name)
    </script>
```



# 变量

## 声明变量

变量遵守小驼峰：userName

### 声明单个变量

```js
let  name="zhangsan"
```

声明变量之后，在没有初始化之前，它的初始值为`undefined`

同Java一样JavaScript 中不能使用连字符。它是为减法预留的。

JavaScript 使用 *Unicode* 字符集。

### 声明多个变量

```js
let  person = "Bill Gates", carName = "porsche", price = 15000;
```

## var与let

var和let都可以声明变量，但是var存在各种缺陷：

- 可以先使用，在声明

  ```js
  carName='byd'
  console.log(carName)
  var carName
  ```

- 没有块级作用域

- var可以重复声明变量

  ```js
  var name='byd'
  var name='tesla'
  ```

  > 因此声明变量建议都使用let，他是为代替var而生的

## 作用域（Scope）

### 全局作用域

*全局*（在函数之外）声明的变量拥有*全局作用域*。

```js
var carName = "byd";

// 此处的代码可以使用 byd

function myFunction() {
  // 此处的代码也可以使用 byd
}
```

### 函数作用域

在函数内声明的变量只在函数内有效

```js
// 此处的代码不可以使用 carName

function myFunction() {
  var carName = "byd";
  // code here CAN use carName
}

// 此处的代码不可以使用 carName
```

### 块作用域（ES6）

function后的作用域为函数作用域，除此之外带有`{ }`的都属于块作用域：if(){}、for(){}、对象{} 

通过 `var` 关键词声明的变量没有块作用域。在块 `{ }` 内使用`var`声明的变量可以从块之外进行访问【没有块作用域】。

```js
var i = 7;
for (var i = 0; i < 10; i++) {
  // statement
}
// 此处，i 为 10
```

要使用**块作用域**，需要使用`let`声明。`let`声明的变量在块外无法使用。因此推荐所有变量都使用`let`声明。

```js
let i = 7;
for (let i = 0; i < 10; i++) {
  // statement
}
// 此处 i 为 7
```

## const

通过 `const` 定义的变量与 `let` 变量类似，但不能重新赋值。 `const` 变量必须在声明时赋值

```js
const PI = 3.14159265359;
```

可以更改常量对象的属性

```js
const car = {type:"porsche", model:"911", color:"Black"};

// 您可以更改属性：
car.color = "White";
```

无法重新为常量对象赋值，数组类似

```js
const car = {type:"porsche", model:"911", color:"Black"};
car = {type:"Volvo", model:"XC60", color:"White"};    // ERROR
```



# 数据类型

## 数组

```js
let arr =[1,2,3]
```

[1,2,3]为数组字面量

```js
console.log(arr[1])
```



## Number

```js
let num1 =100;
let num2=12.3;
```



## String

使用单引号或双引号或反引号，推荐使用单引号

支持使用`+`进行字符串拼接

```js
let str='hello'
```

```js
let str2=`hello world`
```

```js
//不使用相同的字符串符号造成误解即可
let name ='我是"dddd"对吧'
```

### 模板字符串

模板字符串使用反引号，使用`${变量}`占位。模板字符串简化了字符串的拼接

```js
document.write(`大家好，我叫${name}，今年${age}岁`)
```

模板字符串中可以进行换行输入，

```js
document.write(`
<p>
    this is html
    </p>
`)
```

## boolean

true/false

## undefined

变量只声明不赋值时，变量的默认值为**undefined**

undefined的应用在于检查变量是否为undefined，进而判断用户是否有数据传递过来 



## object

undefined表示没有赋值。null表示赋值了，但是内容为空

```js
let name =null
```

应用场景：把null作为尚未创建的对象的初始化值，如果不使用null初始化，则变量变为undefined了

## typeof

typeof关键字可以得到某个变量的类型，输出为字符串

```js
typeof '100px'
//输出结果：'string'
```

## 类型转换

**表单**中的值默认都是String，需要使用类型转换进行数据处理

### 隐式转换

`+`两边只要一边是字符串，会把另外一个也转成字符串（拼接）

其他算术运算符，会把数据转成Number（算术运算）

```js
'10'+12//1012
10-'10'//0
```

在字符串前加上`+`可以转为数字`+10`

```js
+'10'+10//20
```

### 显式转换

- `Number(value)`

  ```js
  let num='10'
  Number(num)
  ```

- `parseInt(value)`

  转value为整数

  ```js
  parseInt("10.12")//10
  ```

- `parseFloat（value）`

  转为浮点

  ```js
  parseFloat('10.12')//10.12
  ```

  > **compare**
  >
  > ```js
  > parseFloat('100px')//100
  > Number('10.12abc')//NaN
  > parseInt('12px')//12
  > ```
  >
  > Number对于value只能是数字型字符串
  >
  > parse可以识别数字开头的字符串，其最大的应用场景就是去除单位：100px

- `String(value)`

  ```js
  String(age)
  ```

- `toString`

  ```js
  age.toString()
  ```

  

## 逻辑





```js
if (condition)
	statements
```



