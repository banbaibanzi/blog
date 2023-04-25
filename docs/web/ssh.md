## ssh 配置

### git 用户名和邮箱配置

```
git config --global user.name "用户名"
git config --global user.email "邮箱"
查询git本地配置
git config --global -l
```

### 打开 cmd 命令行并生成 ssh

```
win + r > cmd
ssh-keygen -t rsa -C "xxx@xx.com"
```

### 配置多个 ssh

待定--未验证

```
ssh-keygen -t rsa -C "xxx@xx.com" -f ~/.ssh/github_id_rsa
```

```
ssh-keygen -t rsa -C "xxx@xx.com" -f ~/.ssh/gitlab_id_rsa
```

### ssh 配置

```
命令行输入 cd ~/.ssh 进入目录（ls），切换到 id_rsa.pub 输入 cat id_rsa.pub 即可打开 ，
复制内容(key)打开github　　Settings > SSH and GPG keys > New SSh keys 将复制的内容（key）粘贴到Key中，填写title即可。
```

## vscode

### 官网

<a href="https://code.visualstudio.com/" target="_blank">vscode 链接</a>

### 解决 vscode 下载速度缓慢问题

复制官网下载链接，例如

`https://az764295.vo.msecnd.net/stable/fd6f3bce6709b121a895d042d343d71f317d74e7/VSCodeUserSetup-x64-1.54.2.exe`，

将`az764295.vo.msecnd.net`替换为国内源`vscode.cdn.azure.cn`即可

### 报错

```
vscode host key verification failed
```

出现如上提示，可执行`ssh -T git@github.com`，出现`Are you sure you want to continue connecting (yes/no)?`输入`yes`即可

### 扩展

| 扩展                                                      | 说明                   |
| --------------------------------------------------------- | ---------------------- |
| Chinese (Simplified) Language Pack for Visual Studio Code | 中文简体语言包         |
| SFTP                                                      | 代码上传服务器         |
| any-rule                                                  | 正则大全               |
| Prettier - Code formatter                                 | Prettier 代码规范      |
| Vue 3 Snippets                                            | vue3 代码提示          |
| JavaScript (ES6) code snippets                            | ES6 代码提示           |
| Auto Close Tag                                            | 自动添加关闭标签       |
| Auto Rename Tag                                           | 同步修改前后标签名     |
| HTML CSS Support                                          | css 自动补齐           |
| Git History                                               | 查看历史记录，更为直观 |
| GitLens — Git supercharged                                | 显示当前行代码提交信息 |
| Image preview                                             | 图片显示               |
| Better Comments                                           | 注释颜色               |
| Polacode-2022                                             | 代码截图               |
| vscode-icons                                              | icon 主题              |
| Vue VSCode Snippets                                       | 代码模板               |
