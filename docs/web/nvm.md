## nvm-windows下载

[nvm下载链接](https://github.com/coreybutler/nvm-windows/releases)点击最新版本nvm-setup.zip下载安装即可

## 配置环境变量（默认配置，可忽略）

环境变量打开方式：右键此电脑 > 属性 > 高级系统设置 > 环境变量

打开用户变量更改如下配置：

```javascript
变量名：NVM_HOME（指向nvm安装目录），变量值：H:\dev_tools\nvm 
变量名：NVM_SYMLINK（指向nodejs安装目录），变量值：H:\dev_tools\nodejs 
变量名PATH中添加%NVM_HOME%及%NVM_SYMLINK%
```

## nvm常用指令

```javascript
nvm -v //查看nvm版本
nvm list available // 查看可安装的nodejs版本
nvm install 18.14.0 64-bit //安装指定版本的nodejs 64位
nvm ls //查看已安装nodejs版本 同nvm list
nvm use 18.14.0 //使用指定版本的nodejs（管理员运行）
nvm uninstall 18.14.0 //删除指定版本的nodejs
npm config ls //查看npm配置
npm install -g cnpm --registry=https://registry.npm.taobao.org //安装淘宝镜像cnmp替代npm（建议cnpm与npm同级，可以同时指向cnpm和npm,可以不用再次配置环境变量）
cnpm config get registry  //验证cnpm是否可用
```

## 配置全局node_global

在node安装目录创建 node_global 和 node_cache 文件夹

配置node_global及node_cache（缓存区)

```
npm config set prefix "H:\dev_tools\nvm\node_global"
```

```
npm config set cache "H:\dev_tools\nvm\node_cache"
```

## 配置node_global环境变量

```
H:\dev_tools\nvm\node_global
```