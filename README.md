# 前端资料汇总

## 使用步骤
1. 使用 node v10 安装 gitbook-cli，gitbook-cli 无法与 node v12+ 兼容。推荐使用 nvm 安装并切换 node 版本。
```
nvm use 10
npm install gitbook-cli -g
```

2. 安装 gitbook 插件
```
gitbook install
```

3. 运行开发环境
```
gitbook serve
```

4. 编译生产环境代码
```
gitbook build
```