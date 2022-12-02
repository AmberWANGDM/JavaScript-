# JS语法

参考 https://wangdoc.com/javascript/basic/grammar

# 表达式与语句

## 两者区别

表达式一般都有值，语句可能有也可能没有

语句一般会改变环境（声明，赋值）

上面两句不绝对

## 表达式

1 + 2 表达式的**值**为 3

add(1,2)表达式的值为函数的**返回值**（只有函数有返回值）

console.log 表达式的值为函数本身

console.log(3) 表达式的值为 undefined

<img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201134902457.png" alt="image-20221201134902457" style="zoom:50%;" />

<img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201132730596.png" alt="image-20221201132730596" style="zoom:50%;" />

## 语句

var a = 1 是一个语句

# 大小写敏感

var a 和 var A 不同

object 和 Object 不同，function 和 Function 不同

# 空格&回车

大部分空格没有意义，但是回车不能加在 return 后面

<img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201133416121.png" alt="image-20221201133416121" style="zoom:50%;" />

# 标识符

## 规则

第一个字符可以是Unicode字母（注意不是英文字母）或 $ 或 _ 或 中文

后面的字符还可以有数字

<img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201133906977.png" alt="语法错误" style="zoom:50%;" />

## 变量名是标识符

var _ = 1

var $ = 2

var 你好 = ‘hi’

# 区块 block

把代码包在一起

常与 if / for / while 合用

# 条件语句

## if语句

### 语法

`if (表达式){语句1} else {语句2}`

### 变态情况

- 表达式 a=1

<img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201145836296.png" alt="image-20221201145836296" style="zoom:50%;" /><img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201145912296.png" alt="image-20221201145912296" style="zoom:50%;" />

- 语句1和语句2可以嵌套if-else
- 缩进

<img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201151222383.png" alt="image-20221201151222383" style="zoom:50%;" /><img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201151317942.png" alt="image-20221201151317942" style="zoom:50%;" />

### 推荐写法

最好

```js
if (表达式) {
	语句
} else if (表达式) {
	语句
} else {
	语句
}
```

次推荐

```js
function fn(){
	if (表达式)  {
		return 表达式
	}
	if (表达式) {
		return 表达式
	}
	return 表达式
}
```

## switch语句

### 语法

```js
switch (fruit) {
  case "banana":
    // ...
    break;
  case "apple":
    // ...
    break;
  default:
    // ...
}
```

### break

大部分时候，每个`case`代码块内部的`break`语句不能少，否则会接下去执行下一个`case`代码块，而不是跳出`switch`结构。

## 问号冒号表达式

`表达式1 ? 表达式2 : 表达式3`

如果表达式1为`true`，则返回“表达式2”的值，否则返回“表达式3”的值。

## && 且 短路逻辑

用于多个表达式的求值

`A && B && C && D`

返回第一个布尔值为false的表达式的值 或 表达式D的值

<img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201155722874.png" alt="image-20221201155722874" style="zoom: 25%;" />

使用场景：

<img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201153306291.png" alt="image-20221201153306291" style="zoom:50%;" />

## || 或 短路逻辑

`A || B || C || D`

取第一个真值或D

<img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201155739759.png" alt="image-20221201155739759" style="zoom:25%;" />

使用场景：



<img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201155438599.png" alt="image-20221201155438599" style="zoom:50%;" />

<img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201155620301.png" alt="image-20221201155620301" style="zoom:50%;" />

# 循环语句

## while语句

`while(表达式){语句}`

如果表达式为真，执行语句，执行完毕再判断表达式的真假，当表达式为假，执行后面的语句

<img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201162451149.png" alt="image-20221201162451149" style="zoom:50%;" />

注意

1. while没有返回值
2. 死循环问题
3. 浮点数问题

<img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201163056673.png" alt="image-20221201163056673" style="zoom:50%;" />

## for循环

while的语法糖<img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201163339084.png" alt="image-20221201163339084" style="zoom:50%;" />

### 语法

`for (语句1①; 表达式2②; 语句3③) {循环体④}`

先执行语句1，然后判断表达式2，如果为真，执行循环体，然后执行语句3；每轮循环判断表达式2，如果为假，则直接退出循环。

①②④③->②④③->②④③->②为false退出循环

## break和continue

退出所有循环 v.s. 退出当前一次循环

注意：break只会退出离他最近的for

## label

```js
foo: {
  console.log(1);
  break foo;
  console.log('本行不会输出');
}
console.log(2);
```

可以用来跳出双层循环

```js
top:
  for (var i = 0; i < 3; i++){
    for (var j = 0; j < 3; j++){
      if (i === 1 && j === 1) break top;
      console.log('i=' + i + ', j=' + j);
    }
  }
// i=0, j=0
// i=0, j=1
// i=0, j=2
// i=1, j=0
```

<img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201174005323.png" alt="image-20221201174005323" style="zoom: 25%;" />

foo是一个label，跟着的语句是1

# 数据类型

## 数字与字符串

Q: 都是一，为什么要分 1 和 '1'

A: <u>功能</u>不同（数字能加减乘除，字符串不行；字符串能表示电话号码，数字不行；<u>存储形式</u>不同（Js中数字变成二进制直接存，用64位浮点数的形式存储，字符串需要编码，使用类似UTF-8的形式——UCS-2）

**Q:如何存数字**

A: 十进制转成二进制

31 变成二进制 <img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201202311113.png" alt="image-20221201202311113" style="zoom:33%;" />
经过一番尝试<img src="https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/image-20221201202325481.png" alt="image-20221201202325481" style="zoom:33%;" />
所以 31(十进制) = 011111(二进制)
不是套公式吗？程序员从来不套公式 :smile:

​	Q: 为什么用十六进制

​	A: 二进制写起来太慢了

​	Q: 二进制转十六进制

​	A: 从右往左每四位改写成一位，大于9的数字改为ABCDEF



**Q: 如何存字符**

A: 转成数字~ 给每个字符编号

1. 『ASCII』128个字符的编码 占用一个字节的7位

2. 表示中文 『国标2312』4位十六进制数 4*4=16位 两个字节

3. 微软 国标扩展 『GBK』16位 两个字节 

4. 万国码 『Unicode』已收录13万字符（大于16位） 全世界通用

缺点：两个字节不够用，每个字符要用三个及以上字节，这样所有文件都扩大 50%，不划算

使用UTF-8偷懒：最少可用 8 位存一个字符，是一种变长的编码方式

## JS中的数据类型

8种

number, string, bool, symbol, bigint, undefined, null, object

数组、函数、日期不是数据类型，属于object

### number

> 64位浮点数

#### 写法

整数、小数、科学计数法1.23e4、八进制（0|00|0o开头）、16进制（0x或0X）、2进制（0b或0B）

#### 特殊值

**正0和负0**

都是0

![](https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/20221202093603.png)

**无穷大**

Infinity +Infinity -Infinity

**无法表示的数字**

NaN 

但NaN仍然是一个数字

0/0 => NaN

NaN != NaN

#### ==64位浮点数==

**js数字的存储形式**

浮点就是浮动的点，意思就是小数点会乱动

123.456 可以表示为 1.23456e10^2

也可以表示为 12345.6e10^-2

**64位存储一个number**

![](https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/202212020946877.png)

正负号占1位, 指数占11位(-1023~+1024), 有效数字占52位(开头的1省略)

**范围和精度**

**范围** 指数拉满, 有效数字拉满, 得到最大二进制数字; 指数负方向拉满, 有效数字最小1, 得到最小值

`Number.MAX_VALUE` `Number.MIN_VALUE`

**精度** (有效数字) 

最多只能到52+1个二进制位表示有效数字, 2^53 对应的十进制是 9 后面 15 个零, 所以15位有效数字都能精确表示

16位有效数字如果小于 90 开头，也能精确表示
9110000000000001 就存不下来


### string

每个字符两个字节(阉割版UTF-8)

**写法**

单引号, 双引号, 反引号

注意: 引号不属于字符串的一部分, 如果要在单引号里面包含单引号, 就需要用到**转义**

**转义**

'It's ok' JS引擎会认为'it'就结束了

正确写法: 'It\'s ok' 或 "It's ok" 或 \`It's ok\`

```
\' 表示 '
\" 表示 "
\n 表示换行
\r 表示回车
\t 表示 tab 制表符
\\ 表示 \
\uFFFF 表示对应的 Unicode 字符
\xFF 表示前 256 个 Unicode 字符
```

**多行字符串**

反引号

**字符串的属性**

后续讲

**字符串的长度**

string.length

```
'123'.length // 3
'\n\r\t'.length // 3
'\\\\\\'.length // 3
''.length // 0
' '.length // 1
```

**通过下标读取字符**

`string[index]` index从0到length 

`string[length] // undefined 不会报错`

**base64转码**

`window.btoa` 正常字符串转为Base64编码的字符串

`window.atob` Base64编码的字符串转为原来的字符串

### boolean

true和false

**一些运算会得到bool值**

否定运算
!value

相等运算
1 == 2、1 != 2、3 === 4、3 !== 4

比较运算
1 > 2、1 >= 2、3 < 4、3 <= 4

**if 配 bool**

if( value ) { ... } else { ... }

**5个falsy值**

undefined null 0 NaN ''

### 两种空类型 undefined null

**没有本质区别**

细节一: 
如果一个变量声明了，但没有赋值，那么默认值就是 undefined，而不是 null

细节二: 
如果一个函数，没有写 return，那么默认 return undefined，而不是 null

细节三: 
前端程序员习惯上，把非对象的空值写为 undefined，把对象的空值写为 null
但仅仅是习惯上而已

# 变量声明

指定值

var a = 1

同时也指定了类型

var a = 1

但是值和类型都可以随意变化

a = 2

a = '字符串'

## 三种声明方式

var a = 1 

let a = 1 

const a = 1

a = 1

**区别**

var 是过时的、不好用的方式

let 是新的，更合理的方式

const 是声明时必须赋值，且不能再改的方式

最后这种方式是错误的，不准这样声明


## var方式

代码不要用var

**var变量提升**
https://wangdoc.com/javascript/basic/grammar#%E5%8F%98%E9%87%8F%E6%8F%90%E5%8D%87

## let方式

**规则**

1. 遵循块作用域，即 使用范围不能超出 { }

```js
{
    let b = 1
    console.log(b)
}

console.log(b)
// 1
// Uncaught ReferenceError: b is not defined
```

2. 不能重复声明

```js
let a = 1
let a = 2
// Uncaught SyntaxError: Identifier 'a' has already been declared

```

3. 可以赋值，也可以不赋值

4. 必须先声明再使用，否则报错

```js
{
    console.log(b)
    let b = 1
}
// Uncaught ReferenceError: Cannot access 'b' before initialization
```

5. 全局声明的 let 变量，不会变成 window 的属性

```js
var abc = 'abc'
console.log(window.abc)
// abc

let abc = 'abc'
console.log(window.abc)
// undefined

```

6. for 循环配合 let 有奇效

![var](https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/202212021034551.png)

![let](https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/202212021034842.png)

## const方式

常量(只读变量) 

声明时就要赋值，赋值后不能改

# 类型转换

## number => string

String(n)

n + ''

## string => number

Number(s)

parseInt(s) / parseFloat(s)

s - 0

## x => bool

Boolean(x)

!!x

```js
!!1
// true
!!0
// false
```

## x => string

String(x)

x.toString()

```js
1.toString() 
// Uncaught SyntaxError: Invalid or unexpected token
// js认为1.后面需要加数字
(1).toString()
1..toString()
```


# 对象

## **定义**

无序的数据集合

键值对的集合

## **写法**

```javascript
let obj = { 'name': 'frank', 'age': 18 }
let obj = new Object({'name': 'frank'})
console.log({ 'name': 'frank, 'age': 18 })
```

**细节**

- 键名是字符串，不是标识符，可以包含任意字符
- 引号可省略，省略之后就只能按照标识符的规则来写
- 就算引号省略了，键名也还是字符串（重要）
![](https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/202212021110827.png)

![](https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/202212021113586.png)

## **属性名**

每个key都是对象的属性名(property)

**奇怪的属性名**

所有属性名会自动变成字符串
```js
let obj = {
  1: 'a',
  3.2: 'b',
  1e2: true,
  1e-2: true,
  .234: true,
  0xFF: true
};
Object.keys(obj)
// ["1", "100", "255", "3.2", "0.01", "0.234"]

```
**变量de值用作属性名**

加[], 当做变量求值

```js
// es6新语法
var a = 'xxx'
var obj = {
    [a]:'aaa',
    [1+2+3+4]:'10'
}

console.log(obj) // {xxx: 'aaa', 10: '10'} 

// 之前需要写两行
var obj = {}
obj[a] = 1234
```
**除了字符串, Symbol也可以做属性名**
```js
let a = Symbol()
let obj = { [a]: 'Hello'}
```

## **属性值**

每个value都是对象的属性值

## **对象的隐藏属性**

JS每个对象都有一个隐藏属性, 存储着其共有属性组成的对象的地址, 这个共有属性组成的对象叫做原型

也就是说, 隐藏属性储存着原型的地址

```js
var obj = {}
obj.toString() // 不报错
```
因为obj隐藏属性对应的对象上有toString()

## 删除属性

`delete obj.xxx` 或 `delete obj['xxx']`

注意区分 属性值为undefined 和 不含属性名

```js
// 不含属性名
'xxx' in obj === false
// 含有属性名，但是值为 undefined
'xxx' in obj && obj.xxx === undefined
```
注意 `obj.xxx === undefined` 不能断定 'xxx' 是否为 obj 的属性


## 查看属性
### 查看所有属性

**查看自身所有属性**

`Object.keys()` `Object.values()`  `Object.entries()`

![](https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/202212021351650.png)

**查看自身+共有属性**

1. `console.dir(obj)` 推荐
![](https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/202212021353185.png)

2. `obj.__proto__`

**判断一个属性是自身的还是共有的**

`obj.hasOwnProperty('属性名')`

> 说到共有属性, 就涉及到原型的概念

 **每个对象都有原型**, 原型存储了对象的共有属性

 对象的原型也是对象, 所以对象的原型也有原型

 **对象的根**

 obj = {} 的原型即为所有对象的原型
 
 这个原型包含所有对象的共有属性, 称为对象的根

 这个原型也有原型, 是null

```js
console.log(obj.__proto__.__proto__)
// null
```
 ### 查看单个属性
 两种方法查看属性
 1. 中括号语法  obj['key'] 
 2. 点语法 obj.key

优先使用中括号语法: 点语法会误导你，让你以为 key 不是字符串

<span style="font-size:30px;color:red">obj.name 等价于 obj['name']
</span>

### 考题
```js
let list = ['name', 'age', 'gender']
let person = {
       name:'frank', age:18, gender:'man'}
for(let i = 0; i < list.length; i++){
  let name = list[i]
  console.log(person__???__)
}
// 应该填什么使得 person 的所有属性被打印出来
// 1. console.log(person.name)  会打印三遍frank, 相当于 person['name']
// 2. console.log(person[name])  √ for循环取出数组的项name是字符串
```

## 修改/增加属性

**直接赋值**

```js
let obj = {name: 'frank'} // name 是字符串
obj.name = 'frank' // name 是字符串
obj['name'] = 'frank' 
obj[name] = 'frank' // 错，因 name 值不确定
obj['na'+'me'] = 'frank'
let key = 'name'; obj[key] = 'frank'
let key = 'name'; obj.key = 'frank' // 错, 因为 obj.key 等价于 obj['key']
```
**批量赋值**

`Object.assign(obj, {age: 18, gender: 'man'})`

**无法通过自身修改或增加共有属性**

读可以访问共有属性, 但写操作不会影响共有属性

**如果一定要修改隐藏属性**

`obj.__proto__.toString = 'xxx'`
`Object.prototype.toString = 'xxx'`

不推荐使用上述方式, 推荐使用 `Object.create`
```js
// 在给对象赋值前指定原型
let common = { '国籍': 'China'}
let person = Object.create(common)
person.name = 'dan'
```

# 对象分类

任务: 输出一打正方形, 有3个属性 边长 面积 和 周长

实现思路1: 借助for循环
```js
let squareList = []
let widthList = [5,6,5,6,5,6,5,6,5,6,5,6]
for(let i = 0; i<12; i++){
  squareList[i] = {
    width: widthList[i],
    getArea(){ 
      return this.width * this.width 
    },
    getLength(){
      return this.width * 4
    }
  }
}
```
改进思路2: 借助原型
```js
let squareList = []
let widthList = [5,6,5,6,5,6,5,6,5,6,5,6]
let squarePrototype = {
  getArea(){ 
    return this.width * this.width 
  },
  getLength(){
    return this.width * 4
  }
}
for(let i = 0; i<12; i++){
  // Object.create()指定原型
  squareList[i] = Object.create(squarePrototype) 
  squareList[i].width = widthList[i]
}
```
上面代码依旧有分散的问题, 最好把创建对象的功能抽离到一个函数createSquare里面

改进思路3:
```js
let squareList = []
let widthList = [5,6,5,6,5,6,5,6,5,6,5,6]
function createSquare(width){ //此函数叫做构造函数
  let obj = Object.create(squarePrototype)
  // 以 squarePrototype 为原型创建空对象
  obj.width = width
  return obj
}
let squarePrototype = {
  getArea(){ 
    return this.width * this.width 
  },
  getLength(){
    return this.width * 4
  }
}
for(let i = 0; i<12; i++){
  squareList[i] = createSquare(widthList[i])
  // 这下创建 square 很简单了吧！
}
```
改进思路4:函数和原型结合
```js 
let squareList = []
let widthList = [5,6,5,6,5,6,5,6,5,6,5,6]

function createSquare(width){
  let obj = Object.create(createSquare.squarePrototype) // 先使用后定义？NO
  obj.width = width
  return obj
}
createSquare.squarePrototype = { //把原型放到函数上，结合够紧密了吗？
  getArea(){ 
    return this.width * this.width 
  },
  getLength(){
    return this.width * 4
  },
  constructor: createSquare //方便通过原型找到构造函数
}
for(let i = 0; i<12; i++){
  squareList[i] = createSquare(widthList[i])
  console.log(squareList[i].constructor) 
  // constructor 可以知道谁构造了这个对象：你妈是谁？
}
```

## new操作符

来自JS之父的爱 -- new操作符

```js
let squareList = []
let widthList = [5,6,5,6,5,6,5,6,5,6,5,6]
function Square(width){ 
  this.width = width
}
Square.prototype.getArea = function(){ 
  return this.width * this.width 
}
Square.prototype.getLength = function(){
  return this.width * 4
}
for(let i = 0; i<12; i++){
  squareList[i] = new Square(widthList[i])
  console.log(squareList[i].constructor) 
}
```
- 每个函数都有 prototype 属性，这是 JS 之父故意的

- 每个 prototype 都有 constructor 属性，也是故意的
- 

- new X()做了4件事
1. 自动创建空对象
2. 自动为空对象关联原型, **原型地址指定为 X.prototype**(将X.prototype保存的地址复制到空对象.__proto__里)
3. 将空对象作为this关键字运行构造函数
4. 自动return this

构造函数X
X函数本身负责为对象添加自身属性
X.prototype对象负责保存对象的共有属性

## 代码规范

**大小写**

所有构造函数(专门用来创建对象的函数)首字母大写

所有被构造出来的对象, 首字母小写

**词性**

new后面的的函数,使用名词形式,如 new Person() new Object()

其它函数一般用动词开头, 如 createSquare(), createElement('div')

## 确定对象的原型 -- 重要公式

为什么 ?

- let obj = new Object() 的原型是 Object.prototype
- let arr = new Array() 的原型是 Array.prototype
- let square = new Square() 的原型是 Square.prototype
- let fn = new Function() 的原型是 Function.prototype

因为 new操作符 把对象的原型地址 指定为 X.prototype

结论: 你是谁构造的, 你的原型就是谁的prototype属性对应的对象

原型公式: `对象.__proto__ === 其构造函数.prototype`

但是有一个例外

`Object.prototype.__proto__ === null`



## 类型 v.s. 类
类型是JS数据的分类, 类是针对于对象的分类, 有无数种, 常见的有 Array, Function, date, RegExp

### 数组对象
- 定义
  ```js
  let arr = [1,2,3]
  let arr = new Array(1,2,3) // 元素为 1,2,3
  let arr = new Array(3) // 长度为 3
  ```
- 自身属性
  - '0'/'1'/'2'/'length'
  -  再次强调 属性名都是字符串
- 共有属性
  - 'push'/'pop'/'shift'/'unshift'/'join'/'concat'
### 函数对象
- 定义
  ```js
  function fn(x,y){return x+y}
  let fn2 = function fn(x,y){return x+y}
  let fn = (x,y) => x + y
  let fn = new Function('x','y', 'return x+y')
  ```
- 自身属性
  'name'/'length'(接收形参数)
- 共有属性
  'call'/'apply'/'bind'

## JS终极一问

- window 是谁构造的
  - Window
  - 可以通过 constructor 属性看出构造者
- window.Object 是谁构造的
  - window.Function
  - 因为所有函数都是 window.Function 构造的
- window.Function 是谁构造的
  - window.Function
  - 因为所有函数都是 window.Function 构造的
  - 自己构造的自己？并不是这样，这是「上帝」的安排
  - 浏览器构造了 Function，然后指定它的构造者是自己


## class 语法
```js
class Square{
  static x = 1 // Square.x
  width = 0 //初始化
  constructor(width){
    this.width = width
  } 
  getArea(){ 
    return this.width * this.width 
  }
  getLength(){
    return this.width * 4
  }
  get area2(){ // 只读属性 调用不需加()
    return this.width * this.width
  }
}
```
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Classes

class中两种函数写法的区别

语法1：
```js
class Person {
  sayHi(name){}
}
// 等价于
function Person(){}
Person.prototype.sayHi = function(name){} // 共有属性
```

语法2: 
```js
class Person{
  sayHi = (name)=>{} // 多用箭头函数
}
// 等价于
function Person(){
  this.sayHi = (name) => {} // 自身属性
}
```

# JS数组
一种特殊的对象

JS其实没有真正的数组, 只是用对象模拟数组

典型数组: 元素的数据类型相同, 使用连续的内存存储, 通过数字下表获取元素

但JS的数组: 

- 元素的数据类型可以不同

- 内存不一定是连续的(对象是随机存储的)

- 不能通过数字下标, 而是通过字符串下标获取元素

## 创建数组

- 新建
  - let arr = [1,2,3]
  - let arr = new Array(1,2,3)
  - let arr = new Array(3) //长度
- 转化
  - let arr = '1,2,3'.split(',') // 通过字符串
  - let arr = '123'.split('')
  - Arrar.from('123')

  ```js
  Array.from('123') // ['1', '2', '3']
  Array.from({0:'a',1:'b',2:'c',length:3}) // ['a', 'b', 'c']  对象有 0 1 2 3的下标, 有length
  Array.from({0:'a',1:'b',2:'c',length:2}) // ['a', 'b'] 以length为准
  ```
  用下标访问数组会隐式地将数字转为字符串形式
  ```javascript
  arr[1]
  // 等价于
  arr[(1).toString()]
  ```
- 伪数组
  - 没有数组共用属性的数组
  - 原型链上没有数组的原型
    ```js
    var arr = {0:'a',1:'b',2:'c',length:3}
    let divList = document.querySelector('div') // NodeList
    Array.from(divList)
    ```
  - 一般都会将伪数组转为数组
- 合并数组
  ```js
  arr1.concat(arr2) // 返回新数组,不会修改旧数组
  ```
- 截取数组
  ```js
  arr1.slice(1) // 从第二个元素开始, 返回新数组, 不会修改原数组
  arr1.slice(0) // 全部截取 相当于浅拷贝
  ```
  JS只提供**浅拷贝**

## 增删改查
### 删
- 跟对象一样
  ```js
  let arr = ['a','b','c']
  delete arr['0'] // 长度不会改变
  arr // [empty,'b','c'] 稀疏数组
  ```
- 直接改length(不要随便改)
  ```js
  let arr = [1,2,3,4,5]
  arr.length = 1
  arr // [1]
  ```
- 删除头部的元素
  - arr.shift() // 返回被删除元素, arr被修改
- 删除尾部的元素
  - arr.pop() // 返回被删除元素, arr被修改
- 删除中间的元素
  - arr.splice(index, num) // 删除index的一个元素
  - arr.splice(index, 1, 'x') // 并在删除位置添加'x'
  - arr.splice(index, 1, 'x', 'y') // 并在删除位置添加'x','y'


### 查
- 查看所有属性名
  - 使用对象的方法, 例如 Object.keys for...in
    ```js
    var arr = [1,2,3,4,5,6,7,8,9]
    arr.x = 'x'
    // keys
    Object.keys(arr)
    // for in 
    for(let i in arr){
      console.log(`${i}:${i}`)
    } 
    ```
- 查看数字(字符串)属性名 和 值 
  - for 控制长度 从0到length-1
    ```js
    for(let i = 0; i < arr.length; i++){
      console.log(`${i}:${arr[i]}`)
    }
    ```
  - forEach/map等原型上的函数
    ```js
    arr.forEach(function (item, index) {
      console.log(`${index}:${item}`)
    })
    ```
    forEach基本等价于如下
    ```js
    function forEach(array, fn) {
      for (let i = 0; i < array.length; i++) {
        fn(array[i], i, array) // 元素 下标 数组本身
      }
    }

    forEach(['a', 'b', 'c'], function (x, y, z) {
      console.log(x, y, z)
    })
    // a 0 [ 'a', 'b', 'c' ]
    // b 1 [ 'a', 'b', 'c' ]
    // c 2 [ 'a', 'b', 'c' ]
    ```
    for循环和forEach的区别: ①for循环里面有break和continue语句 ② for是个关键字,没有函数作用域,只有块级作用域,forEach是函数作用域

- 查看单个属性
  - 和对象一样使用中括号 arr[0] !!自动将数字转成字符串!!
  - 索引越界
    - arr[arr.length] === undefined
    - arr[-1] === undefined
      ```js
      for (let i = 0; i <= arr.length; i++) {
        console.log(arr[i].toString())
      }
      // 报错 Cannot read property 'toString' of undefined
      ```
  - 查找某个元素是否在数组里
    - arr.indexOf(item) // 返回索引, 否则返回-1
  - 使用条件查找元素
    - arr.find(item => item % 2 === 0) // 找到第一个偶数
  - 使用条件查找元素的索引
    - arr.findIndex(item=>item % 2 === 0) // 找到第一个偶数的索引


### 增
不推荐使用 arr[index] = 'xxx' 的方式

- 在尾部添加元素
  - arr.push(newItem) // 修改arr 返回新长度
  - arr.push(item1, item2) // 修改arr 返回新长度
- 在头部添加元素
  - arr.unshift(newItem) // 修改arr 返回新长度
  - arr.unshift(item1, item2) // 修改arr 返回新长度
- 在中间添加元素
  - arr.splice(index,0,'x')
  - arr.splice(index,0,'x','y')

### 改
- arr[index] = 'newValue'
- splice方法
- 反转顺序
  - arr.reverse() // 修改原数组
- 自定义顺序
  - arr.sort((a,b)=>{a-b}) // 修改原数组
    ```js
    arr.sort(function (a, b) {
      if (a > b) {
        return 1
      } else if (a === b) {
        return 0
      } else {
        return -1
      }
    })
    // 简写后
    arr.sort((a,b)=>{a-b})
    ```


## 数组变换
![](https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/202212022122040.png)

不会改变原数组

### map
n变n
```js
// 每一项平方
// 1. for循环
// map方法
arr.map(item => item*item)
```

### filter
n变少
```js
arr.filter(item => item%2 === 0)
```

### reduce
n变1
```js
// 求和
let arr = [1, 2, 3, 4, 5, 6]
// 求平方 代替map
let newArr = arr.reduce((array, item) => {
  // array.push(item * item)
  // return array
  return array.concat(item * item)
}, [])
console.log(newArr) // [ 1, 4, 9, 16, 25, 36 ]

// 过滤 filter
let newArr = arr.reduce((array, item) => {
  // if (item % 2 === 0) {
  //   array.push(item)
  // }
  // return array

  // if (item % 2 === 1) {
  //   return array
  // } else {
  //   return array.concat(item)
  // }

  // return item % 2 === 1 ? array : array.concat(item)

  return array.concat(item % 2 === 1 ? [] : item)
}, [])
```
![](https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/202212022202938.png)

![](https://danmeng98.oss-cn-hangzhou.aliyuncs.com/img/202212022201217.png)