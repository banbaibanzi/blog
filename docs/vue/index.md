## vite

官网：<a href="https://cn.vitejs.dev/" target="_blank">https://cn.vitejs.dev/</a>

安装依赖

```javascript
npm create vite@latest
```

### 构建一个Vite+Vue项目

```javascript
npm create vite@latest my-vue-app -- --template vue
```



### vite-plugin-warmup

简介：vite文件预热插件，可以尽早的处理一些必须加载的vite文件

链接：<a href="https://github.com/bluwy/vite-plugin-warmup" target="_blank">https://github.com/bluwy/vite-plugin-warmup</a>

安装依赖

```javascript
npm install vite-plugin-warmup
```

配置

```javascript
// vite.config.js
import { defineConfig } from 'vite'
import { warmup } from 'vite-plugin-warmup'

export default defineConfig({
  plugins: [
    warmup({
      // warm up the files and its imported JS modules recursively
      clientFiles: ['./**/*.html', './src/components/*.jsx']
    })
  ]
})
```

## Pinia

简介：Vue 的存储库

官网：<a href="https://pinia.web3doc.top/" target="_blank">https://pinia.web3doc.top/</a>

安装

```javascript
npm install pinia
```

## 自动按需加载

### unplugin-auto-import

简介：加载import APIs

链接：<a href="https://github.com/antfu/unplugin-auto-import" target="_blank">https://github.com/antfu/unplugin-auto-import</a>

安装

```
npm i -D unplugin-auto-import
```

### vite-auto-import-resolvers

简介：`unplugin-auto-import`的`vite resolvers`,主要处理`vite`项目本身的`api`按需自动引入

链接：<a href="https://github.com/dishait/vite-auto-import-resolvers" target="_blank">https://github.com/dishait/vite-auto-import-resolvers</a>

安装

```
npm i vite-auto-import-resolvers -D
```

### unplugin-vue-components

简介：加载components

链接：<a href="https://github.com/antfu/unplugin-vue-components" target="_blank">https://github.com/antfu/unplugin-vue-components</a>

安装

```
npm i unplugin-vue-components -D
```