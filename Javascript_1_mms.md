# JavaScript🎠_1

> **写在前面：🦄**
>
> 第1章是JS里面最最基础的命令与语法 (还没到对象)
>
> 根据B站尚硅谷JS系列视频1-45做的笔记
>
> 网址：[尚硅谷最新版JavaScript基础全套教程完整版(140集实战教学,JS从入门到精通)_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1YW411T7GX?p=1)
>
> 不是所有的都记 选了视频中个人觉得需要记录的
>
> 如果和C++ Python语法一样的话 可能就没有出现在下面的笔记中

## 基本命令🎨

### 写在head里的👸

##### 编码

```js
<meta charset="UTF-8">   <!--没有</meta> -->
```

##### 页面名称

```js
<title>页面名字</title>
```

#### 写在script里的

```js
<script type="text/javascript"> </script>
<!--系统默认type就是"text/javascript" 所以可以不写
    可以有多个script-->
```

##### 弹出框       

```javascript
alert("this is JS")
<!--点击确定后才能执行下面的语句-->
```

```js
var a = prompt("请输入：")
<!--带有一个文本框 返回值为输入值-->
```

##### 向body中输出内容

```javascript
document.write("this is JS")
<!--页面可见-->
```

##### 向控制台输出内容

```html
c = 123 ;
console.log("c= "+c);
<!--F12控制台可见-->
```

### 写在body里的🙆‍♂️

##### 按钮

```js
<button>click me</button> 
<button onclick="alert('是否确定')">click me </button> <!--点击按钮后出现弹出框-->
```

##### 超链接   

```js
<!--不方便维护，不推荐使用 ->属于结构与行为耦合-->
<a href>啥也没有</a>
<a href ="javaScript:;">也是啥也没有</a>
<a href ="javaScript:alert('click we');alert('click again')">注意写语言类型，多行命令要加分号</a>
<a href="123c.cpp" >可以打开文件</a>
<a href="https://www.baidu.com/">可以打开网页</a>
```

## 基本语法🎡

#### 引号

JS里面字符串 单引号和双引号都可 但不要混着用

###### 转义

  \ '表示 '      \ ''表示 ''      \ \表示\    (中间没有空格)

```js
str="我说：\"今天天气真好~\"" //才能打出来我说："今天天气真好~"
```

#### 一些奇怪的数字🌸

##### 无穷大∞

Infinity 当超过number类型的max时

-Infinity 为负无穷

##### 无穷小0

大于0的最小值：Number.MIN_VALUE

##### NaN

- “不是一个数字” 
- 属于number类型
- 算术运算：NaN
- 比较运算：false
- 不和任何值相等，包括它本身
- 用 isNaN() 函数判断是否为NaN

#### 精确度问题

JS的整数运算可以保证精确

但JS进行浮点运算可能不精确

#### 数据类型

检查数据类型：

```js
var a = null;
console.log(typeof a);
```

- ###### 字符串 String

  > 不能这么写：
  >
  > ~~var a ="锄禾日当午~~
  >         ~~汗滴禾下土"~~;
  >
  > 要写就写一行 或者用+号

- ###### 数值 Number

- ###### 布尔 Boolean

- ###### 空值 Null

- ###### 未定义 Undefined

- ###### 对象 Object

##### 强制类型转换🌤

一般指将其他的数据类型转换为String Number Boolean

###### 转换为String

1. +""方法✔

   ```js
   var c = 123 ;
   c = c + "" ;//实际也是调用String()函数
   ```

2. 调用 toString() 方法

   ```js
   var a=123;
   a=a.toString();
   ```

   不影响原来的变量 会以转换的结果返回

   但注意：null与undefined没有toString()方法

   

3. 调用 String() 方法✔

   ```js
   var a = 123;
   a = String(a);
   ```

   不影响原来的变量 会以转换的结果返回

   - null->"null"
   - undefined->"undefined"
   - Number/Boolen->toString()

###### 转换为Number(各种进制)

- -0  *1  /1  + ✔

  ```js
  var a = b = c = d = "123";
  a = a - 0;
  b = b * 1;
  c = c / 1;
  d = + d ;
  ```

  原理和 Number() 一样

  [用+号要注意](#运算符注意事项)❗❗

- 调用 Number() 方法✔

  ```js
  var a = "123.456";
  a=Number(a);
  ```

  - string：

    如果是纯数字->数字

    有非数字的内容->NaN

  - Boolean：1和0

  - Null：0

  - undefined：NaN

    

- 调用 parseInt() parseFloat)方法✔

  ```js
  a = "123.89px567";
  b = parseInt(a);//b=123
  c = parseFloat(a);//c=123.89
  ```

  1. 适用于string类型数字+非数字混杂

  2. 从左开始读，遇到非数字即停止

  3. 第一位就是非数字 ->返回NaN

  4. 对非string使用此方法->先转换为string后操作

     ```js
     //可以用于浮点型->整形
     a = 123.45；
     a = paiseInt(a);//a=123
     ```

     **如果要转换成其他进制**

  *  补充其他进制的知识点：

  > - 2进制的数字->0b开头   (输出会按照十进制输出)
  >
  >   > 但不是所有浏览器都支持
  >
  > - 8进制的数字->0开头   (输出会按照十进制输出）
  >
  > - 16进制的数字->0x开头    (输出会按照十进制输出)

  ```js
  a = "08";//8进制
  a = paiseInt(a,8);//a=10
  ```

###### 转换为Boolean

- ！！方法✔

  ```js
  a = !!a;
  ```

  

- 调用 Boolean() 方法✔

  ```js
  a = "123.456";
  a = Boolean(a);
  ```

  - string：空字符串->false
  - Number：0和NaN->false
  - Null：false
  - undefined：false
  - 对象->true

#### 运算符

比如typeof就是运算符，可以获得一个值的类型

```js
var a = 123;
var result = typeof a;//result="Number"
console.log(typeof result);//输出"string"
```

##### 运算符注意事项🍓

- NaN

  - 算术运算：NaN
  - 比较运算：false

-  只要出现Number，其他都转换为Number再计算

  ​    **注意**：如果第一位是非数字(除null为0) 其他都是NaN 🗽看上一条

  - 除➕加号❗❗

    ```js
    a = "1" + 2 + 3 ;//"123"
    b = 1 + 2 + "3" ;//"33"
    c = +"1";//1 这里没有其他Number啦
    ```

  - 其他算术运算符

    ```js
    a = 100 - "1";//99
    b = 100 * undefined; //NaN
    ```

- 比较运算符

  ```js
  "5"<"11"; // 用Unicode比较 从第一位开始逐位比较 因为都是string类型
  +"5"<"11"; // 即比较5<11
  ```

-  相等运算符

  - ==     !=       弱      先进行转换
  - ===   !==    强

- 条件运算符

  ```js
  true ? alert("yes") : alert("no");//条件表达式?语句1:语句2;
  ```

- 优先级

  ![image-20210731214042388](C:\Users\26368\AppData\Roaming\Typora\typora-user-images\image-20210731214042388.png)

#### if语句

和C++一模一样

```js
var a = 1;
if ( a === 1 ){ alert("yes"); }
else if( a === 2 ) alert("no") ;
else alert("none");
```

#### switch语句

和C++一模一样

```js
switch(num){
    case 1 : alert("是1");break;
    default : alert("不是1");break;
}
switch(true){
    case num ===1  :alert("是1");break;
    default : alert("不是1");break;
}
```

#### while语句

和C++一模一样

```js
while (true) {}
do {} while (true);
```

#### for循环

和C++一模一样

```
for(var a = 0 ; a <= 5; a++) alert(a);
```
