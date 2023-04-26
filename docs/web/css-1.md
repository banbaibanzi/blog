## mixin

引用示例：`@include webkit(transition, all 0.3s ease 0s);`

```css
/* 属性前缀 */
@mixin webkit($type, $value) {
  -webkit-#{$type}: $value;
  -moz-#{$type}: $value;
  -ms-#{$type}: $value;
  -o-#{$type}: $value;
  #{$type}: $value;
}

/* 属性后缀 */
@mixin webkitA($type, $value) {
  #{$type}: -webkit-#{$value};
  #{$type}: -moz-#{$value};
  #{$type}: -ms-#{$value};
  #{$type}: -o-#{$value};
  #{$type}: $value;
}
```

## extend

引用示例：`@extend %clearfix; `

```css
/* 清除浮动 */
%clearfix {
  &:after {
    clear: both;
    content: ".";
    display: block;
    height: 0;
    line-height: 0;
    overflow: hidden;
  }
  *height: 1%;
}
```

## 页面变灰

```html
html {
  -webkit-filter: grayscale(100%);
  -moz-filter: grayscale(100%);
  -o-filter: grayscale(100%);
  filter: grayscale(100%);
  filter: progid:DXImageTransform.Microsoft.BasicImage(grayscale=1);
}
```

## 省略号

```css
/* 单行文本省略号 */
.ellipsis {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
/* 多行文本省略号 */
.ellipsis {
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
}
```

