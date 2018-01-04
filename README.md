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