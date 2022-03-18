# 函数

### 创建函数对象

使用构造函数创建函数对象（实际开发中通常不使用），像下面这样：

```javascript
var fn = new Function();
```

通常在实际开发中我们会使用函数声明创建函数对象，像下面这样：

```javascript
function (arg0, [agr1]){
    statements
}
```

还可以用函数表达式创建函数对象，即创建一个匿名函数并把它赋值给一个变量，这里我们需要引入匿名函数的概念。

**匿名函数**就是指没有函数名称的函数对象，匿名函数就是下方表达式的右半边，右半边是将它赋值的变量，这就是用函数表达式创建的一个函数对象

```javascript
var fn = function(agr0, [agr1]){){
    statements
}
```

除此之外，还有一种立即执行的函数，通常只执行一次，立即执行函数像下面这样：

```javascript
(function(agr0, [agr1]){){
    statements
})(agr0, [agr1]){);
```

#### 函数的声明提前

* 使用函数声明形式<mark style="color:red;">`function fun(){}`</mark>声明的函数在所有代码执行前整个都被创建，可以在函数代码那一行之前调用；
* 使用<mark style="color:red;">`var`</mark>声明的函数只会被声明，不会被创建赋值（打印出来的值是<mark style="color:red;">`undefined`</mark>），不能在声明前调用

### 函数对象的参数

在函数对象声明时设置的参数叫做形参，相当于用<mark style="color:red;">`var`</mark>声明的函数变量。这里需要注意的是，解析器不会检查形参的格式和数量，因此需要在函数内部做好校验工作。

当形参不够时，缺少的形参默认赋值为<mark style="color:red;">`undefined`</mark>；当形参过多时，多余形参不参与函数操作。

### 函数的调用与执行

```javascript
// 调用函数对象不执行，次方式可以打印出函数的主体
fn;

// 执行函数，此方法可以打印出函数的返回值
fn();
```

### 函数的返回值

函数对象通过<mark style="color:red;">`return`</mark>返回学习，也通过它结束函数，因此<mark style="color:red;">`return`</mark>语句后的函数不会被执行。

<mark style="color:red;">`return`</mark>语句后不跟返回值会返回<mark style="color:red;">`undefined`</mark>，不写<mark style="color:red;">`return`</mark>语句也返回<mark style="color:red;">`undefined`</mark>。

```javascript
function (arg0, [agr1]){
    ...
    return;
}
```

这里区分一下<mark style="color:red;">`break`</mark>，<mark style="color:red;">`continue`</mark>和<mark style="color:red;">`return`</mark>：

* <mark style="color:red;">`break`</mark>：退出整个循环；
* <mark style="color:red;">`continue`</mark>：跳过当次循环直接继续下一个循环；
* <mark style="color:red;">`return`</mark>：终止函数执行。

### 作用域

#### 全局作用域

* 全局作用域在页面打开时创建，关闭时销毁；
* 全局作用域含有一个全局对象<mark style="color:blue;">`window`</mark>，由浏览器创建可以直接使用；
* 我们创建的全局变量都会变成<mark style="color:blue;">`window`</mark>对象的属性，函数都会变成<mark style="color:blue;">`window`</mark>对象的方法；
* <mark style="color:red;">`var`</mark>声明的对象会在所以代码执行前被声明（但不会被赋值）

#### 函数作用域

* 每调用一次函数都会创建一个新的函数作用域，他们之间是独立的，函数执行完毕后作用域销毁；
* 函数中可以访问全局变量，函数操作一个变量先从自身作用域开始找，找不到去上级作用域找；
* 函数中用<mark style="color:red;">`var`</mark>声明的变量会在函数代码执行前被声明，且形参就相当于用<mark style="color:red;">`var`</mark>声明的变量；&#x20;
* 函数中不用<mark style="color:red;">`var`</mark>声明的变量会变成全局变量。

### 递归函数

{% hint style="warning" %}
递归是在函数内部调用自身, 通常结合return加入结束条件, 否则会无限循环.
{% endhint %}

```javascript
//永远点不完的弹窗

function fn(){
    alert('弹窗');
    fn();
}
fn();
```

```javascript
//弹窗三次

var i=0;
function fn(){
    i++;
    alert('弹窗');
    if(i>=3){
        return;
    }
    fn();
}
fn();
```

```javascript
//计算1~n的和

function getSum(n){
    if(n==1){
        return n;
    }
    return n+getSum(n-1);
}
document.write(getSum(5));
```

### foreach

```javascript
arr.forEach(item => {
    if(item instanceof Array) {
        arrMap(item);
    }else{
        newArr.push(item);
    }
});
```
