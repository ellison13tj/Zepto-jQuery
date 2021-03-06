首先介绍一下Zepto：  
  1. 它是一个轻量化的，API类似jQuery的javascript类库。  
  2. 它是一个面向移动端的类库，虽然能在桌面客户端运行，不过仅支持高级游览器（IE10+）。  
  3. 它支持移动端“touch”有关的一些事件。  

简单的介绍完Zepto之后，我们再谈谈它和jQuery之间的区别，从功能先入手，之后会讲到大家纠结的大小，效率等问题：  
  1. 选择器的区别；Zepto实现了一些基本的选择器，排除了部分选择方式。其中不支持的有：  
    - 基本伪类选择：:first、:not(selector)、:even、:odd、:eq等通过“:”来实现选择方式。  
    - 属性选择：[attribute!=value]。
  
  2. 宽度和高度的区别（以宽度为例）；  
    1. 首先介绍jQuery的几种取值方式：  
      - .width()，返回内容宽度；![enter image description here](http://7xi9ky.com1.z0.glb.clouddn.com/1.png)  
      - .css('width')，同上，不过返回的是带完整单位的字符串。  
      - .innerWidth()，返回带padding的内容宽度；![enter image description here](http://7xi9ky.com1.z0.glb.clouddn.com/2.png)  
      - .outerWidth(boolen)，有两种情况，默认返回带padding以及border的内容宽度；当传参数“true”时，返回值将包含margin；![enter image description here](http://7xi9ky.com1.z0.glb.clouddn.com/3.png) 
  
    2. 接下来介绍Zepto的取值方式，它只提供了两种：
      - .width()，返回带border，padding的内容宽度，和jQuery里面的.outerWidth()一致。
      - .css('width')，和jQuery的方法一致。  
    3. 综上所述：  
      - 想要通过Zepto获取内容宽度，需要通过$(elm).css('width').slice(0, -2)来实现。  
      - 其他的距离以此类推。  
  3. Zepto的.offset()包含4个属性值，比jQuery多出了width和height的值。当然这个width和height同样是包含border以及padding的内容宽度。  
  4. Zepto的animate只使用css过渡效果动画（所以游览器一定要高级），对于jQuery的easings不会支持。jQuery的相对变化（"=+10px"）syntax也不支持。同时Zepto拥有总的动画设置$.fx，设置即时生效。详细可以了解官网文档。  
  5. 其他经常性用到的区别可以这里补充，如果不怎么用到的，毕竟类库本身就不同，没必要做到那么细致的了解。  

功能性的问题就对比到这里。接下来对比一些纠结性问题，这些问题的分析能帮助你如何去取舍：  
  1. 生态圈问题。jQuery拥有成熟的生态圈，能在网上找到一大堆相关的控件以及框架，遇到困难也能在社区当中寻找答案。很多招聘信息一般性也都会加熟悉jQuery等信息。这些都是Zepto所缺乏的。当然这也阻止不了Zepto使用者的热情，哪个工具不是经历从无到有的过程的。造成这个问题的原因我觉得可以有这几点：  
    - 时间问题。Zepto出生于2010年10月末，对于出生于2006年1月的大哥jQuery小了将近5年的时间。先行占领市场的肯定能多分杯羹了。  
    - 市场问题。Zepto的本意就是使用于移动端，但是移动端的发展近几年才迅猛起来。同时jQuery又出来了一版jQuery.mobile，所以很多人开发控件的时候一般性都会去选择jQuery。导致这么一个小弟一直被放在一边默默无闻。 

  2. 大小问题。Zepto的体积很小，压缩之后只有25k。因为Zepto支持移动端事件的特性，相当于jQuery（98K）和jQuery.mobile（198K，一般性连着UI一起用了，所以也不会少）的集合。虽然4G年代来了，上百KB无所谓了，优化个图片就有了，不过国内流量那么贵，依然需要省省用的。  
  3. 性能问题。Zepto的性能略差于jQuery；不过通过数十万的计算得出一个百分之几的差距，实际使用中很少会出现。而且目前移动端游览器都如此先进，就跟上面的大小问题一样，还在出那么点性能么。  
  4. 跨平台问题。想制作跨平台响应式的网站，不需要多想，请使用jQuery吧。jQuery以其优良的兼容性完胜了仅支持IE10+的Zepto。
  5. 更新问题。大哥jQuery还在不停更新当中，小弟Zepto官方最后一次更新是在2013年12月初。  

总的来讲，虽然在移动端使用Zepto占据很大优势，不过限制于各种原因，它还有很长的路要走，譬如“点透”等问题还未解决。





