# jQuery语法



## jQuery初识



```
什么是jQuery
```

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

1、$(function(){});

2、$(document).ready(function(){});

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
> $('li').prevAll();前面的4
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

注意：fadeTo([[speed],opacity,[easing],[fn]])

### 滑动效果

slideDown([speed,[easing],[fn]])【下滑效果】
slideUp([speed,[easing],[fn]])【上滑效果】
slideToggle([speed,[easing],[fn]])【切换效果】

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

标签用户自己给元素添加的属性，我们称为自定义属性。比如给 div 添加 index=“1”。 

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

### jQuery **内容文本值**val()

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

### **遍历元素**each()

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

> 其他操作：$('<div>内容</div>').appendTo(ul)；添加到哪

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

## jQuery 尺寸、位置操作

### 尺寸

> width()、height()【只算width和height】
>
> innerWidth()、innerHeight()【包含padding+width】
>
> outerWidth()、outerHeight()【包含padding、border、width】
>
> outerWidth(true)、outerHeight(true)【包含padding、border、margin、width】

```
以上参数为空，则是获取相应值，返回的是数字型。
如果参数为数字，则是修改相应值。
参数可以不必写单位。

```



### 位置

位置主要有三个： offset()、position()、scrollTop()/scrollLeft();

#### offset 

**offset()设置或获取元素偏移**

> offset：距离文档的距离【left，top】

```
①offset() 方法设置或返回被选元素相对于**文档**的偏移坐标，跟父级没有关系。

②该方法有2个属性 left、top 。offset().top  用于获取距离文档顶部的距离，offset().left 用于获取距离文档左侧的距离。

③可以设置元素的偏移：offset({ top: 10, left: 30 });

```

#### position

**position() 获取元素偏移**

①position() 方法用于返回被选元素相对于**带有定位的父级**偏移坐标，如果父级都没有定位，则以文档为准。

②该方法有2个属性 left、top。position().top 用于获取距离定位父级顶部的距离，position().left 用于获取距离定位父级左侧的距离。

注意：该方法只能获取。

只读

#### scroll 滚动事件

**scrollTop()、scrollLeft()设置**或获取元素被卷去的头部和**左侧**

①scrollTop() 方法设置或返回被选元素被卷去的头部。

②不跟参数是获取，参数为不带单位的数字则是设置被卷去的头部。

scroll事件

#### 综合

课程回顾：

​	属性：prop 固有属性，attr   自定义属性  

​	事件：change事件元素发生改变	

​	文本内容值：html，text，val

​	元素操作：

​		遍历：$(元素).each(function () {i,elm})

​			$.each(对象,function (i,elm) {}) ;

​		remove;append,prepend

​		位置：offset，scrollTop

​	元素尺寸：width,height  【只算width和height】

​			innerWidth,innerHeight【包含padding+width】

​			outerWidth, outerHeight【包含padding、border、width】

## jQ事件

### 注册事件

- 语法：element.事件(function(){})

> - on() 方法在匹配元素上绑定一个或多个事件的事件处理函数

> - 语法：element.on(events,[selector],fn)

### on()方法优势

- 1、可以绑定多个事件，多个处理事件处理程序。 

   $(“div”).on({

    mouseover: function(){}, 

    mouseout: function(){},

    click: function(){}  

  });    

- 2、可以事件委派操作。事件委派的定义就是，把原来加给子元素身上的事件绑定在父元素身上，就是把事件委派给父元素。

  $('ul').on('click', 'li', function() {

  ```
  alert('hello world!');
  
  ```

  });   

- 3、动态创建的元素，click()没有办法绑定事件，on() 可以给动态生成的元素绑定事件

   $(“div").on("click",”p”, function(){

  ```
   alert("俺可以给动态生成的元素绑定事件")
  
  ```

   });   

### 解绑事件 off()

> off() 方法可以移除通过 on() 方法添加的事件处理程序。

```
    $("p").off() // 解绑p元素所有事件处理程序

    $("p").off( "click")  // 解绑p元素上面的点击事件 后面的 foo 是侦听函数名

    $("ul").off("click", "li");   // 解绑事件委托

```

> 如果有的事件只想触发一次， 可以使用 **one()**来绑定事件。

解绑：$（元素）.off();

### 自动触发事件trigger()

有些事件希望自动触发, 比如轮播图自动播放功能跟点击右侧按钮一致。可以利用定时器自动触发右侧按钮点击事件，不必鼠标点击触发

**语法**

> element.click()  // 第一种简写形式

> element.trigger("type")//第二种自动触发模式

```
$("p").on("click", function () {

  alert("hi~");

}); 

$('p').click();

$("p").trigger("click"); // 此时自动触发点击事件，不需要鼠标点击

$('div').triggerHandler('click');// 自动触发事件【这种触发事件不会触发默认行为】

```



看似两个非常相似，但是表同里不同！

下面就是他们之间的三大区别：

- 第一：trigger会导致浏览器同名的默认行为的执行，如：trigger('submit');不但会执行submit()函数的效果，也会执行表单提交的效果；

　　　而triggerHandler就不会导致默认行为的执行

- 第二：triggerHandler只会触发JQ对象集合中第一个元素的事件处理函数，也不会产生事件冒泡。而trigger不同

- 第三：这个方法的返回时事件处理函数的返回值，而不是具有可链性的JQ对象，此外，如果最开始的JQ对象集合为空，则返回undefined.

### 阻止冒泡

阻止默认行为：event.preventDefault()   或者 return  false 

阻止冒泡： event.stopPropagation()