## input限制1位小数

```html
<input
          type="text"
          v-model.number="aaa"onkeyup="value=value.replace(/^\D*(\d*(?:\.\d{0,1})?).*$/g, '$1')"
            @blur="aaa = $event.target.value"
        />
```

