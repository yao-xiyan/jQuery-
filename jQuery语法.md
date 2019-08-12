# jQuery语法



##  jQuery初识



	### 什么是jQuery

- jQuery 就是-JavaScript类库  就是一个或者多个.js文件
- **具有链式结构**
  - 一定要从当前元素出发,可以一直往后点点点
- **隐式迭代**
  - 遍历内部DOM元素(伪数组形式存储)的过程叫做隐式迭代

### 学jQuery的目的

- 使用更加简单，提高开发效率
- 以前的主流问题是浏览器的兼容问题，jq里面几乎都解决了(现在不关注了)

### 入口函数

代码开始执行的地方。入口函数的执行时机是页面结构解析渲染完毕，在图片等等外部资源回来之前，我们就不需要等待某些大文件的加载，可以提高浏览器的运行的速度，也可以提高用户的体验。

```javascript


$(function(){});

$(document).ready(function(){});

jQuery(function(){});

jQuery(document).ready(function(){});
```

### jQuery对象和DOM对象

**jq的本质：利用$对DOM对象包装后产生的对象(伪数组的方式)**

- jQery 对象只能用jQuery 对象方法
- JS  DOM对象只能用DOM的属性和方法

- DOM对象  ==>  jq对象
  - $('div') [index]       index 是索引号 


  ```js
  var btn = documenti.querySelector('inpute');
  $(btn).css('background','yellow');
  ```
- $('div') .get(index)    index 是索引号 

```js
var btn = documenti.querySelector('inpute');
$(btn).get(index).css('background','yellow');
```


- jq对象  ==>  DOM对象
  - $(DOM对象)

```js
//去数组中找每一个
$('input')[0]
//
console.log($('input').get(0));

```

### 顶级对象

1.**jQuery :   ==>   $**

2.DOM的顶级对象**window**

3.$ 是 jQuery 的别称，在代码中可以使用 jQuery 代替 ​$，但一般为了方便，通常都直接使用 $ 。

4.$ 是jQuery 的顶级对象， 相当于原生JavaScript中的 window。把元素利用​$包装成jQuery对象，就可以调用jQuery 的方法。

## jq选择器

**$('基本的css选择器:eq(索引)') - 从基本的选择器中找到所有满足条件的元素之后，根据索引进行筛选**

选择器L方法：**parent()\、children()、find()、siblings、eq()**

$('#id')==》指定id元素

$('*')==》所有元素

$('.class')==》指定class元素

$('div')==》根据标签获取元素

$('div,p,li')==》获取多个

$('li.class')==>交集获取

$('ul>li')==>子代

$('ul li')==>后代

### 筛选选择器

$('li:first')：第一个元素

$('li:last')：最后一个元素

$('li:eq(2)')==》索引为2【查找指定索引的元素】

$('li:odd')==》索引为奇数

$('li:even')==》索引为偶数

注意：索引是从0开始的

### 筛选方法

> $('li').parent()父级
>
> $('ul').children('li');子集【儿子级】【如果不加参数，获取所有的，如果添加指定的元素，按照指定的找】
>
> $('ul').find('li')后代【后代级】
>
> $('li').siblings('li')兄弟
>
> $('li'),nextAll();后面的
>
> $('li').prevAll();前面的
>
> 判断是否具有某个类名：$('div').hasClass('aaa')
>
> $('div').eq(index);指定索引方法【eq推荐用方法】

> ```
> 重点记住： parent()  children()  find()  siblings()  eq()
> ```
>
> 小知识点：添加事件，show方法，hide方法，toggle方法

## jQ动画

### 显示隐藏效果

show([speed,[easing],[fn]])【显示】
hide([speed,[easing],[fn]])【隐藏】
toggle([speed,[easing],[fn]])【切换】

（1）参数都可以省略， 无动画直接显示。
（2）speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。
（3）easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。
（4）fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。

### 淡入淡出效果

fadeIn([speed,[easing],[fn]])【淡入】
fadeOut([speed,[easing],[fn]])【淡出】
fadeToggle([speed,[easing],[fn]])【切换】
fadeTo([[speed],opacity,[easing],[fn]])【到达某个位置】

（1）参数都可以省略。
（2）speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。
（3）easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。
（4）fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。

注意：fadeTo([[speed],opacity,[easing],[fn]])

（1）opacity 透明度必须写，取值 0~1 之间。
（2）speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。必须写
（3）easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。
（4）fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。

### 滑动效果

slideDown([speed,[easing],[fn]])【下滑效果】
slideUp([speed,[easing],[fn]])【上滑效果】
slideToggle([speed,[easing],[fn]])【切换效果】

（1）参数都可以省略。
（2）speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。
（3）easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。
（4）fn:  回调函数，在动画完成时执行的函数，每个元素执行一次

### 事件切换

hover( [over] , out)

$('div').hover(function () {//鼠标进入的函数},function () {//鼠标离开的函数});

```
 (1) over:鼠标移到元素上要触发的函数（相当于mouseenter）
 (2) out :鼠标移出元素要触发的函数（相当于mouseleave）
（3）如果只写一个函数，则鼠标经过和离开都会触发它

```

**区别**

```
mouseover  ==  mouseenter
mouseover  :  支持事件冒泡
mouseenter ： 不支持事件冒泡
```





```js
$( 'div' ).hover(function () {

$(this).children('ul').slideDown();

},function(){
    $(this).children('ul').slideUp();
});


```

### **自定义动画** **animate**

语法：animate(params,[speed],[easing],[fn])

参数：
（1）params: 想要更改的样式属性，以对象形式传递，必须写。 属性名可以不用带引号， 如果是复合属性则需要采取驼峰命名法 borderLeft。其余参数都可以省略。
（2）speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。
（3）easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。
（4）fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。



### **动画排队及其停止**

```
动画或者效果一旦触发就会执行，如果多次触发，就造成多个动画或者效果排队执行。
；
停止排队:stop()

(1）stop() 方法用于停止动画或效果。
(2)  注意： stop() 写到动画或者效果的前面， 相当于停止结束上一次的动画
	
```

## **jQuery** **属性操作**

### **元素固有属性值** **prop()**

- **设置一个值为获取**
- **两个值为设置**

### 元素自定义属性值**attr()**

用户自己给元素添加的属性，我们称为自定义属性。比如给 div 添加 index=“1”。 

**获取属性语法**

attr(''属性'')      // 类似原生 getAttribute()

**设置属性语法**

attr(''属性'', ''属性值'')   //类似原生 setAttribute()		

### 数据缓存 **data()**【了解】

当做变量存储

data() 方法可以在指定的元素上存取数据，并不会修改 DOM 元素结构，所以元素上无法查看。一旦页面刷新，之前存放的数据都将被移除。

 **附加数据语法**

data(''name'',''value'')   // 向被选元素附加数据   

**获取数据语法**

date(''name'')             //   向被选元素获取数据   

### jQuery **内容文本值**

**普通元素内容** **html()**（相当于原生inner HTML)

​	获取：html()   // 获取元素的内容

​	设置：html(''内容'')   // 设置元素的内容

**普通元素文本内容** **text()   (**相当与原生 **innerText**)

​	获取：text()   // 获取元素的文本内容

​	设置：text(''文本内容'')   // 设置元素的文本内容

**表单的值** **val()****（ 相当于原生***value**)

​	获取：val()   // 获取表单的值

​	设置：val(''内容'')  // 设置表单的值

## 元素操作

主要是遍历、创建、添加、删除元素操作。

### **遍历元素**

jQuery 隐式迭代是对同一类元素做了同样的操作。如果想要给同一类元素做不同操作，就需要用到遍历。

> 语法1：$("div").each(function(index, domEle) { xxx; }）

```
1. each() 方法遍历匹配的每一个元素。主要用DOM处理。 each 每一个

2. 里面的回调函数有2个参数：  index 是每个元素的索引号;  demEle 是每个DOM元素对象，不是jquery对象

3. 所以要想使用jquery方法，需要给这个dom元素转换为jquery对象  $(domEle)
```

语法2：$.each(object，function(index, element){ xxx;}）

```
1. $.each()方法可用于遍历任何对象。主要用于数据处理，比如数组，对象

2. 里面的函数有2个参数：  index 是每个元素的索引号;  element  遍历内容
```

### 创建元素

语法：$(''<li></li>'');    

### **添加元素**

element.append(''内容'') [把内容放入匹配元素内部最后面，类似原生 appendChild。]

element.prepend(''内容'') 把内容放入匹配元素内部最前面。

- **外部**添加

element.after(''内容'') // 把内容放入目标元素后面

element.before(''内容'')    //  把内容放入目标元素前面 

①内部添加元素，生成之后，它们是父子关系。

②外部添加元素，生成之后，他们是兄弟关系。

### 删除元素

element.remove()   //  删除匹配的元素（本身）

element.empty()    //  删除匹配的元素集合中所有的子节点（删除内容）

element.html('''')   //  清空匹配的元素内容

①remove 删除元素本身。

②empt() 和  html('''') 作用等价，都可以删除元素里面的内容，只不过 html 还可以设置内容。