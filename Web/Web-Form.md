# Attribution

## action

规定了当提交表单时向**何处发送**表单的数据，一般值为URL。如果不指定会提交到当前页面

## method

规定了发送表单数据的方式

- GET

  GET是method的默认值，在URL后面拼接表单数据，URL长度有限制，GET发送不了太多的表单数据。

  在URL中使用?和服务地址分隔

  ```
  www.baidu.com/log.html?username=Sam&age=12
  ```


- POST

  POST安全性更好，表单参数不会直接暴露在URL中，而是在请求体中。POST发送的参数大小没有限制

  



# form item

## input

input有3个属性：

> type
>
> 不同的`type`属性有不同的输入形式的输入框

> name
>
> `name`属性用于指定表单**字段的名称**。这个名称在提交表单时与输入字段的值一起发送到服务器，以便服务器能够识别和处理这些值。
> name=value

> value
>
> name字段对应的值

- text 单行普通文本，value为输入的文本

- password 密码，value为输入的文本

- radio 单选框

  ```html
      <form method="get" action="">
          性别：
          <input type="radio" name="sex" value="1">男
          <input type="radio" name="sex" value="0">女
      </form>
  ```

  > example:
  >
  >  <form>
  >      <div>
  >          性别：
  >         <input type="radio" name="sex">男
  >         <input type="radio" name="sex">女
  >      </div>
  >  </form>

- checkbox 复选框

  ```html
          <div>
              <input type="checkbox" name="code" value="java">java 
              <input type="checkbox" name="code" value="golang">golang 
              <input type="checkbox" name="code" value="python">python 
          </div>
  ```

  > example:
  >          <div>
              <input type="checkbox" name="code" value="java">java 
              <input type="checkbox" name="code" value="golang">golang 
              <input type="checkbox" name="code" value="python">python 
          </div>
  
- file文件
  > accept：设置上传文件允许的格式
  >
  > ```
  > <input type="file" accept=".pdf, .doc">
  
  
  > example:
  >
          <div>
              <input type="file" name="userfile" accept=".pdf, .doc" > 
          </div>

- date/time/datetime-local 日期/时间/日期时间

  ```html
          <div>
              <input type="time" name="time">
              <input type="date" name="date">
              <input type="datetime-local" name="time_data">
          </div>
  ```

  > example
  >
  >         <div>
  >             <input type="time" name="time">
  >             <input type="date" name="date">
  >             <input type="datetime-local" name="time_data">
  >         </div>

- number 数字输入框

  ```html
          <div>
              您的学号：<input type="number" name="id">
          </div>
  ```

  
  
- email 邮件输入框

- hidden 隐藏域

  该表单项不会渲染，提交表单时会传递id=2022413999

  ```
  <input type="hidden" name="id" value="2022413999">
  ```

- submit 提交

  点击后，表单域中的所有数据将会提交至action指定的地址

  ```
          <input type="submit" value="提交">
  ```

- reset 重置

  需要定义JS逻辑

  ```
          <input type="reset" value="自定义按钮2">
  ```

- button 按钮

  需要定义JS逻辑
  
  ```
          <input type="button" value="自定义按钮1">
  ```
  
  

## select

下拉表单项。option子标签表示每个选项，每个option有value属性表示该选项的值。

```html
        <div>
            <select>
                <option value="Beijing">北京</option>
                <option value="Tianjing">天津</option>
                <option value="Sanming">上海</option>
            </select>
        </div>
```

## textarea

文本框表单项 name为 key 文本框内的内容为value。cols和rows指定了文本框的大小Web



```html
<textarea name="自我介绍" cols="30" rows="10">请输入您的自我介绍</textarea>
```

## label

label标签通常绑定一个表单元素，当点击label内的本文时，浏览器会自动跳转至对应的表单元素上

```html
<label for="sex_input">男</label>
<input type="radio" name="sex" id="sex_input"/> 
```

属性for与表单元素的id属性相同
