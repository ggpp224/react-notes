# React

#### react生命周期

* constructor
* render   *保持`render()` 纯粹，可以使服务器端渲染更加切实可行，也使组件更容易被理解。* 
* componentWillMount()  在初始化渲染之前调用，*客户端和服务端都调用*
* componentDidMount() 初始化渲染后调用，*服务端不会调用*



* componentWillReceiveProps() 在接收到新的props时调用，初始化渲染的时候不会调用
* shouldComponentUpdate() 在接收到新的props或者state时渲染之前调用，初始化渲染时不会调用，在使用forceUpdate时也不会调用。 返回false则render不会执行， componentWillUpdate和componentDidupdate也不会被调用， 默认是true.
* componentDidUpdate 真实dom更新后调用，初始化渲染的时候不会被调用，在该方法中可以操作dom
* componentWillUnmount 组件从dom中移除时调用



http://www.infoq.com/cn/articles/react-dom-diff?utm_source=infoq&utm_medium=related_content_link&utm_campaign=relatedContent_articles_clk