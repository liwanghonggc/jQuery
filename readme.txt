1.mouseover和mouseenter事件
  1) mouseover是JS中的,mouseenter是jQuery中的
  2) 只有经过自己才会触发mouseenter事件,经过自己或其子元素就会触发mousemove事件

2、各种选择器
   1) 筛选选择器
      $("li").children(),见下拉菜单案例

      $("#center").eq(index)  --> jq对象
      $("#center").get(index) --> js对象