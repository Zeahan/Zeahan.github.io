# 前端面经整理
[toc]


## 基础

[输入URL后](https://zhuanlan.zhihu.com/p/80551769)

#### HTTP常见请求头
**Accept 可接受的响应类型**
Accept-Charset 字符集
Accept-Encoding 编码
**Accept-Language 可接受的语言**
**Content-Language**
**Content-Type 发送内容的类型**
Authorization 认证信息 token
Origin 跨域请求的来源信息
响应头
Access-Control-Allow-Origin

#### cors
对于简单请求，浏览器直接发送带有origin的请求，对于复杂请求，先发送option请求
浏览器将响应头中的Access-Control-Allow-Origin与Origin对比，来决定是否允许请求



## javascript

#### Promise
**状态：**
1. 待定Pending 初始状态
2. 已兑现（fulfilled）: 意味着操作成功完成
3. 已拒绝（rejected）: 意味着操作失败

`Promise.reject(reason)` 返回一个拒绝状态，带有原因的Promise
`Promise.resolve(value)` 返回一个带着给定值解析过的Promise

##### Promise all any
两者都接受一个Promise的可迭代对象作为参数
all：返回一个Promise，结束状态包含所有迭代对象参数的数组，如果全部成功或参数为空数组，返回的Promise为成功，否则为待定（等全部Promise结束后状态变化为成功或失败）
any：任意一个成功，返回该成功的Promise，否则返回失败的Promise，带有所有错误原因的集合

##### 链式调用
`Promise.then(onFufilled, onRejected)`
第一个是Promise成功状态的回调函数，第二个参数是拒绝状态的回调函数
`then()` 返回的是一个Promise对象，**当前Promise p1回调函数的返回值对于其返回的Promise p2有以下几种情况：**
1. 返回了一个值x，则p2为接受状态，其回调函数的参数为x
2. 无返回值，则p2为接收状态，其回调函数的参数为undefined
3. 返回了一个接收状态的Promise p，则p2为接受状态，其回调函数的参数与p相同
4. 返回了一个拒绝状态的Promise p，则p2为拒绝状态，其回调函数
5. 返回了一个待定的Promise p，则p2同为待定状态，且终态与p相同
6. **如果没有回调函数，则简单地返回与p1终态相同的新Promise p2**

由于`.then()`会返回一个新的Promise，所以可以一直链式调用下去，对于后续函数依赖上一个函数的返回值作为参数时非常好用
`.catch(onRejected)` 等价于（内部call）`.then(undefined, onRejected)`
可以一直`.then()`而不处理拒绝的情况，最后用catch处理
`finally()`的回调函数无论接受与否均会调用

#### 数组操作
##### map
接受一个函数作为参数，该函数调用数组中每一个元素并返回一个值
返回一个包含所有返回值的数组
##### forEach
第一个参数为回调函数，对每个元素执行一次
回调函数的参数为 当前元素（必要），当前索引（可选），该数组（可选）
第二个参数是thisArg（用于回调函数的this值），可选

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
##### 懒加载
用一张小尺寸占位图代替真实的图片地址作为src，将真实的图片地址放在其他属性中，用scrollTop检测是否在视野内，进入视野时再将地址取出来放入src
##### 预加载
提前加载资源，可以放在js里加载，可以放在css里加载

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

#### 使用Link切换路由
React会使用diff算法比较切换前后的DOM树，仅对变化的部分进行更新

#### 非受控组件
表单中的input，自己维护一个state。

#### 组件使用索引作为key有什么坏处
组件的顺序改变（重新排序或者在组件前添加新组件）之后，key也会变化，导致列表重新渲染。同时，非受控的输入组件中的值，会与原有顺序冲突，造成混乱

#### Render props
**要解决的问题：组件状态和逻辑的复用**
要在A组件中渲染一个依赖它的state的B组件，可以直接把B组件写死在A组件的render函数中
但是如果想要让A组件可以渲染B、C、D、E等等组件中任意一个，这样的方法就不行了
**解决方案：**
将任意合法的组件X的函数作为一个props传入组件A中，然后在A的render中调用这个函数

#### 高阶组件
高阶组件接受一个组件的函数作为参数，然后在其render中使用render props
**不要在某个组件的render方法中使用高阶组件，这会使得该高阶组件在上一层组件的重新挂载中丢失并被重新创建** 在组件外使用HOC，可以保证HOC调用的一致性

#### Fragments
允许render方法返回一组多个独立的子组件，而不添加额外的DOM（正常情况下需要套在一个div这样的容器中返回）
