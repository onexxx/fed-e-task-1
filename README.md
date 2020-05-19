# 方建伟 ｜ Part 1 | 模块一

## 简答题

### 第一题
控制台打印10  
由于变量i是用var声明，所以会提升为全局变量，此时a数组的任意函数执行都是打印i最后的值，也就是10；如果想让函数打印出对应下标的数字，可以把var i 改为 let i

### 第二题
会报一个ReferenceError，提示tmp未定义  
在if中，用let声明了一个变量tmp，那么根据ES6规定，会绑定到这个块级区域，在声明之前就使用这些变量，就会报错。也即是为“暂时性死区”

### 第三题
```
arr.reduce((min, num) => Math.min(min, num), arr[0]);
```

### 第四题
#### 是否存在变量提升？
var声明的变量存在变量提升（将变量提升到当前作用域的顶部）。即变量可以在声明之前调用，值为undefined。

let和const不存在变量提升。即它们所声明的变量一定要在声明后使用，否则报ReferenceError错。

#### 是否存在暂时性死区？
let和const存在暂时性死区。即只要块级作用域内存在let命令，它所声明的变量就“绑定”（binding）这个区域，不再受外部的影响。

在代码块内，使用let命令声明变量之前，该变量都是不可用的。这在语法上，称为“暂时性死区”（temporal dead zone，简称 TDZ）。

var不存在暂时性死区。

#### 是否允许重复声明变量？
var允许重复声明变量。let和const在同一作用域不允许重复声明变量。

#### 是否存在块级作用域？
var不存在块级作用域。let和const存在块级作用域。

#### 是否能修改声明的变量？
var和let可以，const声明一个只读的常量。

### 第五题
会打印出20  
obj.fn()的方式调用时，fn中的this指向obj，而setTimeout中的回调是用箭头函数，箭头函数中的this与外层的this一致，所以也是指向obj，最终打印出20

### 第六题
Symbol表示一个独一无二的值，所以可以用它来设置私有属性，还有就是表示一些内置函数，比如Symbol.iterator

### 第七题
浅拷贝就是只拷贝值，实现的方法有Object.assign，展开运算符；

深拷贝为完全拷贝，对拷贝对象的任何改动，不会影响被拷贝的对象；  
深拷贝常见的方法有：  
1. JSON.parse(JSON.stringify(object))，缺点是会忽略 undefined，symbol和函数，不能解决循环引用的对象问题。
2. MessageChannel，可以处理 undefined 和循环引用对象，缺点是只能处理内置类型，不包含函数
3. lodash 的深拷贝函数
4. 自己实现（遇到对象和数组递归处理，用map解决循环引用问题）

### 第八题
JS是单线程执行的，在开发的过程中会遇到很多异步的场景，处理异步代码有回调，promise，generator，async/await，其中async/await应该是目前js异步编程的终极解决方案，解决了过去很多的问题和痛点。

Event Loop是事件循环，因为js是单线程的，所以执行的任务必须排队一个个执行，当一些异步任务执行完成后就会调用回调函数，此时会将回调任务推到任务队列中。

宏任务和微任务的区别在于执行时机不同，js执行总是从宏任务开始，当前宏任务执行完后会执行微任务直到微任务队列为空，当微任务也执行完后，一个事件循环结束。然后又从宏任务队列取出一个任务开始执行，开始下一轮事件循环。

### 第九题
```
Promise.resolve()
.then((data) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            console.log();
            resolve({ a: 'hello'});
        }, 10);
    })
}).then((data) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve({ ...data, b: 'lagou'});
        }, 10);
    })
}).then((data) => {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            var c = "I * U";
            console.log(data.a + data.b + c);
        }, 10);
    })
})
```

### 第十题
TypeScript是JavaScript的超集  
可以简单理解为：ts = es6+ + 类型系统 + js

### 第十一题
优点：  
- 清晰的函数参数/接口属性，增加了代码可读性和可维护性
- 静态检查
- 生成API文档
- 配合现代编辑器，各种提示
- 活跃的社区

缺点：
- 需要编写类型注解和类型声明代码
- 和某些库结合的不是很完美(比如vue 2.x)

总得来说优点远大于缺点，尤其是在编写大型项目，或是需要不断迭代的项目，可以大大提高项目的可维护性


## 项目文件说明

- notes : 笔记
- code : 代码
