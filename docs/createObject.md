## 创建对象的几种方式

### 工厂模式

```javascript
function createPerson(name) {
  var o = new Object()
  o.name = name
  o.getName = function() {
    return this.name
  }
}

var person = createPerson('kanchil')
```

缺点：对象无法识别，因为所有的实例都指向一个原型

### 构造函数模式

```javascript
function Person(name) {
  this.name = name
  this.getName = function() {
    return this.name
  }
}
var person2 = new Person('kanchil')
```

优点：实例可以识别为一个特定的类型

缺点：每次创建实例时，每个方法都要被创建一次

### 构造函数模式优化

```javascript
function Person(name) {
  this.name = name
  this.getName = getName
}

function getName() {
  return this.name
}

var person = new Person('kanchil')
```

### 原型模式

```javascript
function Person() {}

Person.prototype.name = 'kanchil'
Person.prototype.getName = function() {
  return this.name
}

var person = new Person()
```

优点：方法不会重新创建

缺点：1. 所有的属性和方法都共享 2. 不能初始化参数

### 原型模式优化

```javascript
function Person () {}

Person.prototype = {
  constructor: Person,
  name: 'kanchil',
  getName: function() {
    return this.name
  }
}

var person = new Person()
```

优点：实例可以通过constructor属性找到所属构造函数
缺点：1. 所有的属性和方法都共享 2. 不能初始化参数

### 组合模式

> 构造函数模式与原型模式双剑合璧。

```javascript
function Person(name) {
  this.name = name
}
Person.prototype = {
  constructor: Person,
  getName: function() {
    return this.name
  }
}
```
