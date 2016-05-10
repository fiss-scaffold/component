# 组件说明文档

## 组件开发规范

### 环境依赖
+ [nodejs](https://nodejs.org/en/)
+ [fiss](https://github.com/zhangyihua/fiss)全局安装**最新版本**

### 新建组件
通过模板新建一个组件的目录，比如在本地新建名字为`myComp`的组件
```bash
mkdir myComp
cd myComp
fiss init componet
```

### 版本号
+ 组件初始化时，是没有发布版本的，`component.json`会有一个默认的版本号`0.0.0`。
+ 版本号的规范请参考[semver](https://github.com/npm/node-semver)
+ 查看版本号或者更新版本号请参考[fiss-command-version](https://github.com/fiss-scaffold/fiss-command-version)

### 添加依赖
+ 组件开发过程中可通过`fiss install`命令添加依赖，`fiss install`命令可参考[fiss-command-install](https://github.com/fiss-scaffold/fiss-command-install)

### 文档
+ 可以通过编辑`README.md`文件来简要说明组件的应用场景、使用方法和添加代码示例。

### 测试
+ `test`目录用于存放组件的测试用例

### 使用组件

## 目录结构说明
```
.
├── README.md
├── component.json
├── docs -> 组件文档目录
├── example -> 组件示例目录
├── index.js -> 组件入口文件
├── package.json
├── src -> 组件源码目录
└── test -> 单元测试目录
```

## 常用命令

### 版本相关命令

#### 版本更新：
+ `npm run major`: 更新major版本号并同步到远程仓库(比如`1.0.0`->`2.0.0`)
+ `npm run minor`: 更新minor版本号并同步到远程仓库(比如`1.0.0`->`1.1.0`)
+ `npm run patch`: 更新patch版本号并同步到远程仓库(比如`1.0.0`->`1.0.1`)

### 安装组件命令

+ `fiss install [component]`: 安装指定组件
+ 或者先在`component.json`中配置`dependencies`项后，执行`fiss install`
