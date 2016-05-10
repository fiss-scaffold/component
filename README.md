# 组件说明文档

## 组件开发规范

### 环境依赖
+ [nodejs](https://nodejs.org/en/)：版本>=4
+ [fiss](https://github.com/zhangyihua/fiss)全局安装**最新版本**

### 新建组件
1. 首先请在[Gitlab](http://gitlab.58corp.com/)上新建项目
  + 以组件名称作为项目名称
  + 确保项目初始不含任何文件（除`.git`、`.gitignore`）
2. 将项目通过`git clone`命令下载到本地
3. 然后通过组件模板初始化一个组件的目录
```bash
fiss init component
```

### 配置`component.json`
`component.json`配置文件可能存在于**项目**或者**组件**中，**在不同的应用场景，并非所有的配置项都有用**，请酌情进行配置！

+ `name`: 名称，请和gitlab项目名称仓库保持一致
+ `description`: 描述，请用简洁的语言描述项目或者组件
+ `dependencies`: 依赖的组件
+ `dir`: 组件安装的目录，**仅适用于项目**
+ `version`: 版本号，**仅适用于组件**
+ `main`: 入口文件，**仅适用于组件**
+ `exclude`: 排除的文件和目录，**仅适用于组件**，具体可以参考[fiss-command-install](https://github.com/fiss-scaffold/fiss-command-install#目录排除)

由于默认的`protocol`和`gitlab`配置项已经集成到[fiss-command-install](https://github.com/fiss-scaffold/fiss-command-install)中，所以**无需配置`protocol`和`gitlab`**。

综上所述：
+ **项目**应该配置的项有`name`、`description`、`dir`、`dependencies`
+ **组件**应该配置的项有`name`、`version`、`exclude`、`dependencies`

### 版本号
组件的版本号，如非必要情况请不要手动修改，而是通过`fiss version <releaseType>`或者`npm scripts`命令更新。查看版本号或者更新版本号请参考[fiss-command-version](https://github.com/fiss-scaffold/fiss-command-version)

+ 组件初始化时，是没有发布版本的，`component.json`会有一个默认的版本号`0.0.0`，此时无法被项目使用。
+ 组件更新版本后才能被项目所使用，组件第一次版本更新后，会获得一个默认的版本号`1.0.0`。
+ 更新时必须输入本次版本更新的简要说明，比如`修复了浮层被底部菜单遮挡的bug`
+ 版本号的规范请参考[semver](https://github.com/npm/node-semver)

此外，对于更新版本号的一些建议：
+ **请不要频繁升级版本号！**
+ 除非重要变化（后台接口变动、UI整体升级、代码重构），请不要升级`major`版本号
+ 如果有重要更新或者bug修复，请周知所有使用组件的人

### 添加依赖
组件开发过程中可通过`fiss install`命令添加依赖，`fiss install`命令可参考[fiss-command-install](https://github.com/fiss-scaffold/fiss-command-install)。
+ 如果不指定版本号进行组件安装，将安装组件的最新版本，所以**请事先确认要安装的版本号**！
+ 通过`component.json`配置`dependencies`项安装时请指定版本号
+ 通过`fiss install <component>`命令安装组件时请附带版本号

### 组件开发


### 文档
+ 可以通过编辑`README.md`文件来简要说明组件的应用场景、使用方法和添加代码示例。

### 测试
+ `test`目录用于存放组件的单元测试用例

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
