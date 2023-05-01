## 以监听滚动条为例

```javascript
function showTop() {
  let scrollTop = document.body.scrollTop || document.documentElement.scrollTop
  console.log('滚动条位置：' + scrollTop)
}
window.onscroll = showTop
```

## 防抖(debounce)

简介：第一次触发事件时，不立即执行函数,若计时器的时间间隔之内没有再次触发事件就执行;**在计时器时间间隔内又触发新的事件，会清除计时器，重新计时**

```javascript
function debounce(fn, delay) {
  let timer = null
  return function () {
    if (timer) {
      clearTimeout(timer)
    }
    timer = setTimeout(fn, delay)
  }
}
```

```javascript
window.onscroll = debounce(showTop, 1000)
```

调用

```javascript
function fn() {
  console.log(1)
}
const resultFn = debounce(fn,1000)
```

## 节流(throttle)

简介：第一次触发的事件正在执行时，**计时器设定时间内又触发新的事件，不会再执行**，相当于冷却

```javascript
function throttle(fn, delay) {
  let valid = true
  return function () {
    if (!valid) {
      return false
    }
    valid = false
    setTimeout(() => {
      fn()
      valid = true
    }, delay)
  }
}
```

```javascript
function fn() {
  console.log(1)
}
const resultFn = throttle(fn, 1000)
```

## 防抖指令

### 防抖方法

```javascript
/**
 * 防抖
 * immediate  true点击立即执行  false点击后执行
*/
export const debounce = (func, delay = 600, immediate = true) => {
  let timer
  return function (...args) {
    const context = this
    timer && clearTimeout(timer) // timer 不为null
    if (immediate) {
      const callNow = !timer // 第一次会立即执行，以后只有事件执行后才会再次触发
      timer = setTimeout(() => {
        timer = null
      }, delay)
      if (callNow) func.apply(context, args)
    } else {
      timer = setTimeout(() => {
        func.apply(context, args)
      }, delay)
    }
  }
}
```

### vue3防抖指令

#### 立即执行

```javascript
<button
    v-debounce="[
      () => {
        handleClick(params);
      }
    ]"
  >
    防抖--立即执行
  </button>
```

#### 后执行

```javascript
<button
    v-debounce="[
      () => {
        handleClick(params);
      },
      300,
      false
    ]"
  >
    防抖--后执行
  </button>
```

#### 指令

```javascript
 app.directive('debounce', {
    mounted (el, binding, vnode, prevNode) {
      const [func, delay, immediate] = binding.value
      const debounced = debounce(func, delay, immediate)
      el.addEventListener('click', debounced)
    },
    beforeUnmont () {
      console.log('beforeUnmont', el._debounced)
      el.removeEventListener('click', el._debounced)
    }
  })
```

