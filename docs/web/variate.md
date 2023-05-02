### var声明的变量

#### 示例一

```javascript
console.log(a)
var a
// undefined
```

#### 示例二

```javascript
console.log(a)
var a = 1
// undefined
```

等同于下面代码

```javascript
var a
console.log(a)
a = 1
// undefined
```

#### 示例三

> 非严格模式

```javascript
a = 1
var a
console.log(a)
// 1
```

### function声明的变量

#### 示例一

```javascript
log(1)
function log(mes) {
  console.log(mes)
}
//	1
```

等同于下面代码

```javascript
function log(mes) {
  console.log(mes)
}
log(1)
//	1
```

#### 示例二

> 函数表达式不会被提升

```javascript
log(5)
var log = function (mes) {
  console.log(mes)
}
//	报错log is not a function
```

### function里用var声明变量

#### 示例一

> var声明的变量有函数作用域

```javascript
var a = 1
function foo() {
  var a = 2
  console.log(a)
}
foo()
console.log(a)
//	先输入2，后输入1
```

#### 示例二

```javascript
function foo() {
  a = 1
  console.log(a)	//	输入1
  var a
}
foo()
console.log(a)	//	报错a is not defined
```

### 函数优先

同一个变量申明var和function

#### 示例一

```javascript
foo()
var foo
function foo() {
  console.log(1)
}
foo = function () {
  console.log(2)
}
//	1
```

等同于下面代码

```javascript
function foo() {
  console.log(1)
}
foo()	//	1
foo = function () {
  console.log(2)
}
```

#### 示例二

> 最后的函数声明会覆盖之前的函数声明

```javascript
foo()
function foo(){
  console.log(1);
}
foo()
function foo(){
  console.log(2);
}
foo()
function foo(){
  console.log(3);
}
foo()
//	foo申明三次，调用四次，调用结果都是3
```

#### 示例三

```javascript
foo()
function foo() {
  console.log(1)
}
var foo
foo()
foo = function () {
  console.log(2)
}
foo()
function foo() {
  console.log(3)
}
foo()
//	依次输入3,3,2,2
```

等同于下面代码

```javascript
function foo() {
  console.log(3)
}
foo()	//	3
foo()	//	3
foo = function () {
  console.log(2)
}
foo()	//2
foo()	//2
```

### 普通块内部申明函数

```javascript
function foo() {
  console.log(b) // undefined
  b() //TypeError: b is not a function
  var a = true
  if (a) {
    function b() {
      console.log(2)
    }
  }
}
foo()
```

### 总结

- 提升分为函数声明提升和变量声明提升
- 声明变量用var，声明函数用function
- 变量提升会将变量提升到自己所在作用域的顶部
- 函数表达式不存在提升的机制
- 函数声明和变量声明同时声明同一个标识符时，函数声明优先
- 多个函数声明同一个标识符时，最后一个声明覆盖先前的声明