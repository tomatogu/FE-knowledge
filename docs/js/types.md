# JS类型判断

### **js原始类型**

    js原始类型：Number、String、Bollean、Object、Null、Undefined
    es6中新增：Symbol

### **问题1：如何判断一个变量x是数值类型**

首先想到的是使用 typeof 对 x 进行类型判断

```
typeof x === 'number' 如果为 true 则表明 x 是数值
```
对于99.99%的情况来说这样的判断没问题，但是，js中有一个特殊的全局对象属性 NaN ，惊讶的发现

```
typeof NaN === 'number'  返回的是true
```
所以，在判断的时候，需要将这一情况排除，使用isNaN方法来进行判断，如下：

```
isNaN(x) === NaN  返回 false 表示是数值
```
最终表达式为：

```
typeof x === 'number' && !(isNaN(x) === NaN)
```
返回结果为 true 则表示 x 为数值类型

___

判断 x 是string、boolean、undefined   直接
```
typeof x === 'string' | 'boolean' | 'undefined'
```
判断 x 是 null 时需注意

```
typeof null // 返回 'object'
```
可以使用

```
x === null
```