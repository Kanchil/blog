## 对象继承

### 原型链继承

```javascript
function Parent () {
    this.name = 'kevin';
}

Parent.prototype.getName = function () {
    console.log(this.name);
}

function Child() {}

Child.prototype = new Person()

var child1 = new Child();

console.log(child1.getName()) // kevin
```

1.引用类型的属性被所有实例共享，举个例子：
2.在创建 Child 的实例时，不能向Parent传参


### 借用构造函数

```javascript
function Parent () {
    this.names = ['kevin', 'daisy'];
}

function Child () {
    Parent.call(this);
}

var child1 = new Child();

child1.names.push('yayu');

console.log(child1.names); // ["kevin", "daisy", "yayu"]

var child2 = new Child();

console.log(child2.names); // ["kevin", "daisy"]
```
优点：
1.避免了引用类型的属性被所有实例共享
2.可以在 Child 中向 Parent 传参
缺点：
方法都在构造函数中定义，每次创建实例都会创建一遍方法。
