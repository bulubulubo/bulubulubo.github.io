# JavaScript

jQuery库

三大框架：Angular React Vue

ui框架

## 1.介绍

流行的脚本语言

Java、JavaScript

**EXMAScript**标准，到6版

## 2.入门

### 2.1引入

- 对内对外两种写法

  ```javascript
  //内部标签
  <script>
  	//...
  </script>
  
  //外部引入
  //abc.js ...-> test.html
  <script scr="abc.js"></script>
  ```
  
  都在script标签中
  
  一般在body和head中

### 2.2基本语法

- 严格区分大小写

- 浏览器调试

  ```javascript
  //cosole.log(变量)
  //在浏览器控制台中打印变量
  //alert直接弹窗
  ```

### 2.3数据类型

数值，文本，图形，音频，视频

变量用var

js不区分小数和整数

- number

```javascript
123//整数
123.1//浮点数
123e3//科学计数法
-99//负数
NaN  //not a number
Infinity //无穷
```

- 字符串

  ‘abc' 、 "abc"

- 布尔值

  true 、false

- 逻辑运算

  &&、 ||、 |

- 比较运算

  =、== 、**===绝对等于：类型一样，值一样**

  不用==

  注：NaN与所有都不等，只能通过isNaN(NaN)判断

  ​		避免浮点数运算，用误差值无限小替代

  ```javascript
  console.log(NaN===NaN)
  //false原因如上
  
  console.log(1/3) === (1-2/3)
  //false精度损失
  ```

- null和undefined

  null空

  undefined未定义

- 数组

  可以是不同类型，[]表示，无下标越界，报undefined

  ```javascript
  //数组
  var arr=[1,2,3,'hello',null,true];
  //
  new array=(1,2,3,'hello',null,true);
  ```

- 对象

  大括号,属性之间“，”

  ```javascript
  //Person person = new Person(1,2,3,4,5);
  var person={
  	name:"hsd",
  	age:3,
  	tags:['js','java','web','...']
  }
  
  //取值
  person.name
  >>>"hsd"
  person.age
  >>>3
  ```


### 2.4严格审查模式

```javascript
<!--    前提：IEDA支持ES6语法
        ’use strict‘严格审查模式，预防javascript的随意性导致一些问题，必须写在第一行
        局部变量建议let定义-->
<script>
     'use strict';
      let i = 1;
</script>
```

## 3.数据类型具体

### 3.1字符串

1. 正常字符串，使用单引号或双引号包裹

2. 转义字符\

   ```javascript
   \'
   \n
   \t
   \u####   Unicode字符
   \x41     ASCII字符
   ```

3. 多行字符串编写`

   tab上面 esc键下面

4. 模板字符串

   ```javascript
   let name='li';
   let age=3;
   let msg=`你好,${name}`
   ```

5. 字符串长度

   通过下标输出对象属性

6. 字符串不可变

7. 大小写转换

   ```javascript
   //是方法不是属性
   x.toUpperCase()
   x.toLowerCase()
   ```

8. x.indexOf('y')

   返回y在x的第一次出现位置

9. substring

   ```javascript
   [)包头不包尾
   //从第一个字符串截取到最后一个
   x.substring(1)
   //从第一个字符串截取到第三个
   x.substring(1,3)
   ```

### 3.2数组

Array可以包含任意的数据类型

数组：存储数据（如何）

1. 长度

   ```javascript
   arr.length
   ```

   注：长度可赋值，数组大小发生变化，赋值小，元素丢失，赋值大，undefined为空

2. indexOf

   通过元素获得下标索引

   字符串的“1”和数字1不同

3. slice()

   切片，返回新数组，类似于string 中substring

4. push,pop

   栈

5. unshift(),shift()

   压入头部，头部弹出，双端队列

6. sort()排序

7. reverse()反转

8. concat()拼接

   返回新数组，不改变原身

9. 连接符join

   打印拼接数组，使用特定字符串连接

10. 多维数组

### 3.3对象

若干个键值对

```
var 对象名 = {
	属性名： 属性值,
	属性名： 属性值,
	属性名： 属性值
}
```

