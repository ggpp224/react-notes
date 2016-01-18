服务端预渲染是页面先在服务端生成: 服务端需要内嵌一个能生成页面的环境，由于react是虚拟dom，所以只需要一个能运行javascript的环境，如v8. 在服务端先拿到数据和用react编写成的组件树， 通过React.renderToString方法生成html字符串，注入到静态页面中返回前端， 这时前端能看到的就是一个包含数据的整个页面。 
前端js生成的组件数应该和服务端生成的一致，这样能保证前端js加载后页面无需重新渲染，当然初始化数据也要保证一致，要不然因为数据变化了界面也是要变化的。

有了react的组件只是某一状态下的视图，按照这一思想，我们编写的react组件也应该是前后端可以共用的同一套代码。

可运行demo:
https://github.com/DavidWells/isomorphic-react-example  