1.mouseover和mouseenter事件
  1) mouseover是JS中的,mouseenter是jQuery中的
  2) 只有经过自己才会触发mouseenter事件,经过自己或其子元素就会触发mousemove事件

2、各种选择器
   1) 筛选选择器
      $("li").children(),见下拉菜单案例

      $("#center").eq(index)  --> jq对象
      $("#center").get(index) --> js对象

3、index()方法会返回当前元素在所有兄弟元素里面的索引

4、jQuery基本操作
   1) 操作样式
      css(name, value)
      $("li").addClass("basic");
      $("li").removeClass("bigger");
      $("li").toggleClass("basic");

   2) 操作属性
      attr(name, value)

      attr("checked", true)失效,jQuery1.6版本之后若没有设置该属性attr返回undefined,而checked应该返回false
      因此,对于布尔类型的属性,不要用attr方法,应该使用prop方法,它用法和attr一样,prop("checked", true)

   3) 操作动画,见京东轮播图案例
      3.1) 三组基本动画
      显示show、隐藏hide,不传参数无动画效果,可以传入参数speed、回调函数callback
      $("div").show(1000, function(){

      });

      滑入slideUp、滑出slideDown、切换slideToggle,用法和show一样,不传参数默认也有动画

      淡入fadeIn、淡出fadeOut、切换fadeToggle

      3.2) 自定义动画,见手风琴案例
      linear:线性 匀速
      $("#box3").animate({left:800}, 8000, "linear", function () {
        console.log("ha");
      });

      动画队列
        $("#btn").click(function () {
            //把这些动画存储到一个动画队列里面,一个接一个执行
            $("div").animate({left:800})
              .animate({top:400})
              .animate({width:300,height:300})
              .animate({top:0})
              .animate({left:0})
              .animate({width:100,height:100})
          })

      stop停止当前正在执行的动画,写在前面停其他动画让自己动画执行
      stop的两个参数: clearQueue,是否清楚动画队列,true or false
                     jumpToEnd,是否跳转到当前动画的最终效果

      音乐播放:   var idx = $(this).index();
                 //让对应的音乐播放,音乐播放的方法时DOM对象
                 //audio、video标签,jQuery没有提供封装,因此获取的是DOM对象,不能使用eq方法
                 $("audio").get(idx).load();
                 $("audio").get(idx).play();

   4) 节点操作
      添加节点 append、prepend、appendTo、prependTo、after、before
      清空一个元素的内容: $("div").html("")  --> 清除内容,但不会清除事件,内存泄露
                        $("div").empty()   --> 清空内容,自己还留着
                        $("div").remove()  --> 全删,自己也没了

      克隆 $("div").clone(true)  false,不传参数是深复制,不会复制事件
                                 true,深复制,会复制事件,jQuery默认就是深复制,浅复制没有意义