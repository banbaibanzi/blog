## 关闭按钮

```css
.box {
  position: relative;
  padding: 10px;
  width: 200px;
  height: 100px;
  border: 1px solid #e1e1e1;
  &:after {
    clear: both;
    content: ".";
    display: block;
    height: 0;
    line-height: 0;
    overflow: hidden;
  }
  .close {
    position: absolute;
    top: 10px;
    right: 10px;
    display: block;
    float: right;
    width: 26px;
    height: 26px;
    cursor: pointer;
    &::before,
    &::after {
      position: absolute;
      content: "";
      top: 50%;
      left: 50%;
      height: 20px;
      margin-left: -1px;
      margin-top: -10px;
      border-left: 2px solid #999c9f;
    }
    &::before {
      transform: rotate(45deg);
      -webkit-transform: rotate(45deg);
    }
    &::after {
      transform: rotate(-45deg);
      -webkit-transform: rotate(-45deg);
    }
  }
}
```

## 未知宽度正方形

```css
.outer {
  display: flex;
}
.inner {
  flex: 1;
  &::after {
    display: block;
    content: "";
    padding-bottom: 100%;
  }
  &.inner:nth-child(1) {
    background-color: red;
  }
  &.inner:nth-child(2) {
    background-color: blue;
  }
  &.inner:nth-child(3) {
    background-color: green;
  }
}
```
