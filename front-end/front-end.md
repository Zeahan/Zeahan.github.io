# 前端面经整理
## 基础
## javascript
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
## HTML
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
