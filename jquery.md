# jQuery

##  jQuery概述

* 快速简洁的javascript库
* jquery：
  * 作用：优化dom操作，事件处理，动画涉及和Ajax交互
  * 优点：
    * 轻量级
    * 兼容性好
    * 优化dom操作，事件处理，动画涉及和Ajax交互
    * 支持插件
    * 免费、开源

## jQuery基本使用

* `$`就是jquery的别称（jquery顶级对象），相当于JavaScript 中的window

##  dom对象与jQuery对象

* 用原生js获取的对象就是dom对象
* 用jquery方法获取的元素就是jQuery对象`$('div')`
* dom对象和jQuery对象的属性、方法不能混用

##  dom对象与jQuery对象的转换

* js>jquery,所以原生转jQuery

  * dom对象转换为jQuery对象：`$(DOM对象)`

    ```javascript
    var myvideo = document.querySelector('video')
    $(myvideo)
    ```

* jquery转换为dom

  `$('video')[index]  `

  * index是索引号

  `$('video').get(index) `

  * index是索引号

```javascript
//方法1：
$('video')[0].play()
//方法2：
$('video').get(0).play()
```

##  jQuery选择器

* `$("#id名称")`

* `$(".类名称")`

* `$("标签名称")`

* 并集选择器`$("标签名称,标签名称")`

  * `$("div,li")`

* 交集选择器`$("标签名称.current)`

  * `$("li.current)`

* 层级选择器

  * 子代选择器（用大于符号）

    `$("父节点>亲儿子节点")`，例如:`$('ul>li')`

  * 后代选择器(用空格)

    `$("ul li")`：表示ul下面所有的li，不管是不是亲生的还是儿子生的

##   隐式迭代

* 对同一类元素进行同样的操作

* 遍历内部dom元素**存储为为数组形式**的过程就是隐式迭代
  * 就是将匹配到的所有元素斤西瓜循环遍历，执行相应的方法，而不需要我们再进行循环

##  jQuery的筛选选择器

* `$('li:first')`获取第一个li元素
* `$('li:last')`获取最后一个li元素
* `$('li:eq(2)')`获取到的li元素中，选择索引为2的元素，索引号从0开始
* `$('li:odd()')`获取到的li元素中，选择索引为奇数的元素，索引号从0开始
* `$('li:even(2)')`获取到的li元素中，选择索引为偶数的元素，索引号从0开始

##   jQuery的筛选方法

* `parent()`
  * `$('ul').parent()`
  * 查找**父级**
* `children()`
  * `$('ul').`children('li')`
  * 找**亲儿子**
* `find()`
  * `$('ul').find('li')`
  * 找所有的ul里面的li，儿子孙子重孙......
  * 找**后代**

* siblings()

  * `$('ul').siblings()`
  * 查找**亲兄弟**，不包括自己本身

* `nextAll()`

  * `$('ul').nextAll()`

  * 查找当前元素之**后的所有同辈元素**（同级的）

* `prevtAll()`

  * `$('ul').prevtAll()`
  * 查找当前元素之**前的所有同辈元素**（同级的）

* `hasClass()`

  * `$('li').hasClass('current')`
  * 检查当前元素是否含有某个特定的类，如果有返回true

* `eq()`

  * `$('li').eq(2)`相当于`$('li':eq(2))`
  * 查找下标为2的li

##  jquery中的排他思想

* 想要多选一效果：当前元素设置样式，其余兄弟清除样式

##  事件的this

* jquery事件的**this**就是当前选定事件的元素`$(this)`

## jQuery样式操作 

* `$('div').css('属性'，'值')`，其他选择器也是这么操作,属性与值必须是字符串
  * `$('div').css('background','pink')`,给所有的div设置背景颜色为粉色
* `$('div').css({'属性':'值','属性':'值','属性':'值','属性':'值'})`
* `$('div').addClass('current')`
  * 添加类
* `$('div').removeClass('current')`
  * 删除类
* `$('div').toggleClass('current')`
  * 切换类
    * 点击某一个元素，有类名就移除类名，没有就添加类名

##   类操作与className区别

* 原生js中，className会覆盖元素原先的类名
  * 这个是覆盖类 `className`
* jQuery里面类操作知识对指定类进行操作，不影响原先的类名
  * 这个是添加类 `addClass`

##   jquery动画效果

*  显示隐藏

  * `.hide()`
    * 隐藏匹配的元素。
  * `.show()`
    * 显示匹配的元素
  * `.toggle()`
    * 显示或隐藏匹配元素。

* 滑动

  * `slideDown()`
    * 下拉滑动
  * `slideUp()`
    * 上拉滑动
  * `slideToggle()`
    * 切换滑动

* 淡入淡出

  * `fadeIn()`
    * 淡入
  * `fadeOut()`
    * 淡出
  * `fadeToggle()`
    * 切换淡入淡出
  * `fadeTo()`
    * 设置透明度

* 自定义动画

  * `animate(params,时间（speed）,切换效果,回调函数)`
    * 回调函数:在动画完成时执行的函数，每个元素**只执行一次**
  * 当使用animate动画返回顶部的时候，animate动画函数里面有个scrollTop属性，可以设置位置
    * 但是时元素做动画，因此必须使用`$('body,html').animate({scrollTop:0})`

* 事件切换

  * `hover(鼠标经过时的函数（over）,鼠标移出时的函数（out）)`
  * over:鼠标移到元素上要触发的函数（相当于mouseenter）
  * out:鼠标移出元素上要触发的函数（相当于mouseleave）

  ```JavaScript
  $('.nav>li').hover(function(){},function(){})
  ```

  * 如果**hover中只写一个函数**，那么鼠标经过和鼠标离开都会触发这个函数，所以很适合与**切换**（带有toggle）的方法一起使用

* `stop()`

  * 相当于函数节流(**每一个效果之前**都需要加一个)

  * 用于停止动画或效果
  * 比如多次触发一个动画，会造成多个动画或效果排队执行，所以该方法就可以解决这个问题
  * 注意：`stop()`要写道动画效果的**前面**，相当于停止结束上一次动画，所以当多次触发一个动画时，只触发一次

## jQuery属性操作

* 设置、获取固有属性值`prop()`

  * 固有属性就是元素本身自带的属性，例如`<a>`元素里面的href等
  * 获取属性值
    * `$('a').prop('href')`
  * 设置（修改）属性值
    * `$('a').prop('href','www.baidu.com')`

* 设置、获取自定义属性值`attr()`

  * 获取属性值

    * `<div index="1"></div>`

    * `$('div').attr('index')`
    * 相当于原生`getAttribute()`

  * 设置（修改）属性值

    * `$('div').attr('index',2)`
    * 相当于原生`setAttribute()`

* h5自定义属性

  * `<div data-index="1"></div>`
  * `$('div').attr('data-index')`

* 数据缓存的`data()`

  * 这个里面的数据时存放在元素的内存里,并不会修改dom元素结构，一旦页面刷新，之前存放的数据都将被移除

  * `data(k,v)`

    * 向备选元素添加附加数据

  * `data(k)`

    * 获取数据

    * `<span></span>`

    * `$('span').data('name','andy')`
      * 这个时候页面上是没有数据的

    * $('span').data('name'）`
      * 这样就能获取到andy

  * h5自定义属性也能使用（不需要前面的那个data-）

    * `<div data-index="1"></div>`
    * `$('div').data('index')`

## jQuery文本属性值

* 获取元素内容:`html()`

  * `$('div').html()`

  * 相当于原生的`innerHTML`

* 修改元素内容:`html()`

  * `$('div').html('修改的内容为这个')`

* 获取元素文本内容:`text()`

  * `$('div').text()`

  * 相当于原生的`innerText`

* 修改元素文本内容:`text()`

  * `$('div').text('修改的内容为这个')`

* 获取设置表单值:`val()`

  * 相当于原生的value
  * `$('input').val()`

* 修改表单值:`val()`

  * `$('input').val('修改的内容为这个')`

## jQuery元素操作

* 遍历元素`each()`

  * 给同一类元素做不同操作
  * `$('div').each(回调函数function (index索引号,dom元素对象){})`
    * 注意：由于回调函数的第二个参数是dom对象，如果想要使用jquery方法，**需要将dom对象转换为jquery对象**
    * `$(dom元素对象)`
      * dom对象转换为jquery对象

  * `$.each(object,function(index索引号,element遍历的内容){})`

    * `$.each()`可用于遍历任何对象，主要用于数据处理，比如数组、对象

    * 例如：`$.each($('div'),function(index,element){})`

      或`$.each(arr,function(index,element){})`等

* 动态创建元素

  * `$('标签')`
    * `$('<li></li>')`

* 添加元素

  * 内部添加

    * `element.append("内容")`
      * `$("ul").append(li)`
      * 把内容放到**匹配元素最后面**，类似原生appendChild（尾插）
      * 与目标元素是父子关系

    * `element.prepend("内容")`
      * `$("ul").prepend(li)`
      * 把内容放到**匹配元素最前面**（头插）
      * 与目标元素是父子关系

  * 外部添加

    * `element.after("内容")`
      * `$("ul").after(ol)`
      * 在ul之后
      * 与目标元素是兄弟关系
    * `element.before("内容")`
      * `$("ul").before(ol)`
      * 在ul之前
      * 与目标元素是兄弟关系

* 删除元素

  * `element.remove()`

    * `$("ul").remove()`
    * 删除元素本身

  * `element.empty()`

    * `$("ul").empty()`
    * 删除匹配元素的所有子节点

  * `element.html("")`

    * `$("ul").html("")`

    * 删除匹配元素的所有子节点

##   jQuery事件注册

* 单个事件注册：
  * `element.事件(function(){})`
  * `$('div').click(function(){} )`

##  jQuery事件处理

* `on()`：

  * 在匹配元素上版顶一个或多个事件的事件处理函数

  * `element.on(events事件类型，元素的子元素选择器，回调函数)`

  * ```javascript
    $('div').on({
        mouseenter:function(){
            $(this).css("background","red")
        },
         click:function(){
            $(this).css("background","yellow")
        },
         mouseleave:function(){
            $(this).css("background","blue")
        }
    })
    ```

  * ```javascript
    $('div').on("mouseenter mouseleave ",function(){
            $(this).toggleClass("current")
        }
    })
    ```

  * **事件委托操作**
    
    * `$('ul').on('click','li',function(){})`
  * 动态创建元素
    * 动态创建的元素，click()不能绑定事件，但是**on()可以给动态生成的元素绑定事件**
    * `$('ul').on('click','li',function(){})`

* `off()`：

  * 解绑事件，off()可以移除on()方法添加的事件处理程序

  * `$('ul').off()`
    * 解绑ul上的所有事件
  * `$('ul').off('click')`
    * 解绑ul上的click事件
  * `$('ul').off('click','li')`
    * 解绑ul上的事件委托

* `one()`

  * 如果有的事件只想触发一次，可以使用one()来绑定事件
  * `$('ul').one('click',function(){})`

* `trigger()`:

  * 自动触发事件
    * `$('ul').click()`
    * `$('ul').trigger('事件')`
      * `$('ul').trigger('click')`
    * `$('ul').triggerHandler('click')`
      * 不会触发元素的默认行为

##  jQuery事件对象

* 只要有事件被触发，就会有事件对象的产生

* `element.on(events事件类型，元素的子元素选择器，function(事件对象){})`

  * `$('ul').on('click',function(event){event.stopPropagation()})` 

  * 阻止默认行为
    * `event.preventDefault`()
    * `return false`
  * 阻止冒泡
    * `event.stopPropagation()`

##   jQuery对象的拷贝方法

* `$.extend()`:

  * 如果想要把某个对象合并（拷贝）给另一个对象使用

  * `$.extend()`

    * 参数一：`true`为深拷贝  `false`浅拷贝，默认为`false`

    * 参数二：要拷贝的目标

    * 参数三：待拷贝对象（将其拷贝给参数2）

    * 浅拷贝
    
      * ```javascript
        //拷贝对象
        var targetObj = {id:0,msg:{
            sex:"男"
        	}
        };
        //被拷贝对象 
        var obj = {
        	id:1,
        	name:"andy"
            msg:{
            	age:20
        	}
        }
        //将obj拷贝给targetObj
        $.extend(targetObj,obj)
        //如果原先数据中也有相同属性，以拷贝的属性值为准（会覆盖）
        console.log(targetObj) //  {id:1,name:"andy", msg:一个地址}
        //浅拷贝是把被拷贝对象复杂类型中的地址拷贝给目标对象，修改目标对象被拷贝对象会被影响
        targetObj.msg.age=18
        console.log(obj)//  {id:1,name:"andy", msg:{age:18}}
        ```
    
    * 深拷贝
    
      * ```javascript
        //拷贝对象
        var targetObj = {id:0,msg:{
            sex:"男"
        	}
        };
        //被拷贝对象 
        var obj = {
        	id:1,
        	name:"andy"
            msg:{
            	age:20
        	}
        }
        //将obj拷贝给targetObj
        $.extend(true,targetObj,obj)
        //如果原先数据中也有相同属性，会合并。如果属性名相同，以被拷贝对象为准
        console.log(targetObj) //  {id:1,name:"andy", msg:{ sex:"男",age:20}}
        targetObj.msg.age=18
        console.log(obj)//  {id:1,name:"andy", msg:{age:20}}
        console.log(targetObj) //  {id:1,name:"andy", msg:{ sex:"男",age:18}}
        ```



##  jQuery多库共存的方法

* 解决其他库也是使用`$`作为标识符（标识符冲突）
* 解决方法
  * 把里面的`$`统一改为jQuery
  * 释放$的控制权
    * `jQuery.noConflict()`

##  jQuery插件

* jquery插件库
* jquery之家
* 图片懒加载：就是等页面滑动到可视区域，再显示图片
* 使用jQuery插件库EasyLazyload时
  * 注意：此时的js引入文件和js调用必须写到Dom元素（图片）最后面
* 全屏滚动（fullpage.js）

##   bootstrap中的js插件

* bootstrap框架时依赖jQuery开发的，因此里面的js插件使用，也必须引入jQuery

## jQuery尺寸

* 注意：以下方法如果参数为空，则是获取相应值，并返回数字；如果参数为数字，则数修改相应值，参数不用写单位

* `width()`获取匹配元素的宽度，只算width

* `height()`获取匹配元素的高度，只算height

* `innerWidth()`获取匹配元素的宽度，width+padding

* `innerHeight()`获取匹配元素的高度，height+padding

* `outerWidth()`获取匹配元素的宽度，width+padding+border

* `outerHeight()`获取匹配元素的高度，height+padding+border

* `outerWidth(true)`获取匹配元素的宽度，width+padding+border+margin

* `outerHeight(true)`获取匹配元素的高度，height+padding+border+margin

  

## jQuery位置操作



* `offset()`

  * offset（）方法设置或获取被选元素相当于**文档**的偏移（上top，左left）坐标，跟父级没有关系
  * 设置偏移
    * `offset({left:200,top:200})`

* `position()`

  * position（）方法获取被选元素相当于**带有定位的父级**的偏移（上top，左left）坐标，如果所有父级都没有定位，则以文档为准

* `scrollTop()`

  * `scrollTop()`方法设置或获取被选元素被卷去的头部

* `scrollLeft()`

  * `scrollLeft()`方法设置或获取被选元素被卷去的左侧

  









































 















