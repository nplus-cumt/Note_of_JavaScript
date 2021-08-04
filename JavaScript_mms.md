# JavaScript🎠

> **写在前面🦄**
>
> 完结撒花~
>
> 根据 [B站尚硅谷JavaScript基础](https://www.bilibili.com/video/BV1YW411T7GX?p=1) 做的笔记



## 基本命令🎨

### 写在head里的👸

##### 	编码

```css
<meta charset="UTF-8">   <!--没有</meta> -->
```

##### 	页面名称

```css
<title>页面名字</title>
```



#### 写在script里的

```css
<script type="text/javascript"> </script>
<!--系统默认type就是"text/javascript" 所以可以不写
    可以有多个script-->
```

##### 	弹出框       

```javascript
alert("this is JS")
<!--点击确定后才能执行下面的语句-->
```

```js
var a = prompt("请输入：")
<!--带有一个文本框 返回值为输入值-->
```

##### 	向body中输出内容

```javascript
document.write("this is JS")
<!--页面可见-->
```

##### 	向控制台输出内容

```html
c = 123 ;
console.log("c= "+c);
<!--F12控制台可见-->
```



### 写在body里的👔

##### 	按钮

```css
<button>click me</button> 
<button onclick="alert('是否确定')">click me </button> <!--点击按钮后出现弹出框-->
```

##### 	超链接   

```css
<!--不方便维护，不推荐使用 ->属于结构与行为耦合--><a href>啥也没有</a><a href ="javaScript:;">也是啥也没有</a><a href ="javaScript:alert('click we');alert('click again')">注意写语言类型，多行命令要加分号</a><a href="123c.cpp" >可以打开文件</a><a href="https://www.baidu.com/">可以打开网页</a>
```





## 基本语法🎡

### 引号

​		JS里面字符串 单引号和双引号都可 但不要混着用

#### 转义

 	\ '表示 '      \ ''表示 ''      \ \表示\    (中间没有空格)

```js
str = "我说：\"今天天气真好~\"" //才能打出来我说："今天天气真好~"
```



### 一些奇怪的数字🌸

#### 无穷大∞

​	Infinity 当超过number类型的max时

​	-Infinity 为负无穷

#### 无穷小0

​	大于0的最小值：Number.MIN_VALUE

#### NaN

- “不是一个数字” 
- 属于number类型
- 算术运算：NaN
- 比较运算：false
- 不和任何值相等，包括它本身
- 用 isNaN() 函数判断是否为NaN



### 精确度问题

​	JS的整数运算可以保证精确

​	但JS进行浮点运算可能不精确



### 数据类型

​	检查数据类型：

```js
var a = null;console.log(typeof a);
```

- ###### 数值 Number

- ###### 布尔 Boolean

- ###### 空值 Null

- ###### 未定义 Undefined

- ###### 对象 Object (详细见下一章)

- ###### 字符串 String



#### String

在底层是以字符数组的形式保存的"hay" -> ["h","a","y"]

> 不能这么写：
>
> var a ="锄禾日当午
>   汗滴禾下土";
>
> 要写就写一行 或者用+号

##### length属性 

是属性，所以调用的时候不需要加 ( )

```js
var ss = "string";var len = ss.length;
```

##### charAt( )

根据索引，返回字符串中指定位置的字符

```js
var ss = "string";var result = ss.charAt(1);//"t"
```

charCodeAt( ) 类似 不过返回的是Unicode编码值

补充：String.fromCharCode( )

​			返回Unicode编码对应的字符

```js
var result = String.fromCharCode(20045);//"乍"
```

##### concat( )

连接两个或多个字符串

```js
var str = "hello";var result = str.concat("你好","hi");
```

##### indexof( ) lastindexof( )

indexof( )从前往后   lastindexof( )从后往前

检索是否含有指定内容

​	如果有 -> 返回第一次出现的索引

​	没有    -> 返回-1

可以通过第二个参数指定开始查找的位置

```js
var str = "hello";var result1 = str.indexof("l");				//2var result2 = str.indexof("l",result + 1);	 //3
```

##### search( )

搜索字符串是否含有指定内容

​	如果有 -> 返回第一次出现的索引

​	没有    -> 返回-1

可以使用正则

```js
var result = str.search(/a[bef]c/);//查找abc或aec或afc
```

##### match( )

搜索字符串是否含有指定内容

默认情况下，只会找到第一个符合要求的内容，然后就停止检索

但我们可以设置正则表达式设置为全局匹配模式，这时候会把匹配到的内容封装到一个数组里面返回，即使只能查询到一个结果

```js
var str = "1a2b3c";var result = str.match(/[a-z]/ig);//result[0] == a  ,  result == ["a","b","c"]
```

##### replace( )

参数1：被替换的内容

参数2：新的内容

默认只会替换第一个

但可以使用正则

```js
result = str.replace(/[a-z]/ig,"");//去掉所有字母
```



##### split( )

将一个字符串拆分成一个数组

```js
str = "abc,bcd,jkl,l";var result1 = str.split(",");	//["abc","bcd","jkl","l"]var result2 = str.split();		//["abc,bcd,jkl,l"]var result3 = str.split("");	//["a","b","c"……]
```

使用正则来拆分

```JS
var str = "1s2d3";var result = str.split(/[A-z]/);//["1","2","3"]
```



##### slice( )

slice( start , end )

截取字符串，不改变原来的

包含开始索引，不包含结束索引    **[ start, end )**

如果第二个参数不写 -> **[ start ,** 数组的最后一个元素 **]**

索引可以传递一个负值，如果传递一个负值，则从后往前计算

```js
var str = "01234567";var result1 = str.slice(1,4); //"123"var result2 = str.slice(6);   //"67"var result3 = str.ice(5,-1);//"56"
```

##### substring( )

substring( start , end )

类似 slice

不同的是，索引不可以传递负值，如果传递一个负值，则默认使用0

还会自动调整参数位置，保证前面的<后面的

```js
var str = "01234567";var result = str.ice(5,-1);//"01234"
```

##### substr( )

substr( start , num )

第二个参数的截取的长度

```js
var str = "01234567";var result = str.substr(5,2);//"56"
```





#### 强制类型转换🌤

一般指将其他的数据类型转换为String Number Boolean

##### 转换为String

1. **+""方法✔**

   ```js
   var c = 123 ;c = c + "" ;//实际也是调用String()函数
   ```

2. 调用 toString() 方法

   ```js
   var a = 123;a = a.toString();
   ```

   ​	不影响原来的变量 会以转换的结果返回

   ​	但注意：null与undefined没有toString()方法

   

3. **调用 String() 方法**✔

   ```js
   var a = 123;a = String(a);
   ```

   ​	不影响原来的变量 会以转换的结果返回

   - null->"null"

   - undefined->"undefined"

   - Number/Boolen->toString()

     

##### 转换为Number(各种进制)

- **-0  *1  /1  +** ✔

  ```js
  var a = b = c = d = "123";a = a - 0;b = b * 1;c = c / 1;d = + d ;
  ```

  ​	原理和 Number() 一样

  ​	[用+号要注意](#运算符注意事项)❗❗

  

- **调用 Number() 方法**✔

  ```js
  var a = "123.456";a = Number(a);
  ```

  - string：

    如果是纯数字->数字

    有非数字的内容->NaN

  - Boolean：1和0

  - Null：0

  - undefined：NaN

    

- **调用 parseInt() parseFloat)方法**✔

  ```js
  a = "123.89px567";b = parseInt(a);//b=123c = parseFloat(a);//c=123.89
  ```

  1. 适用于string类型数字+非数字混杂

  2. 从左开始读，遇到非数字即停止

  3. 第一位就是非数字 ->返回NaN

  4. 对非string使用此方法->先转换为string后操作

     ```js
     //可以用于浮点型->整形a = 123.45；a = paiseInt(a);//a=123
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
  a = "08";//8进制a = paiseInt(a,8);//a=10
  ```

##### 转换为Boolean

- ！！方法✔

  ```js
  a=!!a;
  ```

- 调用 Boolean() 方法✔

  ```js
  a = "123.456";a = Boolean(a);
  ```

  - string：空字符串->false
  - Number：0和NaN->false
  - Null：false
  - undefined：false
  - 对象->true



### 拷贝👻

#### 基本数据类型

​	除了Object

​	原因：基本数据类型的值 直接 保存在栈内存中，值与值独立存在

​		栈内存里：变量：a   值：123

```js
var a = 123;var b = a;a++;//a=124 b=123
```

#### 引用数据类型😈

​	只有Object

​	原因：对象是保存在堆内存中，栈里面的变量保存 的是 对象的内存地址 (即对象的引用)

​		栈内存里：变量：obj2   值：0x123(堆内存的地址)

​		堆内存里：name="哈利波特"……

```js
var obj = new Object();obj.name = "哈利波特";var obj2 = obj;obj.name = "赫敏格兰杰";//obj.name == obj2.name == "赫敏格兰杰"
```

```js
var obj = new Object();obj.name = "哈利波特";var obj2 = obj;obj.name = "赫敏格兰杰";obj2 = null;//断开obj与obj2的联系//obj.name == "赫敏格兰杰"//obj2.name == null
```



### 运算符

​	比如typeof就是运算符，可以获得一个值的类型

```js
var a = 123;var result = typeof a;//result="Number"console.log(typeof result);//输出"string"
```

#### 运算符注意事项🍓

- NaN

  - 算术运算：NaN
  - 比较运算：false

- 只要出现Number，其他都转换为Number再计算

  ​    **注意**：如果第一位是非数字(除null为0) 其他都是NaN 🗽看上一条

  - 除➕加号❗❗

    ```js
    a = "1" + 2 + 3 ;//"123"b = 1 + 2 + "3" ;//"33"c = +"1";//1 这里没有其他Number啦
    ```

  - 其他算术运算符

    ```js
    a = 100 - "1";//99b = 100 * undefined; //NaN
    ```

- 比较运算符

  ​	比较两个基本数据类型时，就是比较值

  ```js
  "5"<"11"; // 用Unicode比较 从第一位开始逐位比较 因为都是string类型+"5"<"11"; // 即比较5<11
  ```

  ###### 	比较两个引用数据类型时，比较的是对象的内存地址🎃

  ```js
  var obj1 = new Object();var obj2 = new Object();obj1.name = "JS";obj2.name = "JS";//obj1.name != obj2.name
  ```

  

- 相等运算符

  - ==     !=       弱      先进行转换
  - = = =   ! = =    强

- 条件运算符

  ```js
  true ? alert("yes") : alert("no");//条件表达式?语句1:语句2;
  ```

  


### 基本语句

#### if语句

​	和C++一模一样

```js
var a = 1;if ( a === 1 ){ alert("yes"); }else if( a === 2 ) alert("no") ;else alert("none");
```

#### switch语句

​	和C++一模一样

```js
switch(num){    case 1 : alert("是1");break;    default : alert("不是1");break;}switch(true){    case num===1  :alert("是1");break;    default : alert("不是1");break;}
```

#### while语句

​	和C++一模一样

```js
while (true) {}do {} while (true);
```

#### for循环

​	和C++一模一样

```js
for(var a = 0 ; a <= 5; a++) alert(a);
```



### 作用域

#### 全局作用域

- 直接编写在script里面的代码

- 在页面打开的时候创建，在页面关闭的时候销毁

- 在全局作用域中有一个全局对象window，代表的是浏览器的窗口

  ```js
  //<script>var a = 10;console.log(a); //两句话等价console.log(window.a);function fun(){console.log("我是fun函数");}fun(); //两句话等价window.fun();alert("hello"); //两句话等价window.alert("hello");//</script>
  ```

- 看代码不说话

  ```js
  //<script>    alert(a); //弹出undefined   var a = 123;//</script>
  ```

  ```js
  //<script>    fun();  //可以弹出a   function fun(){alert("a");}   fun2(); //不执行   var fun2 = function(){alert("b");}//</script>
  ```

  

#### 函数作用域

- 当在函数作用域操作一个变量时，它会先在自身作用域寻找，如果找到就直接用

  如果没有则向上一级作用域寻找，直到找到全局作用域

  如果全局作用域没有，则报错ReferenceError

  ```js
  var a = 2;function fun(){    alert(a); //弹出undefined    var a = 1;}
  ```

- 在函数中访问全局变量可以用window

#### this🐰

```js
name="Harry";var fun = function(){alert(this.name);}fun(); //弹出来Harryobj={    name:"Ron",    show:fun}obj.show();//弹出来Ron
```

```js
name="Harry";var fun = function(){alert(this.name);}obj={    name:"Ron",    show:fun()}obj.show;  //弹出来Harryobj.show();//弹出来Harry
```



### 垃圾回收GC

直接赋值为null

```js
var a = 1;a = null;
```





## 对象Object🦊

是一个引用数据类型，[拷贝时要注意 ](#引用数据类型😈)  [比较时也要注意](#比较两个引用数据类型时，比较的是对象的内存地址🎃)  ❗❗  

### 对象的基本使用

#### 对象的分类

1. 内建对象
   - 由ES标准中定义的对象，在任何的ES实现中都可以使用
   - 比如 Math String Number Boolean Function Object……
2. 宿主对象
   - 由JS的运行环境提供的对象，目前来讲主要指由浏览器提供的对象
   - 比如 BOM DOM
3. 自定义对象
   - 由开发人员自己创建的

#### 创建对象

```js
var obj1 = new Object (); var obj2 = {};var obj3 = {    name:"Ron",    school:{name:"Hogwarts"},    showName:function(){        console.log(obj3.name);    }    //Object里 } 前最后一个 , 可有可无 最好有};
```

##### 用工厂方法创建对象

```js
function createPerson( name , age ){    var obj = new Object();    obj.name = name ;    obj.age = age ;    obj.showname = function(){alert( this.name );},    alert("create")    return obj; //这句别忘了}var obj = createPerson( "Hermione" , 12 );
```

##### 用构造函数创建对象✔

构造函数习惯上首字母大写，需要用new关键字来调用

```js
function Person( name , age ){    this.name = name ;    this.age = age;    this.showname = fun,}function fun(){alert( this.name );};var harry = new Person( "harry" , 18 );
```

注意  [prototype](#**prototype**🌺)  ❗❗



#### 添加/删除/读取对象属性

JS对象的属性值可以是任意数据类型，甚至也可以是一个**对象**

```js
obj.name = "JavaScript";console.log (obj.name);//如果对象没有该属性，不会报错而是返回undefineddelete obj.name;
```

如果要使用特殊的属性名:✔

​		下面两段函数是等效的🦢

```js
obj["123"] = 789; //对象["属性名"] = 属性值console.log (obj.["123"]);
```

```js
var n = "123";obj[n] = 789; console.log (obj.[n]);
```

#### 枚举对象的属性

```js
for( var n in obj ){    console.log(n);//()里面不能写obj.n    console.log(obj[n]);//和上面等价}//很像python里面的for
```

#### instanceof函数

检查一个对象是否一个类的实例

```js
console.log( harry instanceof Person );
```

#### 打印对象

在我们直接在页面中打印一个对象，实际上输出的是 toString() 方法的返回值

```js
var Luna = new Person( "Luna", "Ravenclaw" );console.log( Luna );console.log( Luna.toString() );//两者等价 都是[object Object]
```

可以为对象添加一个 toString() 方法

```js
Luna.toString = function(){    return "Person[name="+this.name+",collage="+this.collage+"]"}//注意是用return方式返回console.log( Luna );//这次就是"Person[……]"
```





### 函数🎪

函数是一个对象

#### 创建和调用函数

```js
var fun = new Function("console.log('JS');");//很少这么用console.log(fun.prototype);//[object Object] 每个函数都有function fun2( a , b ){ //()里面可以加形参，也可不写    function fun4( a , b ){ //可以在函数内部再声明一个函数        console.log( a + b );    }    return fun4 ;//返回的是函数对象fun4}var fun3 = function(){     function fun5(){        console.log( "JS" );        return;//和不写return一样，都是返回undefined    }    return fun5() ;//返回的是fun5的返回值undefined    }fun();fun2(123,"hello",456);//456和没写一样//调用函数时，解析器不会检查实参的 类型 和 数量//所以要注意，是否有可能会接收到非法的参数//后面的多余实参不会被赋值
```

调用函数时要区分:

​		fun() 是调用函数，相当于使用函数的返回值

​		fun   是函数对象，相当于直接使用函数对象



#### **prototype**🌺

我们创建的每一个函数，解析器都会向函数中添加一个属性prototype

- 如果函数是普通函数，调用prototype没有任何作用

- 如果函数以构造函数调用，它所创建的对象都有一个隐含的属性(可以理解为公共接口)

  指向该构造函数的原型对象，可通过 \_\_proto__访问该属性(前后各两个下划线)

  原型对象相当于一个公共的区域，所有同一个类的实例都可以访问到这个原型对象

  ```js
  function College(){}College.prototype.color = none;var Gryffindor = new College();var Ravenclaw = new College();Ravenclaw.__proto__.color = blue;alert(Gryffindor.__proto__ === Ravenclaw.__proto__);//truealert(Gryffindor.__proto__.color = none );//truealert(Ravenclaw.__proto__.color = blue);//true
  ```

  |         College函数对象         |  值   |      |  原型对象(0x123) 名称  |  值  |
  | :-----------------------------: | :---: | :--: | :--------------------: | :--: |
  |            prototype            | 0x123 |      |         color          | none |
  |                                 |       |      |                        |      |
  | 通过College创建的对象Gryffindor |  值   |      |                        |      |
  |           \_\_proto__           | 0x123 |      |         color          | none |
  |                                 |       |      |                        |      |
  | 通过College创建的对象Ravenclaw  |  值   |      |                        |      |
  |           \_\_proto__           | 0x123 |      |         color          | none |
  |              color              | blue  |      | 左边的优先级高于上面的 |      |

下面来套娃🎎：

​	原型对象也是对象，所以它也有原型

​		当我们使用一个对象的属性和方法的时，会先在自身中寻找

​			if ( 自身方法有 ) 直接使用

​			else if ( 原型对象有 ) 用原型对象的

​			else if ( 原型对象的原型有 ) 用原型对象的原型的

​			…………

```js
function fun () {}alert(fun.__proto__.__proto__);//弹出[object Object]alert(fun.__proto__.__proto__.__proto__);//弹出nullalert(fun.__proto__.color);//弹出undefined
```



hasOwnProperty()

检查对象自身是否含有该属性，不检查prototype里面有没有

```js
console.log( Gryffindor.hasOwnProperty("color") );//falseconsole.log( "color" in Gryffindor );//检查原型+自身 true
```



#### 立即执行函数

定义完立即被调用，往往只执行一次

```js
(function( a , b ){    alert("a = " + a );    alert("b = " + b );})( 123 , 456 );
```



#### call( ) 和 apply( )

都是函数对象的方法，需要通过函数对象来调用

第一个参数 -> 一个对象 -> 成为函数的 this 

第二个参数（ 看原来的函数有没有形参 ）：

- call( ) 将实参在对象之后依次传递
- apply( ) 需要将实参封装到一个数组中统一传递

```js
function fun(){    alert(this);}var obj = {};fun();//弹出[object , Window]fun.call( obj );//弹出[object , Object]fun.apply( obj );//弹出[object , Object]var harry ={    name: "Harry",    showName: function(){        alert(this.name);    },    test: function( a , b ){        console(this.name + a + b );    }};var ron ={    name: "Ron";};harry.showName.apply(ron);//弹出Ronharry.test.call(ron,2,3);//ron23harry.test.apply(ron,[2,3]);//ron23
```



#### arguments

在调用函数时，浏览器每次都会传递两个隐含的参数：

1. 函数的上下文对象this

2. 封装实参的对象arguments

   

arguments是一个类数组对象，但不是真正的 ~~数组~~

- 可以通过索引操作数据
- 可以获取长度
- 有一个属性：callee   ->  对应当前的函数对象

```js
function fun(){    console.log(argument[0]);    console.log(argument.length);    console.log(argument.callee == fun );}fun("hello",true);//"hello",2,true
```





### 数组🎏

数组 Array 也是一个对象

不同的是，普通对象是使用字符串作为属性名，而数组是使用数字作为索引 (index) 操作元素

#### 创建数组

```js
var arr = new Array();arr[0] = 1;alert(arr);//弹出来1 不是地址var arr2 = [5];//数组只有一个元素5var arr3 = [1,"hello",null];var arr4 = new Array(10);//创建一个长度为10的数组var arr5 = new Array(10,"hello",null);
```

#### 数组的length

数组的最大索引 +1 

```js
arr[10] = 8;//此时arr.length == 11arr.length = 10;//修改length值来修改数组arr[arr.length] = 70;//向数组这个队列最后push一个元素
```

if （修改的 length > 大于原长度）多出的部分空出来

if （修改的 length < 大于原长度）多余的元素会被删除



#### 数组的基本函数

##### push( )

向数组 **最后** ==添加== 函数，返回值为数组新的长度

```js
var arr = ["Harry"];arr.push( "Ron","Jenny" );var result = arr.push( "Hermione" );//result == 4//arr == ["Harry","Ron","Jenny","Hermione"]
```

##### pop( )

从数组 **最后** ==删除== 函数，返回值为删除的那个元素值

```js
var arr = ["Harry" , "Ron" . "Hermione"];var result = arr.pop();  //result == "Hermione"arr.pop();//arr == ["Harry"]
```

##### unshift( )

向数组 **开头** ==添加== 元素，返回值为数组新的长度

```js
var arr = ["Harry"];arr.unshift( "Ron","Jenny" );var result = arr.unshift( "Hermione" );//result == 4//arr == ["Hermione","Ron","Jenny","Harry"]
```

##### shift( )

向数组 **开头** ==删除== 元素，返回值为删除的那个元素值

```js
var arr = ["Harry" , "Ron" . "Hermione"];var result = arr.shift();  //result == "Harry"arr.shift();//arr == ["Hermione"]
```

##### forEach( )

==遍历==数组

需要一个函数作为参数，数组中有几个元素就执行几次

IE8及以下浏览器不支持

```js
arr.forEach(function(){            console.log("JS");});arr.forEach(function(value , index , a) {                   //浏览器会在回调函数中传递三个参数    console.log(a);//第一个：当前正在遍历的元素    console.log(b);//第二个：当前正在遍历的元素索引012    console.log(a == arr);//第三个：就是正在遍历的数组    //加入有第四个之后->undefined});
```

##### slice( )

slice( start , end )

==截取==数组，==不改变==原来数组

包含开始索引，不包含结束索引    **[ start, end )**

如果第二个参数不写 -> **[ start ,** 数组的最后一个元素 **]**

索引可以传递一个负值，如果传递一个负值，则从后往前计算

```js
var arr = [0,1,2,3,4,5,6,7];var result1 = arr.slice(1,4); //[1,2,3]var result2 = arr.slice(6);   //[6,7]var result3 = arr.slice(5,-1);//[5,6]
```

##### splice( )

==截取== 并 ==删除== 原来数组，返回值为删除的元素

splice( start ,  num , 杂七 , 杂八 …… )  

第二个参数是删除的数量

第三个及以后(可以没有) 传递新的元素，这些元素自动插入到 start 位置

```js
var arr = [0,1,2,3,4,5,6,7];var result1 = arr.splice(3,0);//相当于没改var result2 = arr.splice(1,3,9); //[1,2,3]//arr = [0,9,4,5,6,7]
```

##### concat( )

==连接== 两个或多个数组，并且将新的数组返回，==不改变== 原数组

```js
var arr1 = [0,1,2];var arr2 = [3,4,5];var arr3 = [6,7,8];var result = arr1.concat(arr2,arr3);//result == [0,1,2,3,4,5,6,7,8]
```

##### join( )

将数组 ==转换为字符串==，返回值为字符串，不改变原数组

join( "连接符" )  括号里面的参数将作为元素的连接符

如果没有，则默认使用  ==**, **== 作为连接符

```js
var arr1 = [0,1,2];var result = arr1.join("");    //"012"var result2 = arr1.join("+");  //"0+1+2"var result3 = arr1.join();     //"0,1,2"
```

##### reserve( )

==翻转== 数组

```js
var arr1 = [0,1,2];arr1.reserve();  //[2,1,0]
```

##### sort( )

对数组 ==排序== ，改变原数组
默认用Unicode编码进行排序 ( 纯数字要注意❗❗ )

```js
var arr1 = ["b","c","a"];arr1.sort();  //["a","b","c"]var arr2 = [2,3,11];arr1.sort();  //[11,2,3]
```

对于**纯数字**和其他特殊需求：

​	可以在sort( )添加一个回调函数，用来指定排序规则

​		回调函数中需要定义两个形参，浏览器会分别使用数组的元素作为实参去调用回调函数

​		使用哪个元素调用不确定，但确定的是数组中 第一个形参 在 第二个形参 前边

​		浏览器会根据回调函数的返回值决定元素的顺序，如果返回**大于**0，则元素交换位置 (   **等于0也不交换！！**)

```js
var arr = [0,2,1];arr.sort(function(a,b){    return a-b;    //a-b是从小到大，b-a是从大到小});//arr == [0,1,2]
```





### Date对象

#### 创建和调用Date

当前代码执行的时间

```js
var d = new Date();console.log(d);//Mon Aug 02 2021 22:28:02 GMT+0800 (GMT+08:00)
```

指定时间对象

​	格式：月/日/年 时:分:秒

```js
var d = new Date("9/10/2003");console.log(d);//Wed Sep 10 2003 00:00:00 GMT+0800 (GMT+08:00)
```



#### Date 的基本函数

##### getDate( )

获取当前日期是几日 (日期)

```js
var d = new Date();var date = d.getDate();
```

##### getDay( )

获取当前日期是星期几 返回一个0-6的值 其中0表示周日

```js
var d = new Date();var day = d.getDay();
```

##### getMonth( )

获取当前日期的 ==月份-1==   返回一个0-11的值 其中 **0表示1月**

```js
var d = new Date();var Month = d.getMonth();
```

##### getFullYear( )

获取当前日期的年份 返回的是四位数字 比如2021

```js
var d = new Date();var year = d.getFullYear();
```

##### getTime( )

获取当前日期的的时间戳

```js
var d = new Date();var time = d.getTime();
```

时间戳： 本初子午线时间1/1/1970  0:0:0 到当前日期的**毫秒**数 ( 如果要用北京时间需要转换 )

​				计算机底层在保存时间的时候使用时间戳

​				可以利用时间戳来测试代码执行的性能

```js
var start = Date。now();//各种函数操作var end = Date.now();console.log((end-start)+"毫秒"）;
```



时分秒都可以获得 具体看函数库





### Math对象

属于一个工具类，不是一个构造函数。不用创建对象，里面封装了数学运算相关的属性和方法

比如 Math.PI == 3.1415926……表示圆周率

#### Math的基本函数

##### abs( )

绝对值

```js
 console.log(Math.abs(-1));
```

##### ceil( )

向上取整

```js
 console.log(Math.ceil(1.01));  // 2
```

##### floor( )

向下取整

```js
 console.log(Math.floor(1.99)); // 1
```

##### round( )

四舍五入

```js
 console.log(Math.round(1.5); // 2
```

##### random( )

生成一个 **0-1** 之间的随机数

```js
 console.log(Math.random()); // 比如0.0985663453
```

若要生成一个 **x-x+y** 之间的随机数

```js
 console.log( Math.random()*y + x); // 比如0.0985663453
```



##### max( ) min( )

最大值 最小值

```js
var max = Math.max(10,20,30);
```

##### pow( )

pow( x , y )返回 x 的 y 次方

```js
console.log( Math.pow(12,2));// 144
```

##### sqrt( )

取平方根

```js
console.log(Math.sqrt(2));//1.41421……
```





### 包装类

自己少用，给浏览器底层用



由于基本数据类型无法添加方法和属性

当我们对一些基本数据类型的值去调用属性和方法时：

​	浏览器会临时使用包装类将其转换为对象，然后再调用对象的属性和方法

​	调用完之后，再将其转换为基本数据类型

```js
var s = 123;s = s.toString();//这里s被临时转换为对象
```



JS中为我们提供了三个包装类：

- String( ) 
- Number( ) 
- Boolean( ) 

通过这三个包装类可以将基本数据类型的数据转换为对象

```js
var num = new Number(3);console.log(typeof num);//objectnum.name = "NUM";//可以往里面添加属性
```

但注意，两个对象比较的时候，比较的是地址

```js
var num1 = new Number(3);var num2 = new Number(3);// num1 != num2
```

因为是对象，就会存在下面这种问题：

```js
var b = new Boolean(false);if(b){alert("我运行了");}//不管怎么样都会运行//因为if(b)当中，由于b是一个对象，转换为Boolean值都为true
```







## 正则表达式📐

正则表达式是一个对象，我们需要先创建它

### 创建正则的对象

var  变量 = new RegExp( "正则表达式" , "匹配模式" )

更灵活，可以随时修改

匹配模式：

- **"i"**：忽略大小写
- **"g"**：全局匹配模式

```js
var reg = new RegExp("a");//字符串是否含有avar reg = new RegExp("a","i");//字符串是否含有a或A
```

简洁版：字面量

```js
reg1 = /a/i;		//是否含有a或Areg2 = /a|b|c/;		//是否含有a或b或creg3 = /[abc]/; 	//是否含有a或b或creg4 = /[a-c]/; 	//是否含有a或b或creg5 = /[A-z]/;   	//是否含有字母reg6 = /1[abc]2/; 	//是否含有1a2或1b2或1c2reg7 = /[^abc]/; 	//只要有除了a或b或c就行reg8 = /(ab){3}/;	//是否含有abababreg9 = /ab{3}/;		//是否含有abbbree1 = /ab{1,3}c/;	//是否含有abc或abbc或abbbcree2 = /ab*c/;		//*相当于{0,} ->是否含有ac或abc或abbc……ree3 = /ab+c/;		//+相当于{1,} ->是否含有abc或abbc或abbbc……ree4 = /ab?c/;		//?相当于{0,1} ->是否含有ac或abcree5 = /^a/;		//^表示开头 ->是否以a开头ree6 = /a$/;		//$表示开头 ->是否以a结尾ree7 = /./;			//.表示任意字符ree6 = /\./;		//是否有.phone = /^1[3-9][0-9]{9}$/email = /^\w{3,}(\.\w+)*@[A-z0-9]+(\.[A-z]){2,5}){1,2}$/;
```

\w 任意的数字+字母

\W 除了数字字母

\d 任意的数字

\D 除了数字

\s 空格

\S 除了空格

\b 单词边界 比如/\bchild\b/ 只能查到child children返回false

\B 除了单词边界

### 正则的方法

#### test( )

检查一个字符串是否符合正则表达式的规则 返回 true/false

```js
var reg = new RegExp("a");var str = "abc";var result = reg.test(str);//true
```





## DOM

### 表单全选和反选

```html
<html>    <head>       <meta charset="GBK">            <title>                hello world            </title>            <script>                window.onload = function(){                    //全选                    var checkedAllBtn = document.getElementById("checkedAllBtn");                    checkedAllBtn.onclick = function(){                        //获取四个多选框items                        var items = document.getElementsByName("items");                        //遍历items                        for(var i=0;i<items.length;i++){                            items[i].checked=true;                        }                    };                    //反选                    var checkedRevBtn = document.getElementById("checkedRevBtn");                    checkedRevBtn.onclick = function(){                        //获取四个多选框items                        var items = document.getElementsByName("items");                        //遍历items                        for(var i=0;i<items.length;i++){                            items[i].checked=!items[i].checked;                        }                    };                }                            </script>    </head>    <body>        <!--表单-->        <form method = "post" action = "">            你喜欢的运动<!--<input type = "checkbox" id = "checkedAllBox"/>-->            <br />            <input type = "checkbox" name = "items" value = "篮球" />篮球            <input type = "checkbox" name = "items" value = "足球" />足球            <input type = "checkbox" name = "items" value = "排球" />排球            <input type = "checkbox" name = "items" value = "网球" />网球            <br />            <input type = "button" id="checkedAllBtn"   value = "全选" />            <input type = "button" id="checkedRevBtn"   value = "反选" />        </form>    </body></html>
```

