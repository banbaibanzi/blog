## 文档

### ES6

链接：<a href="https://es6.ruanyifeng.com/" target="_blank">https://es6.ruanyifeng.com/</a>

### Array

链接：<a href="https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array" target="_blank">Array</a>

## 常用数组方法

### [...arr]解构

#### 数组复制

只能深拷贝一层，第一层（基本类型）拷贝不改变原数组；深层是对象或数组时仍会改变原数组

示例：`arr_copy = [...arr]`

```javascript
const arr = [1, 2, 3, { type: 'vite' }]
const arr_copy = [...arr]
arr_copy[3].type = 'pinia'
console.log(arr) // [1,2,3,{type: 'pinia'}]
console.log(arr_copy) // [1,2,3,{type: 'pinia'}]
```

#### 连接、合并数组

示例：`newArr=[...arr,...arr1]`

```javascript
const arr = [1, 2, 3]
const arr1 = [4, 5, 6]
const newArr = [...arr, ...arr1]
console.log(newArr) //  [1, 2, 3, 4, 5, 6]
```

### map()

#### 提取部分属性值

```javascript
const arr = [
  { code: '12', type: 'js', id: 1 },
  { code: '23', type: 'css', id: 2 }
]
const list = arr.map(({ id, type }) => {
  return { id, type }
})
console.log(list)
// [{id:1,type:'js'},{id:2,type:'css'}]
```

### some()

简介：不改变原数组，只要有一个满足条件就返回true

```javascript
const arr = [1, 2, 3, 4]
console.log(arr.some((v) => v > 3))
// true
console.log(arr.some((v) => v > 4))
// false
```

### every()

简介：所有属性都满足返回true

```javascript
const arr = [1, 2, 3, 4]
console.log(arr.every((v) => v > 0))
// true
console.log(arr.every((v) => v > 1))
// false
```

### reduce()

#### 累加器

```javascript
const arr = [1, 2, 3, 4]
console.log(arr.reduce((pre, cur) => pre + cur))
// 10
```

#### 将数组转换为对象

```javascript
const arr = [
  {
    id: 1,
    type: 'vue'
  },
  {
    id: 2,
    type: 'vite'
  },
  {
    id: 3,
    type: 'pinia'
  }
]
let result = arr.reduce((pre, cur) => {
  return { ...pre, [cur.id]: cur }
}, {})
console.log(result)
// {1:{id:1,type:'vue'},2:{id:2,type:'vite'},3:{id:3,type:'pinia'}}
```

#### 求数组的最大值与最小值

```javascript
const arr = [1, 2, 3, 4]
let minValue = arr.reduce((pre, cur) => Math.min(pre, cur))
console.log(minValue)// 1
let maxValue = arr.reduce((pre, cur) => Math.max(pre, cur))
console.log(maxValue)// 4
```



### Array.from()

```javascript
const arrayLike = {
  0: 'vue',
  1: 'vite',
  2: 'pinia',
  length: 3
}
const arr = Array.from(arrayLike)
// ['vue', 'vite', 'pinia']
```

#### new Set()

简介：可以去重

```javascript
const arr = [1, 1, 2, 3, 2, 4]
const set = new Set(arr)
console.log(...set)	// 1,2,3,4
console.log(Array.from(set))	// [1,2,3,4]
```

### includes()

简介：判断数组中是否含有某个元素，返回true/false。是`indexOf()!==-1`的优化补充

```javascript
const arr = [1, 2, 3, 4]
console.log(arr.includes(3))	// true
console.log(arr.includes(5))	// false
```

### find(item,index,arr)

简介：查找数组中符合条件的第一个元素

```javascript
const arr = [1, 2, 3, 4, 3, 5, 3]
console.log(arr.find((v) => v > 3))	// 4
```

### findIndex()

简介：返回索引

```javascript
const arr = [1, 2, 3, 4, 3, 5, 3]
console.log(arr.findIndex((v) => v > 3))	// 3
```

## 常用操作

### 解构法

简介：移除数组中某个元素

```javascript
const [first, ...rest] = [1, 2, 3, 4, 5]
console.log(first, rest)
// first:1  rest:[2,3,4,5]
```

### Array.push.apply()

简介：数组合并，原数组发生改变

```javascript
const arr = [1, 2, 3]
const arr1 = [4, 5, 6]
const arr2 = arr.push.apply(arr, arr1)
console.log(arr) // [1, 2, 3,4, 5, 6]
console.log(arr1) //  [4, 5, 6]
console.log(arr2) //  6
```

### 判断一个数据是否为数组

示例

```javascript
const arr = [1, 2, 3]
const obj = { type: 'vite' }
```

#### Array.isArray()

```javascript
console.log(Array.isArray(arr)) //  true
console.log(Array.isArray(obj)) //  false
```

#### 原型 `prototype + toString + call`

```javascript
console.log(Object.prototype.toString.call(arr)) //  "[object Array]"
console.log(Object.prototype.toString.call(obj)) //  "[object Object]"
```

#### 构造函数 `constructor`

```javascript
console.log(arr.__proto__.constructor.name) //  "Array"
console.log(obj.__proto__.constructor.name) //  "Object"
```

#### instanceof

```javascript
console.log(arr instanceof Array) //  true
console.log(obj instanceof Array) //  false
```

### 复制新数组，不影响原数组

示例：`let arr = [1, 2, 3]`

#### 先JSON.stringify( ) 后 JSON.parse( )

#### Object.assign() || [...arr] || concat()

简介：只适用于基础类型，不适用对象数组

```javascript
let newArr = Object.assign([], arr) // let newArr = [...arr] || [].concat(arr)
newArr.push(4)
console.log(arr) // [1, 2, 3]
console.log(newArr) // [1, 2, 3,4]
```



