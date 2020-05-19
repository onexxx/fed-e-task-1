## 笔记
### 快速上手
- 安装：`npm i typescript -D`
- 创建`.ts`文件
- 编译：`npx tsc xxx.ts`

### 编译整个项目
- 初始化：`npx tsc --init`
- 编译：`npx tsc`

### 类型
- string,number,boolean，在非严格模式下可以为null或undefined
- 如果要将es6的代码转成es5，需要配置lib属性指定标准库：`lib: ['ES2015', 'DOM']`，否则无法找到es6新增类型的定义
- 标准库就是内置对象所对应的声明
- 对象类型：object，字面量，或者接口类型
- 数组类型：`Array<number>` 或 `number[]`
- 元组类型：`tuple: [number, string] = [18, 'jarvis']`，通常用于函数返回多个值。比如Object.entries(data)返回一个元组数组
- 枚举类型：在很多其他语言中会有枚举类型，js中通常定义一个对象来模拟枚举类型。语法：enum Status { status1 = 1, status2 = 2 }。普通枚举对代码有侵入性，会生成一个可以双向访问的枚举对象。如果不需要通过索引访问枚举值，可以选用常量枚举：`const enum xxx{}`，编译后枚举的值会被替换成对应的常量。
- 函数类型：函数声明和函数表达式，`function add(a: string, b: number): string {}`，`let fun: (a: string, b: number) => string = function add(a: string, b: number): string {}`
- 任意类型：any，`let a: any = 100; a = 'lucy';`，是动态类型，也就是不检查类型，应该避免使用，一般用于兼容旧代码
- 隐式类型推断：如果没有指定类型，会根据声明时赋值的类型来推断，如果声明时没有赋值，则标记为any类型，可以接收任意类型。也是不建议使用
- 类型断言：在某些情况下，ts无法推断出一个变量的具体类型，而开发者可以明确类型就可以使用断言来辅助ts做出判断。有两种方式：`res as number`，`<number>res`，后一种使用了尖括号，在jsx中会和标签冲突，推荐使用第一种方式。类型断言并不是类型转换，类型转换是运行时的概念，而类型断言是编译时的概念，类型断言只在编译时存在。
- 接口：定义数据需要包含哪些成员。可选成员，只读成员，动态成员。接口只存在于编译阶段。

### 类
- ts增强了class的相关语法
- 基本用法（成员属性定义）
- 访问修饰符：私有成员，公有成员，受保护成员，只读属性
- 类与接口：类与类之间也有相似的行为，就可以抽象为接口。
- 抽象类：abstract关键字。不能直接实例化，只能继承并实现抽象类中的抽象方法。
- 泛型：不在定义的时候指定类型，在使用的时候才确定类型。

### 类型声明
- declare语句声明类型
- 主要是兼容一些普通的js模块
- 绝大多数常用的npm模块都提供了对应的声明，我们只要安装对应的声明模块就可以了（由于是编译时才用到，安装时加上-D）

## 练习
1. 使用ts编写一个简单demo，用到之前学到的知识

## 扩展阅读
1. [腾讯IMWEB团队《未来可期的TypeScript》](https://mp.weixin.qq.com/s?__biz=MzA4Nzg0MDM5Nw==&mid=2247485046&idx=1&sn=1046b23d254bcdba9803e6c76b83ffe8&chksm=90320594a7458c821cb08d7753054395b4e7b383809383f772426d5af0b99783ba874458d814&mpshare=1&scene=24&srcid=&sharer_sharetime=1588907131094&sharer_shareid=bf4520c14504ed470fa220a97f7103bb#rd)
