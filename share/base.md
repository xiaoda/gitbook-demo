# 前端基础培训材料

# 【1】Git
## [基础命令](https://lexiangla.com/docs/9ff25c1c0bce11ec865c1e2e701dac04?company_from=385abcf0dd9d11e8a11752540005f435)[【备用链接】](https://fe.anchnet.com/2021/Git%E5%B8%B8%E7%94%A8%E5%91%BD%E4%BB%A4%E6%B1%87%E6%80%BB/)
### git clone
克隆仓库

### git pull / git fetch
拉取代码

### git diff / git diff --staged
查看代码修改

### git add . / git add xxx
添加到暂存区

### git status
查看当前状态

### git commit -m '解决 xxx 问题'
提交代码

### git push
推送代码

## 分支使用
### git checkout xxx / git checkout -b xxx
切换分支

### git merge xxx
合并分支

### git rebase xxx
另一种合并分支的方式：Reapply commits on top of another base tip

### git branch -d xxx
删除分支

## 解决冲突
经过沟通保留双方需要的代码片段

## [代码回滚](https://lexiangla.com/docs/909861520afd11ec8b19568564ad7a16?company_from=385abcf0dd9d11e8a11752540005f435)[【备用链接】](https://fe.anchnet.com/2021/%E6%8A%80%E6%9C%AF%E5%88%86%E4%BA%AB%E4%B9%8BGit%E6%92%A4%E9%94%80%E6%8F%90%E4%BA%A4/)
### git reset xxx / git reset --hard xxx
回滚到之前的某个版本

### git revert xxx
撤销某一次提交

## 其它常用命令
### git config / git config --global
查看或修改 git 配置信息

### git branch / git branch -r
查看或创建分支

### git log
查看提交日志

### git tag
查看或创建标签

### git stash
暂存代码

### git blame
查看文件修改记录

## .gitignore
gitignore 的作用是帮助我们在执行 git add 时将我们指定的一些文件自动排除在外，不提交到 Git 当中。

```
node_modules
/build
/dist
/.idea
/.vscode
.DS_Store
```

## 注意事项
1. 尽量使用命令行而不是各类工具操作 Git
2. Git 操作出现问题或意料之外的情况时，停止操作、保留命令行并及时向组长/主管求助。
3. git push -f 强制推送很危险，绝大部分时候不允许使用。
4. 在进行有风险、没有把握的操作时，先对分支进行备份。

## 疑难问题
### 改变文件名字母大小写时，Git 为什么不记录，我该怎么办？
Mac / Windows 操作系统默认对字母大小写不敏感，因此 Git 无法识别到文件名的变化。使用临时名称、改两次名字并提交可以解决。

### 提交被误删了怎么办？
git reflog / git cherry-pick 搭配使用可以找回。

## 参考资料
1. [git 使用简易指南](https://www.bootcss.com/p/git-guide/)

# 【2】前端项目注意事项

## 项目依赖
### [package.json](https://docs.npmjs.com/cli/v7/configuring-npm/package-json/)
每个项目的根目录下面，一般都有一个 package.json 文件，定义了这个项目所需要的各种模块，以及项目的配置信息（比如名称、版本、许可证等元数据）。npm install 命令根据这个配置文件，自动下载所需的模块，也就是配置项目所需的运行和开发环境。

``` json
{
  "dependencies": {
    "vue": "2.6.14",
    "react": "~17.0.2"
    "angular": "^13.0.1"
  },
  "devDependencies": {},
  "scripts": {
    "start": "...",
    "dev": "...",
    "watch": "...",
    "test": "...",
    "build": "...",
    "build:prod": "..."
  }
}
```

### [package-lock.json](https://docs.npmjs.com/cli/v7/configuring-npm/package-lock-json/) / [yarn.lock](https://classic.yarnpkg.com/en/docs/yarn-lock/)
该文件旨在跟踪被安装的每个软件包的确切版本，以便产品可以以相同的方式被 100％ 复制（即使软件包的维护者更新了软件包）。package-lock.json 会固化当前安装的每个软件包的版本，当运行 npm install 时，npm 会使用这些确切的版本。package-lock.json 文件需要被提交到 Git 仓库，以便被其他人获取（如果项目是公开的或有合作者，或者将 Git 作为部署源）。

## [代码格式化](https://lexiangla.com/docs/5a52b0dc0bc211ec9c20d2f844567384?company_from=385abcf0dd9d11e8a11752540005f435)[【备用链接】](https://github.com/297087852/docs/tree/main)
***关闭编辑器的代码格式化功能！***

### [ESLint](https://eslint.org/)[【ESLint 规则】](https://cn.eslint.org/docs/rules/)
JS 语法规则和代码风格的检查工具，可以用来保证写出语法正确、风格统一的代码。

### 规则
1. [Standard](https://standardjs.com/rules-zhcn.html)
2. [Airbnb](https://lin-123.github.io/javascript/)
3. [Google](https://google.github.io/styleguide/jsguide.html)

### 要求
1. 不允许将带有 ESLint 报错的代码提交到远程

### [.editorconfig](https://editorconfig.org/)
帮助开发人员在不同的编辑器和 IDE 之间定义和维护一致的编码样式。

```
root = true

[*]
indent_style = space
indent_size = 2
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
```

### 其它
1. [Prettier](https://prettier.io/)
2. [Stylelint](https://stylelint.io/)
3. [commitlint](https://commitlint.js.org/)

## 环境变量
1. 接口地址等变量不可以硬编码在项目中，建议使用环境变量作区分。
2. 调试数据尽量使用环境变量定义以确保调试被限制在特定环境里

## console.log
1. 临时调试，用完删除。
2. 可用于重要模块的日志打印

# 【3】前端开发实用工具
1. [Chrome DevTools](https://developer.chrome.com/docs/devtools/)
2. iOS Simulator: Mac 平台 Xcode 自带 iPhone / iPad 仿真模拟器。
3. [微信开发者工具](https://developers.weixin.qq.com/miniprogram/dev/devtools/download.html)：主要用于开发微信小程序，也可用于开发和调试公众号网页。
4. [Postman](https://www.postman.com/) / [Apifox](https://www.apifox.cn/): API 接口模拟请求工具
5. [Fiddler](https://www.telerik.com/fiddler) / [Charles](https://www.charlesproxy.com/): 网络抓包、手机网络代理等功能

# 【4】前端代码最佳实践

## JS
### if 条件判断
``` js
if (a === true) {
  doSomething()
}

// 类似的
const b = condition ? true : false
```

建议
``` js
if (a) {
  doSomething()
}

const b = Boolean(condition)
const b = !!condition
```

### if 条件判断 2
``` js
if (a == 1) {
  doThis()
} else if (a == 2) {
  doThat()
} else if (a == 3) {
  doWhatever()
} else {
  doNothing()
}
```

建议
``` js
switch (a) {
  case 1:
    doThis()
    break
  case 2:
    doThat()
    break
  case 3:
    doWhatever()
    break
  default:
    doNothing()
}
```

### if 条件判断 3
``` js
let a
if (condition) {
  a = 1
} else {
  a = 2
}
```

建议
``` js
const a = condition ? 1 : 2
```

### if 条件判断 4
``` js
if (!a) {
  if (b) {
    if (!c) {
      doThis()
    } else {
      doThat()
    }
  } else {
    doWhatever()
  }
} else {
  doNothing()
}
```

建议
``` js
if (a) {
  doNothing()
} else {
  if (b) {
    if (c) {
      doThat()
    } else {
      doThis()
    }
  } else {
    doWhatever()
  }
}
```

### indexOf
``` js
const stringContainX = a.indexOf('x')
const arrayContainX = b.indexOf('y')
```

建议
``` js
const stringContainX = a.includes('x')
const stringContainX = a.startsWith('x')
const stringContainX = a.endsWith('x')
const arrayContainX = b.includes('y')
```

### 数组方法的选择
``` js
const a = array.forEach(...)
array.map(...)
```

建议
``` js
array.forEach(...)
const b = array.map(...)
```

### 删除数组元素
``` js
array.forEach((item, index) => {
  if (index % 2 === 0) {
    array.splice(index, 1)
  }
})
```

### 复杂类型的引用传值
``` js
const a = {x: 1}
const b = a
b.x = 2
console.log(a.x)
```

建议
``` js
// 深度克隆
const b = JSON.parse(JSON.stringify(a))
```

### 运行时报错：对象为空
*Can not read property x of undefined*
``` js
const b = a.x
```

建议
``` js
const b = a ? a.x : null

// or
const b = a?.x
```

## React
1. [React Hook](https://lexiangla.com/docs/3babd20e0bd011ec9abb6e2d8f959e52?company_from=385abcf0dd9d11e8a11752540005f435)[【备用链接】](https://github.com/TwoNingMengTea/reack-hook/blob/master/react-hooks.md)
2. [React关于shouldComponentUpdate、PureComponent和React.memo](https://lexiangla.com/docs/4136d1300bd811ecb0be32c75543b97e?company_from=385abcf0dd9d11e8a11752540005f435)

## Vue
1. [vue之keep-alive的应用](https://lexiangla.com/docs/5672c9420bd211ec9efa762d8987966a?company_from=385abcf0dd9d11e8a11752540005f435)

## 综合
### 组件、代码复用
1. 能复用尽量复用，避免重复造轮子
2. 可以复用的模块、组件、方法等尽量提取出来
3. 公共代码是可以修改的，但要谨慎考虑各种情况。

### 数据和模板分离
1. 多个相同或类似的 HTML 结构尽量使用数据循环输出模板内容

### 问题解决
1. 遇到问题先自行思考或搜索
2. 比报错更重要的是具体的错误信息
3. 一段时间内无法解决的问题及时向组长/主管求助
4. 不要用猥琐的方式（奇巧淫技）解决问题

### 代码可读性
1. 代码可读性在某种程度上比代码运行效率更重要，为了可读性降低一点效率是可以接受的。
2. 对代码进行必要的注释，特别是核心模块、公共组件、通用方法、重要参数等。

## 参考资料
1. [内部基础规范](https://gitlab.51idc.com/frontend/standard-summary/-/blob/master/%E5%9F%BA%E7%A1%80%E8%A7%84%E8%8C%83.md)
2. [编码规范 by @mdo](https://codeguide.bootcss.com/)
3. [ES6 入门教程 by 阮一峰](https://es6.ruanyifeng.com/)
4. [Javascript 秘密花园](http://bonsaiden.github.io/JavaScript-Garden/zh/)

# 【5】前后端联调

1. [前后端联调问题点](https://github.com/xiaoda/web-api-issues)
2. [后端 API 问题认定方法](https://lexiangla.com/docs/772932420afc11ecaee0762d8987966a?company_from=385abcf0dd9d11e8a11752540005f435)[【备用链接】](https://fe.anchnet.com/2020/%E5%90%8E%E7%AB%AFAPI%E9%97%AE%E9%A2%98%E8%AE%A4%E5%AE%9A%E6%96%B9%E6%B3%95/)

# 【6】前端进阶课题
## 经典问题
1. 浏览器从输入 URL 到页面加载发生了什么？

## 技术分享
1. 前端技术分享：Canvas [【分享材料】](https://lexiangla.com/docs/dde1f7600afe11ec9bb41225d70f91d9?company_from=385abcf0dd9d11e8a11752540005f435)[【分享视频】](https://lexiangla.com/docs/4e271aa00aff11eca4fe7625e6a790b5?company_from=385abcf0dd9d11e8a11752540005f435)

2. Jenkins + Git + Nginx 自动化部署前端项目[【分享材料】](https://lexiangla.com/docs/d13f53d60b0311eca0d50e1a3ac2541b?company_from=385abcf0dd9d11e8a11752540005f435)

3. 前端技术分享：Electron 客户端[【分享材料】](https://lexiangla.com/docs/27cd397a113f11ec93926aa02128f815?company_from=385abcf0dd9d11e8a11752540005f435)[【分享视频】](https://lexiangla.com/docs/5224fb32114d11ec9e5a9abf86510192?company_from=385abcf0dd9d11e8a11752540005f435)

4. 前端微服务及框架 qiankun 技术分享[【分享材料】](https://lexiangla.com/docs/a76fea1e150511ec9ad96ac746018b05?company_from=385abcf0dd9d11e8a11752540005f435)[【分享视频】](https://lexiangla.com/docs/208490fe154611ec97b72eeb24d9f88e?company_from=385abcf0dd9d11e8a11752540005f435)
