# ReactJs 的继承和扩展

#### 导语：

> 在选择一个UI框架的时候，对组件的扩展性是一个必须要考虑的因素。例如我们自己编写了一个公共组件，组件中提供了通用功能，但是在某个场景下要添加一个独特功，这个时间就需要对我们的组件类扩展，常用的手段包括继承、重写、组合mixin手段，那么react对这些手段的支持情况如何呢？

## React.createClass

React.createClass(options) 生成一个组件类 ,如：

``` javascript
var Person = React.createClass({displayName: "Person",
  render: function() {
    this.outputs();
    return React.createElement("div", null, "Hello ", this.props.name);
  },

  outputs: function(){
      console.log('person.');
  }

});


var person = new Person();
person.outputs();   //output: person.
```

这是一个正常的创建组件类的方法，这时我们想重写outputs方法，在person实例化之前重写原型方法:

``` javascript
Person.prototype.outputs = function(){
   console.log('overwrite..')
}

var person = new Person();
person.outputs();
```

我们期待打印出: 'overwrite.. ', 但事与愿违，打印出的是'person.', 也就是说outputs并没有被重写。查看源代码我们发现createClass返回的是一个function（构造函数）,但在这个构造函数的方法体内我们看到react会把options内的方法都会绑到this上，作为this的属性，这样就永远不会执行到prototype上的outputs方法，因为执行的顺序是先找对象上的属性，找不到才执行原型上的方法。所以用React.createClass创建的类是无法用传统的方法来实现继承的。



## React.Component

``` javascript
class Footer extends React.Component {
}
```

这种方法实现的继承是没有问题的，而且Footer可以继续被继承



## 另一种框架Vue和React的createClass有一样的问题。

