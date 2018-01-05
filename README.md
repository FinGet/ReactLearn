# ReactLearn
learn basic react 

>`React`一个用于创建可复用，可聚合web组件的js库。 只提供了前端`MVC`框架中的“V”。并不是一个完整的前端`MVC`框架

### React 特点
- 1.`声明式设计` −React采用声明范式，可以轻松描述应用。
- 2.`高效` −React通过对DOM的模拟，最大限度地减少与DOM的交互。
- 3.`灵活` −React可以与已知的库或框架很好地配合。
- 4.`JSX` − JSX 是 JavaScript 语法的扩展。React 开发不一定使用 JSX ，但我们建议使用它。
- 5.`组件` − 通过 React 构建组件，使得代码更加容易得到复用，能够很好的应用在大项目的开发中。
- 6.`单向响应的数据流` − React 实现了单向响应的数据流，从而减少了重复代码，这也是它为什么比传统数据绑定更简单。

#####  JSX有以下优点：
- JSX 执行更快，因为它在编译为 JavaScript 代码后进行了优化。
- 它是类型安全的，在编译过程中就能发现错误。
- 使用 JSX 编写模板更加简单快速。

>注意:由于 JSX 就是 JavaScript，一些标识符像 `class` 和 `for` 不建议作为 XML 属性名。作为替代，React DOM 使用 `classNam`e 和 `htmlFor` 来做对应的属性。

![](https://i.imgur.com/b3Sru2N.png)
##### 第一个实例

```
<div id="example"></div>
<script type="text/babel">
  React.render(
    <h1>Hello, world!</h1>,
    document.getElementById('example')
  );
</script>
```

## React的渲染方式
![react渲染方式](https://i.imgur.com/f48ariI.png)
![将不再有啥](https://i.imgur.com/UqBVbfZ.png)
![好处](https://i.imgur.com/xpHpreo.png)

>一个React组件可以理解成一个独立的函数。
>*接受参数（props）*，*可复用*，*可以传递*，*返回结果（渲染组件）*

## 虚拟DOM树
>JavaScript虽快，但是做一些DOM操作却相当慢。

##### react处理方式(在每一次更新时...)
- React重建DOM树
- 找到与上个版本的DOM的差异
- 计算出最新的DOM更新操作
- 从操作队列中批量地执行DOM更新操作

##### react可以在Node.js中运行（服务器端）
- 服务器与客服端共用逻辑（Isomorphic javascript）
- SEO友好，便于生成缓存的单页应用
- 直接渲染特定的页面而不用渲染整个app

## React state(状态)
React 把组件看成是一个状态机（State Machines）。通过与用户的交互，实现不同状态，然后渲染 UI，让用户界面和数据保持一致。
React 里，只需更新组件的 state，然后根据新的 state 重新渲染用户界面（不要操作 DOM）。
以下实例中创建了 LikeButton 组件，getInitialState 方法用于定义初始状态，也就是一个对象，这个对象可以通过 this.state 属性读取。当用户点击组件，导致状态变化，this.setState 方法就修改状态值，每次修改以后，自动调用 this.render 方法，再次渲染组件。

```
({liked: !this.state.liked});
  },
  render: function() {
    var text = this.state.liked ? '喜欢' : '不喜欢';
    return (
      <p onClick={this.handleClick}>
        你<b>{text}</b>我。点我切换状态。
      </p>
    );
  }
});
 
React.render(
  <LikeButton />,
  document.getElementById('example')
);
```
### 正确地使用状态

###### 不要直接更新状态

```
// Wrong
this.state.comment = 'Hello';
```
应当使用 setState():

```
// Correct
this.setState({comment: 'Hello'});
```
>构造函数是唯一能够初始化 this.state 的地方。

## props
>state 和 props 主要的区别在于 props 是不可变的，而 state 可以根据与用户交互来改变。这就是为什么有些容器组件需要定义 state 来更新和修改数据。 而子组件只能通过 props 来传递数据。

#### 使用 Props
```
var HelloMessage = React.createClass({
  render: function() {
    return (<h1>Hello {this.props.name}</h1>)
  }
});
 
React.render(
  <HelloMessage name="Runoob" />,
  document.getElementById('example')
)
```
#### 默认 Props
>你可以通过 `getDefaultProps()` 方法为 props 设置默认值，实例如下：

```
var HelloMessage = React.createClass({
  getDefaultProps: function() {
    return {
      name: 'Runoob'
    };
  },
  render: function() {
    return (<h1>Hello {this.props.name}</h1>)
  }
});
 
React.render(
  <HelloMessage />,
  document.getElementById('example')
);
```

#### Props 验证
>Props 验证使用 propTypes，它可以保证我们的应用组件被正确使用，React.PropTypes 提供很多验证器 (validator) 来验证传入数据是否有效。当向 props 传入无效数据时，JavaScript 控制台会抛出警告。

```
var title = "hello react";
// var title = 123;
var MyTitle = React.createClass({
  propTypes: {
    title: React.PropTypes.string.isRequired,
  },
 
  render: function() {
     return (<h1> {this.props.title} </h1>)
   }
});
React.render(
    <MyTitle title={title} />,
    document.getElementById('example')
);
```

更多验证器
```
React.createClass({
  propTypes: {
    // 可以声明 prop 为指定的 JS 基本数据类型，默认情况，这些数据是可选的
   optionalArray: React.PropTypes.array,
    optionalBool: React.PropTypes.bool,
    optionalFunc: React.PropTypes.func,
    optionalNumber: React.PropTypes.number,
    optionalObject: React.PropTypes.object,
    optionalString: React.PropTypes.string,
 
    // 可以被渲染的对象 numbers, strings, elements 或 array
    optionalNode: React.PropTypes.node,
 
    //  React 元素
    optionalElement: React.PropTypes.element,
 
    // 用 JS 的 instanceof 操作符声明 prop 为类的实例。
    optionalMessage: React.PropTypes.instanceOf(Message),
 
    // 用 enum 来限制 prop 只接受指定的值。
    optionalEnum: React.PropTypes.oneOf(['News', 'Photos']),
 
    // 可以是多个对象类型中的一个
    optionalUnion: React.PropTypes.oneOfType([
      React.PropTypes.string,
      React.PropTypes.number,
      React.PropTypes.instanceOf(Message)
    ]),
 
    // 指定类型组成的数组
    optionalArrayOf: React.PropTypes.arrayOf(React.PropTypes.number),
 
    // 指定类型的属性构成的对象
    optionalObjectOf: React.PropTypes.objectOf(React.PropTypes.number),
 
    // 特定 shape 参数的对象
    optionalObjectWithShape: React.PropTypes.shape({
      color: React.PropTypes.string,
      fontSize: React.PropTypes.number
    }),
 
    // 任意类型加上 `isRequired` 来使 prop 不可空。
    requiredFunc: React.PropTypes.func.isRequired,
 
    // 不可空的任意类型
    requiredAny: React.PropTypes.any.isRequired,
 
    // 自定义验证器。如果验证失败需要返回一个 Error 对象。不要直接使用 `console.warn` 或抛异常，因为这样 `oneOfType` 会失效。
    customProp: function(props, propName, componentName) {
      if (!/matchme/.test(props[propName])) {
        return new Error('Validation failed!');
      }
    }
  },
  /* ... */
});
```

## React 事件
React 元素的事件处理和 DOM元素的很相似。但是有一点语法上的不同:
- React事件绑定属性的命名采用驼峰式写法，而不是小写。
- 如果采用 JSX 的语法你需要传入一个函数作为事件处理函数，而不是一个字符串(DOM元素的写法)

例如，传统的 HTML：
```
<button onclick="activateLasers()">
  Activate Lasers
</button>
```
React 中稍稍有点不同：
```
<button onClick={activateLasers}>
  Activate Lasers
</button>
```
在 React 中另一个不同是你不能使用返回 false 的方式阻止默认行为。你必须明确的使用 preventDefault。例如，传统的 HTML 中阻止链接默认打开一个新页面，你可以这样写：
```
<a href="#" onclick="console.log('The link was clicked.'); return false">
  Click me
</a>
```
在 React，应该这样来写：
```
function ActionLink() {
  function handleClick(e) {
    e.preventDefault();
    console.log('The link was clicked.');
  }

  return (
    <a href="#" onClick={handleClick}>
      Click me
    </a>
  );
}
```

在实例中我们设置了输入框 input 值value = {this.state.data}。在输入框值发生变化时我们可以更新 state。我们可以使用 onChange 事件来监听 input 的变化，并修改 state。
```
var HelloMessage = React.createClass({
  getInitialState: function() {
    return {value: 'Hello Runoob!'};
  },
  handleChange: function(event) {
    this.setState({value: event.target.value});
  },
  render: function() {
    var value = this.state.value;
    return (<div>
		// 绑定了value如果不监听onChange事件，则输入框的值不能被改变
		// 如果绑定defaultValue = {value} 不绑定onChange事件，只能改变输入框的值，
		// state并不会改变
	    <input type="text" value={value} onChange={this.handleChange} /> 
	    <h4>{value}</h4>
	   </div>)
  }
});
ReactDOM.render(
  <HelloMessage />,
  document.getElementById('example')
);
```
## React 组件生命周期 [官方链接](https://doc.react-china.org/docs/react-component.html)

组件的生命周期可分成三个状态：
- Mounting：已插入真实 DOM
- Updating：正在被重新渲染
- Unmounting：已移出真实 DOM

生命周期的方法有：
- `componentWillMount` 在渲染前调用,在客户端也在服务端。
- `componentDidMount` : 在第一次渲染后调用，只在客户端。之后组件已经生成了对应的DOM结构，可以通过`this.getDOMNode()`来进行访问。 如果你想和其他JavaScript框架一起使用，可以在这个方法中调用setTimeout, setInterval或者发送AJAX请求等操作(防止异部操作阻塞UI)。
- `componentWillReceiveProps` 在组件接收到一个新的prop时被调用。这个方法在初始化render时不会被调用。
- `shouldComponentUpdate` 返回一个布尔值。在组件接收到新的props或者state时被调用。在初始化时或者使用forceUpdate时不被调用。 
可以在你确认不需要更新组件时使用。
- `componentWillUpdate` 在组件接收到新的props或者state但还没有render时被调用。在初始化时不会被调用。
- `componentDidUpdate` 在组件完成更新后立即调用。在初始化时不会被调用。
- `componentWillUnmount` 在组件从 DOM 中移除的时候立刻被调用。

###### 装配
这些方法会在组件实例被创建和插入DOM中时被调用：
- constructor()
- componentWillMount()
- render()
- componentDidMount()

###### 更新
属性或状态的改变会触发一次更新。当一个组件在被重渲时，这些方法将会被调用：
- componentWillReceiveProps()
- shouldComponentUpdate()
- componentWillUpdate()
- render()
- componentDidUpdate()

###### 卸载
当一个组件被从DOM中移除时，该方法被调用：
- componentWillUnmount()

###### 其他API
每一个组件还提供了其他的API：
- setState()
- forceUpdate()

###### 类属性
- defaultProps
- displayName

###### 实例属性
- props
- state