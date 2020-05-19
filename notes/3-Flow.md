## 笔记
### 类型
- 强类型与弱类型，类型安全维度的区分
- 静态类型与动态类型，类型检查维度的区分
- 类型安全和类型检查不能混为一谈，比如phython是强类型，动态类型的语言
- JavaScript是弱类型，动态类型，主要由于当时应用场景简单，所以采用弱类型，更易上手；由于是解释型语言，没有编译过程，所以设计成静态类型也没用
- 弱类型的缺点：无法做静态检查，如调用某个对象中不存在的方法，向函数中传入不正确的参数
- 强类型的优势：1.错误更早暴露 2.代码提示更智能，编码更准确 3.重构更牢靠 4.减少不必要的类型判断

### Flow
类型检测器，由Facebook公司于2014年推出，通过添加类型注解的方法来标记变量的类型

#### 快速上手
- 安装：`npm i flow-bin -D`
- 关闭vscode默认的js语法检查：搜索JavaScript validate，关闭
- 初始化flow配置文件：`npx flow init`
- 要检查的文件要加上`// @flow`注释标记，代码中添加类型注解
- 启动检查：`npx flow`
- 停止检查：`npx flow stop`

#### 移除类型注解
- 安装官方提供的移除工具：`npm i flow-remove-types -D`
- 执行：`flow-remove-types src -d dist`
- 使用babel配合插件移除：`npm i @babel/core @babel/cli @babel/preset-flow -D`
- 注意要添加.babelrc配置
- 执行：`babel src -d dist`

#### 开发工具插件
- flow language support
- 需要保存才会执行检查

#### 基本使用
- flow有类型推断，但是尽可能使用类型注解
- 数组类型限制：`let arr: Array<number>` 或 `let arr: number[]`，元组：`let arr: [number, string]`
- 对象类型限制：属性类型，是否可选，任意属性的类型
- 函数类型限制：`fun: (string, number) => void`
- 字面量限制：限制属性只能是某个值，结合联合类型用法，可以实现枚举类型效果
- 声明类型：`type StringOrNumber = string | number`
- maybe类型： `let a: ?number`，等价于 `let a: number | null | void`
- mixed 与 any，any是弱类型，mixed是强类型，any不会做类型检查，而mixed会检查。尽量不用any，除非是用于兼容旧代码
- 官方类型手册：https://flow.org/en/docs/types/
- 第三方类型手册（直观）：https://www.saltycrane.com/cheat-sheets/flow-type/latest/
- 运行环境api类型限制，如dom，bom，node。flow在工作时会自动下载这些api的定义到临时目录，我们就可以直接使用这些类型。可以在官方仓库中找到。

## 练习
1. 使用flow检查文件
2. 使用flow-remove-types移除文件中的类型注解
3. 使用babel移除文件中的类型注解
4. 编写一段代码，使用flow做类型检查，最好能用到上面学到的类型
