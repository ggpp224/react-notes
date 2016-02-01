# 移动设备css适配

### meta

* viewport

​		1. width = device-width 设置视图宽度等于设备屏幕宽度

​		2. initial-scale = 1 设置初始缩放比例是1

​		3. minimum-scale = 1 设置最小缩放比例是1

​		4. maximum-scale = 1 设置最大缩放比例为1

​		5. user-scalable = no 不允许缩放



### 字体单位

* px 无继承
* em 相对于父元素继承
* rem 相对于root继承， 一般为html; css3属性

​             1rem的定义是根元素的字体大小，比如html的font-size : 12px,那么1rem=12px

* vh 1vh=视窗高度/100 ， css3属性

利用rem通过js来计算根元素的font-size，从而适应各种屏幕







##### *references:*

*http://www.tuicool.com/articles/nmm6reE*