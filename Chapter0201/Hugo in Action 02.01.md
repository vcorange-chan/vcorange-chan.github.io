---
title: Hugo in Action 02.01
updated: 2022-10-06 23:38:41Z
created: 2022-10-06 21:04:37Z
latitude: 1.35537940
longitude: 103.86774440
altitude: 0.0000
---

# 1.0 建立网站骨架
使用`hugo new site`命令，`yaml`格式，创建名为acme-corporation的网站骨架
```
hugo new site acme-corporation --format yaml
```

---
# 2.0 补充所需git用法
## git建立代码库
```
git init -b main
git add . && git commit -m "initial commit"
gh repo create
```
注意：不设置readme等文件，不克隆。

## git建立checkpoint
```
git status
git checkout -b 名称
```

```
After Each Checkpoint
$ git status
$ git add .
$ git status
$ git commit -m "Checkpoint 23 completed, interfaces"
$ git push origin checkpoint-23-interfaces
$ git checkout master
$ git merge checkpoint-23-interfaces
$ git push
```

---
# 3.0 文件结构
`hugo new`建立了六个文件夹
- archetypes : 包含内容(content)文件的模板。
- content : 包含网站内容。
- data : 包含存储结构，例如`YAML`,  `TOML`, `CSV`, 或者`JSON`文件。是网站的全局变量
- layouts : 覆盖主题的一部分。Hugo可灵活混搭主题页面、定制个性页面。此文件夹包含所有个性化主题。
- themes : 包含当前内容制作所用代码，可用Go模板语言写主题，亦可添加已有主题。
- config : 网站设计文件。包含网站初始数据例如：主题名称、主题参数。默认是一个`config.yaml`文件。Hugo支持一个配置文件分为多个配置文件之组合。
- static : 存储例如pdf、图片这样的静态内容。

除上述文件之外，通常还会遇到如下文件

- assets ： 放置网站全局所需之未处理的源代码。这些文件在编译中可执行。Hugo可重塑图像、包的大小，可缩小JavaScript文件，转化SCSS成CSS。
- public ：Hugo默认输出目录，即Hugo命令所生成的部署在CDN上的HTML。
- resources : Hugo在此文件夹中缓存数据处理时的大型操作。构建网站时，该文件中的数据应可重复使用，应有版本控制。例如图像处理结果。
- go.mod和go.sum ：Hugo模型以此同步独立项目。应版本控制。
- vendor : 存Hugo 模型引入的第三方依赖。
- node__modules, package.json, package-lock.json, package.hugo.json ： 用JavaScript生态关联整合Hugo。
- .github 和 netlify.toml ：用Github和Netlify服务关联Hugo。
- api : 定制化应用程序接口。