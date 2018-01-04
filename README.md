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

##### 第一个实例

```
<div id="example"></div>
<script type="text/babel">
  ReactDOM.render(
    <h1>Hello, world!</h1>,
    document.getElementById('example')
  );
</script>
```
