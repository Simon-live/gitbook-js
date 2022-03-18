---
description: 对象属于引用数据类型，与基本数据类型进行区分。
---

# 对象

## 创建对象

**用关键字创建对象**

```javascript
var obj = new Object();

// 为对象添加属性
obj.id = 1;
obj.name = "Simon";
```

**用字面量创建对象**

```javascript
var obj = {};

// 用字面量创建对象的时候可以同时指定属性
var obj = {
    id: 1,
    name: "Simon"
};
```

{% hint style="info" %}
通常我们指定属性的时候不需要给属性名加引号，但如果需要设置特殊字符构成的属性名，则需要用引号包裹，避免引发歧义。
{% endhint %}

## 对象的属性操作

**读取属性**

{% hint style="info" %}
如果读取的属性不存在对象中，不会报错会返回undefined。
{% endhint %}

```javascript
console.log(obj.id);
```

**修改属性**

```javascript
obj.name = "Alex";

// 还有一种更灵活的方法
obj["name"] = "Alex";

// 在这种方法中可以直接传入变量
var a = "name";
obj[a] = "Alex";
```

**删除属性**

```javascript
delete obj.name;
```

**判断属性存在**

```
“属性名" in 对象;

// return: true|false
```

#### 遍历属性

```javascript
// for...in 循环遍历对象的属性
// 这个变量a是属性名，对象[a]就是对应的属性值，不能用对象.n会返回undefined
for(var a in obj){
	console.log(a);
}
```

### 关于引用数据类型和基本数据类型

基本数据类型保存在栈内存中，引用数据类型保存在堆内存中由地址指针索引。

作比较时，基本数据类型比较他的值，引用数据类型比较内存地址。所以哪怕一个对象内容是一样的，但是内存地址不同，他们也是不相等的。
