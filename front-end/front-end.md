# 前端面经整理


## 基础


## javascript

#### call apply bind
1. 三者第一个参数都是目标函数，都会改变this的指向
2. call和apply立即执行，获得返回值
3. bind只绑定，不执行，返回值是一个改变this指向的函数
4. call需要接受原函数的每一个参数
5. apply接受数组作为参数
6. apply的应用：`Math.max(num1, num2, num3, ...)`需要输入多个参数来对比，但是数组的大小是不确定的，可以用apply传入。总结：用于传入不定量的参数

#### 浏览器本地存储
##### cookie
解决http无状态的问题
在所有同源的请求中自动携带，有过期时间，4kb左右，键值对
记住密码，购物车，记录浏览数据进行推荐
##### local Storage
比cookie大（5MB），本地存储，同源页面访问，存储图片
##### session storage
会话级别的，同窗口读取，本地存取
对表单信息进行维护（刷新页面不丢失）
##### IndexDB
#### 闭包
##### 优缺点
可以访问局部变量，同时避免全局变量污染
对对象进行封装
占用内存比较多，函数内部的循环依赖会造成内存泄漏
1. 全局变量和局部变量
   1. 全局变量 各处可以访问
   2. 局部变量 只有函数内部可以访问
2. 链式作用域
   子对象会一层一层向上从父对象中查找目标变量，反之则不行
3. 闭包的目的
   从函数外部访问内部变量
4. 闭包的实现方式
   函数`f1`内部有个子函数`f2`可以访问变量，`f1`将`f2`作为返回值并赋值给外部的变量，`f2`会一直存在，直到没有访问后，被垃圾回收机制回收

#### js事件处理
##### 拖动事件
**被拖动的元素：**
`ondragstart`开始拖动`ondrag`正在被拖动`ondragend`完成拖放
`ondragenter` `ondragover` `ondragleave` `ondrop`

[事件汇总](https://www.w3school.com.cn/jsref/jsref_events.asp)
捕获：window-document-html-body-祖先DOM-target
冒泡：target-祖先DOM-body-html-document-window
`addEventListener()`第一个参数为类型，第二个为触发的动作，第三个boolean，true表示捕获阶段处理，false为冒泡阶段处理
`onblur` 失去焦点，`focus`获得焦点，`load`, `onload`,`onmouseenter` `onmouseleave`鼠标进入/离开元素，这些时间无法冒泡

##### 事件委托
将一个元素的事件处理委托给另一个元素（父元素）
目的：为多个元素绑定相同的事件（绑定一次事件即可应用到多个元素上，例如列表中的每一项）
实现方式：利用事件的冒泡机制，将事件绑定在目标元素的父元素上，在冒泡阶段触发，父元素触发事件时，利用`event.target`查找到原本的元素。

#### js数据类型
基本数据类型`number`,`string`,`boolean`,`undefined`
基本包装类型`Number`, `String`, `Boolean`使得基本数据类型有了属性和方法，使用时转换为包装类型，使用后转回基本数据类型

`NaN` - `Number`
`null` - `Object` 空对象
`undefined` - `undefined` 声明未赋值，未声明，函数无返回值（return undefined），函数未传参

#### js对象
创建方式
1. 使用字面量，花括号，里面是键值对
2. 使用构造函数（new）
3. 使用工厂模式（`createXXX()`）内部会return一个`new Object()`
1/3只能返回Object类型的对象

instanceof 构造函数，判断对象属不属于该类型

#### 深拷贝与浅拷贝
**浅拷贝** 只拷贝最浅一层的属性，如果属性是对象或数组，仅仅复制该子对象的属性的内存地址
实现方式有for in 遍历属性和 `Object.assign()`
**深拷贝** 
对于对象的每一层均拷贝一份
实现方式是使用`for in` 进行递归（遇到对象或数组则进入下一层递归）

#### 原型链和原型对象
原型对象 构造函数.prototype 对象._proto
可以对原型对象添加方法，避免重复创建函数
当调用一个对象的方法时，先找自身属性，然后找原型对象，然后找原型的原型，最后找到object，如果没有则返回null

#### 函数内 this 的指向【非常重要】

我们在《JavaScript 基础/函数.md》这篇文章讲过，函数的调用有**六种**形式。

根据函数的调用方式的不同，this 会指向不同的对象：

- 1.以函数的形式（包括普通函数、定时器函数、立即执行函数）调用时，this 的指向永远都是 window。比如`fun();`相当于`window.fun();`

- 2.以方法的形式调用时，this 指向调用方法的那个对象

- 3.以构造函数的形式调用时，this 指向实例对象

- 4.以事件绑定函数的形式调用时，this 指向**绑定事件的对象**

- 5.使用 call 和 apply 调用时，this 指向指定的那个对象

#### ES6新特性
**箭头函数**
**class**
**let, const**
**Promise** resolve reject promise.then
**fetch** 基于promise，替代ajax

#### 同源和跨域
XMLHttpRequest
同源：域名，协议，端口相同
解决跨域问题
1. jsonp 利用html标签的src属性允许跨域的特性，添加script标签
2. cors 
浏览器发送请求时，添加origin字段
后端通过Access-Control-Allow-Origin检查是否允许访问

#### ajax axios fetch

#### 懒加载和预加载

#### js变量提升
使用var声明的变量会被提升到最顶部, 在声明前可以访问到

## HTML

#### HTML5新增特性

1. 语义化标签
2. 音视频标签
3. canvas绘图
4. 拖放API
语义化标签
`header` `footer` `aside` `article` `section` `nav` `dialog`  `details` `summary`

#### meta
```html
<meta charset=’utf-8′>
声明文档使用的字符编码
<meta http-equiv=”X-UA-Compatible” content=”IE=edge,chrome=1″/>
优先使用 IE 最新版
本和 Chrome
<meta name=”description” content=” 不超过 150 个字符 ”/>
页面描述
<meta name=”keywords” content=””/>
页面关键词者
<meta name=”author” content=”name, email@gmail.com”/>
网页作
<meta name=”robots” content=”index,follow”/>
搜索引擎抓取
<meta name=”viewport” content=”initial-scale=1, maximum-scale=3, minimum-scale=1,
user-scalable=no”> 为移动设备添加 viewport
<meta name=”apple-mobile-web-app-title” content=” 标题 ”> iOS 设备 begin
```

## CSS
#### 布局
##### 响应式与自适应
自适应：根据多个场景开发多个页面
响应式：一套页面应对多个场景
方式
1. CSS媒体查询 
   `@media`以窗口分辨率作为分割点
   `min-width` 移动端优先（为pc端单独设置样式）
   `max-width` pc优先（为移动端单独设置样式）
2. 百分比布局 bootstrap
3. rem布局
   em 节点基于上一级节点的size
   rem 基于根节点的size，解决em多层继承带来的尺寸不可控的问题
4. 视口单位viewport
   1. vw 相对于视窗的宽度
   2. vh相对于视窗的高度
5. 图片响应式 max-width
##### 块级元素和行内元素
块级元素独占一行，可以设置宽高
行内元素不会独占一行，不能设置宽高
inline-block 对外是行内元素（不会独占一行），对内是块级元素（可以单独设置宽高）
##### position
static 默认属性值，跟随文档流
relative: 相对于自身原本的位置偏移，依然保持原来占据的空间，不脱离文档流
absolute: 相对于最近的祖先元素中的relative/absolute进行偏移，脱离文档流
fixed: 相对于可视区域固定，脱离文档流
sticky: 粘性定位，在到viewport的距离未触发阈值`top: 0px`时，为`relative`，反之则为`fixed`

##### 布局
表格布局
浮动布局：为了兼容，实现图文混排
不会影响兄弟元素的位置，但会影响其内部文字排列
会脱离文档流，造成父级元素高度塌陷
inline-block布局 像文本一样去排列block元素
响应式布局：
#### 如何实现水平居中
对于行内元素`inline, inline-block,.inline-table/flex`，在块级父容器中使用`text-align: center;`
对于块级元素，设置`margin-left`,`margin-right` 为auto，前提是已经设置了`width`不然块级元素会被拉伸为父容器的宽度
多个块级元素：使用flexbox
#### 如何实现垂直居中
对于单行的行内元素或文本元素，为它们添加相等的上下padding，或者使`line-height`与`height`相等
多行同样可以设置padding

对于块级元素，如果已知元素的高度，可以将其定位到父级元素的中间高度`top: 50%`然后设置`margin-top`为高度的一半。未知高度则使用`transform: rotateY(-50%)`

使用flexbox
`justify-content: center` 与flex-direction水平方向居中
`align-items`: 与flex-direction垂直方向居中


## 框架
### React
