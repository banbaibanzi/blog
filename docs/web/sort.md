### 常规写法

> 不够均匀，不推荐使用

```javascript
function shuffle(arr) {
  arr.sort(() => Math.random() - 0.5)
}
```

### 洗牌算法

简介：Fisher–Yates shuffle

```javascript
function shuffle(arr) {
    let i = arr.length;
    while (--i) {
        let j = Math.floor(Math.random() * i);
        [arr[j], arr[i]] = [arr[i], arr[j]];
    }
}
```

