# Knockout_demo
Knockout.js学习
三个核心功能：
1、属性监控与依赖跟踪
2、声明式绑定
3、模板机制
MVVM（Model-View-View Model）
Model: 存储应用程序的数据，通常通过Ajax向服务器读写
View Model: 描述数据内容和页面操作的数据模型
View: 代表View Model状态的一个可见、互动的UI界面，在View Model发生变化时自动更新
使用KO创建一个View Model  只需声明一个JS对象，在HTML中通过data-bind绑定

ko.applyBindings(）激活KO
ko.applyBindings(用于声明式绑定的View Model对象，使用data-bind属性的HTML元素或容器（可选）)     用于在一个页面中声明了多个View Model来绑定不同的界面区域

ko.observable() 监控属性  当View Model发生变化时自动更新UI界面
reading observables ：  myViewModel.personName();
writing observables： myViewModel.personName('Jack');
     链式写法：myViewModel.personName('Jack').personAge(50)

ko.observableArray() 监控属性数组
var myObservableArray = ko.observableArray();
myObservableArray().push('new value')  //  在末尾增加新项
myObservableArray().pop()   //  删除最后一项并返回该项
myObservableArray().unshift('new value')  //  在头部增加新项
myObservableArray().shift()   //  删除头部第一项并返回该项
myObservableArray().reverse()    //  反转数组的顺序
myObservableArray().sort()   //   数组排序
myObservableArray.splice()   //   删除指定索引和指定数目的数组元素
myObservableArray.remove(someItem)   //   移除数组内匹配someItem的元素并返回这些对象的新数组
myObservableArray.removeAll()   //移除所有对象并返回新数组

ko.computed() 计算属性

visible绑定 绑定一个值来确定DOM元素显示或隐藏（改变display属性）
参数设置为一个假值（false 0 null undefined等）隐藏样式
参数设置为一个真值（true Object对象或数组 不等于null等）显示样式
text绑定  让DOM元素显示参数值
通常绑定在(<span>、<em>)，实际上任何元素都可以
讲参数值设置成元素内容，之前的内容会被覆盖
html绑定  DOM元素显示的值为绑定的参数
KO设置该参数到元素的innerHTML属性上，元素之前的内容会被覆盖
css绑定  添加或删除一个或多个css class到DOM元素上
参数是一个js对象，属性是class名称，值是 true/false
可以一次设置多个CSS class
style绑定   添加或删除一个或多个DOM元素上的style值
参数是js对象，属性是style名称，值是style需要应用的值
attr属性绑定   用于给DOM元素添加自定义属性，或绑定到已有属性
foreach绑定    循环遍历输出某个数组、集合中的内容
$data  输出数组中所有元素
$index  表示数组的下标
$parent  使用foreach元素之外的属性
if绑定   与visible绑定类似，都可以控制内容是否出现在页面中（修改DOM）
if绑定是真正控制标签是否出现在DOM中，会修改DOM结构，出于性能，不应频繁修改
with绑定   来重新定义一个上下文来绑定
click绑定   在DOM元素上添加事件 元素被点击时执行JS函数
不一定是view model上的函数，可以声明任意对象上的任何函数
通过clickBubble: false来禁止冒泡
event绑定   在DOM元素上添加事件 元素被触发时执行JS函数
通常用在keypress、mouseover、mouseout
submit绑定   绑定在form表单上添加指定的事件该form被提交时执行JS函数
只能用在form表单上
ko会阻止form表单默认的submit动作   若要继续执行默认的表单操作在submit句柄里返回true
value绑定   关联DOM元素的值到view model的属性上
主要用在表单控件<input>、<select>、<textarea>
主参数设置为value的值 之前的值将被覆盖
使用valueUpdate参数  KO将使用自定义事件而不是默认的离开焦点
