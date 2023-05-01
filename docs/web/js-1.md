## 判断属性是否存在

> property 为属性名的变量

示例：`let obj = { id: 1, type: 'vue' }`

### Object.prototype.hasOwnProperty.call

```javascript
let obj2 = new Object({ id: 2 })
Object.prototype.name = '瓦尔特'
Object.prototype.hasOwnProperty.call(obj2, 'id') //  true
Object.prototype.hasOwnProperty.call(obj2, 'name') //  false
```

### property in obj

```javascript
'id' in obj //true
```

### Reflect.has(obj, property)

```javascript
Reflect.has(obj, 'id')	//	true
```

> 其他用法

- js的内置对象，无构造函数，可以用它遍历对象的key

  示例：`Reflect.ownKeys(obj) // ['id', 'type']`

- 给对象添加一个属性

  示例：`Reflect.set(obj, 'value', '123')	//	true`

### obj.hasOwnProperty(property）

> 判断是否是对象的自有属性（原型链上的属性不会读取）

```javascript
obj.hasOwnProperty('id1')	//	true
```

### Object.hasOwn(obj, property)

简介：判断自有属性

​			注意浏览器版本兼容问题，谷歌 93 以上版本支持

> MDN推荐用该方法替换掉 hasOwnProperty。原话是这样的：“ 建议使用此方法替代 Object.hasOwnProperty()，因为它适用于使用 Object.create(null) 创建的对象以及覆盖了继承的 hasOwnProperty() 方法的对象。尽管可以通过在外部对象上调用 Object.prototype.hasOwnProperty() 解决这些问题，但是 Object.hasOwn() 更加直观。”

## 遍历数组

```javascript
for,for...in,for...of,forEach,map
```

### for...in

> 遍历数组下标，遍历对象key

### for...of

> 遍历数组值，不可遍历对象，报错`obj is not iterable`不可迭代

### forEach

> 会改变原数组

### map

> 返回新数组