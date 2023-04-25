## map

### 提取部分属性值

```javascript
let arr = [
      { code: "12", type: "js", id: 17 },
      { code: "23", type: "css", id: 19 }
    ];
    let list = arr.map(({ type, id }) => {
      return { type, id };
    });
```

## input限制1位小数

```html
<input
          type="text"
          v-model.number="aaa"onkeyup="value=value.replace(/^\D*(\d*(?:\.\d{0,1})?).*$/g, '$1')"
            @blur="aaa = $event.target.value"
        />
```

