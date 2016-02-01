# Redux

> Redux 是一个javascript的状态管理容器, 试图让state变化变得可预测
> 
> * 应用中所有的state都以一个对象树的形式存在一个单一的store中
>   
> * 惟一改变state的方法就是触发action
>   
>   ​



### Action

* 尽量减少在action中传递的数据
* Action创建函数是生成action的方法， 可以认为是生成一批同类型action的方法，**纯函数** ,返回action对象

### Reducer

* 为了描述action如何改变state树,你需要编写reducers


* reducer形式为(state, action) => state的纯函数，描述了action如何把一个state转变成下一个state。
* 当state发生变化时需要返回全新的对象，而不是修改传入的参数
* 保持reducer纯净，不要执行有副作用的操作，如api请求和路由跳转



### 数据流

严格的单向数据流是redux的核心设计

redux应用中数据的生命周期遵循下面4个步骤：

1. 调用 store.dispatch(action)
2. store调用传入的reducer函数
3. 改变state树数据
4. 从根容器开始往子孙组件执行render方法









