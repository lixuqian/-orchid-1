# DOM对象总结

API： 已经封装好的对象属性和方法；

对象就是属性和方法的集合体；

只有对象才可以+.；

方法+（），属性没有；

标签就叫做：DOM节点 ；

在循环里点击当前的对象，就用this；

事件的三个阶段：冒泡执行：捕捉，到达目标，冒泡，

事件默认在冒泡阶段执行，冒泡的时候如果父节点和目标节点注册同样的事件，父阶段也会触发，

546 861如果第三个参数为true的话，会冒泡执行， 

如果第三个参数为false的话，会捕获执行；

absolute：不设置top、left在原有位置脱标；

如果给新增的标签，注册一样的事件，用事件委托：冒泡机制；

### 元素对象：获取DOM节点

```` js
document.getElementById //获取DOM ID节点；
document.getElementByclassName //根据类名获取元素 返回值：伪数组；
document.getElementsByTagName  // 标签名 返回值：伪数组；；
document.body //获取body ；
document.querySelector //获取指定元素的第一个，获取不到返回null，可以选择.css、#id、标签名等，可以再里面添加选择器；
document.querySelectorAll //获取全部指定的元素，返回值：伪数组，可以用forEach方法；
document.createElement //创建DOM节点，只是在js里创建出来了，在页面中没有显示；
父级DOM节点.appendChild('添加创建的DOM节点') //和createElement配合使用，是从后添加；
父级DOM节点.insertBefore('添加创建的DOM节点'，指定在谁前面添加) //和createElement配合使用，是从前添加，它有两个参数；

````





# 思想

````js
开关思想：
1.当某种情况的结果只有两种情况（开关思想，声明一个布尔类型的值表示开关）
2.随便假设开关一种状态
3.验证你的状态


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>


<script>
    var arr = [20,25,66,78,25,66,39];//【20,25,66,78,39】

    //1.声明一个空数组，存储不重复的元素
    var newArr = [];
    //2.遍历arr
    for(var i = 0;i<arr.length;i++){
        //3.检查arr[i]是否在newArr中，如果不在就添加，在就不添加(结果只有两种情况，要么在，要么不在)
        var canAdd = true;//假设可以添加
        /*遍历newArr，看newArr中是否有元素与arr[i]相等
         */
        for(var j = 0;j<newArr.length;j++){//验证开关的状态
            if(newArr[j] == arr[i]){
                //arr[i]在newArr中，此时不添加
                canAdd = false;
                break;//只要有重复元素，后面元素没有比较的必要
            }
        }

        if(canAdd == true){//如果开关状态是true，则添加
            newArr[newArr.length] = arr[i];
        }
    }

    console.log ( newArr );

    /*开关思想
    1.当某种情况的结果只有两种情况（开关思想，声明一个布尔类型的值表示开关）
    2.随便假设开关一种状态
    3.验证你的状态

     */
</script>
</body>
</html>
————————————————
版权声明：本文为CSDN博主「Mrlonely思考笔记」的原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/zjhzjh893/article/details/81707934；
````



````js
排他思想：
1.先清空所有的，然后单独设置当前；
2.基于 for 循环来实现的排他思想；
btnList[0].onclick = function () {
    //遍历清除所有的 claaName
    for (var i = 0; i< btnList.length; i++){
        btnList[i].className=''
    }
    //将响应事件的按钮，再单独设置
    btnList[0].className='current'
};
````



````js
三元表达式：
三元(三目)运算符 表达式 ? 表达式1 : 表达式2
如果表达式成立，执行表达式1，不成立执行表达式二
````





















  

## 对象

````js
this //事件注册给谁上面，就是谁，点击哪个DOM节点，this就是哪个DOM节点；
e // 形参，事件对象，描述我们一次点击行为，点击的行为当成对象；
e.stopPropagation（）//阻止冒泡，为了用户体验；
````

















### 事件、方法

```js
DOM节点.事件=function（）{要做什么事}；
'onclick' //注册事件 鼠标点击 一些情况不用+on ；
'onfocus' //有光标时：获得焦点focus；
'onblur' //光标失去：失去焦点blur；
'mousedown' //鼠标点下时触发；
'mousemove' //鼠标移动时触发；
'mouseout' //鼠标移出；
'mouseover' //鼠标移入；
'mouseup' //鼠标抬起时触发；
'onkeydown'//键盘事件 //返回值：是数字，回车键返回值为13；
.onscroll //上下左右，滚动条事件；scrollTop,scrollLeft;

注册事件： //on事件名  方法 ；
.addEventListener（'事件名称'，点击之后触发的函数）//事件监听，多次注册事件，不会覆盖；
.oncotextmenu //给整个浏览器注册事件；

事件解绑：
需要定义一个随意函数名，事件注销：begin.removerEentListener('点击事件'，函数名)；

指定父DOM节点.removeChild(被删除的DOM)；
过渡结束时事件：
transitionend:元素过渡动画结束后触发，//不能使用on的方式注册，只能使用add方式注册；
动画结束时执行事件
@keyframes 命名 {0%{}  100%{}} 
animationend //动画无限循环不会执行；
<div contenteditable="true"></div>  //在div里加入，让div变成可输入；
```











### 属性

````js
.style //更改节点元素样式，返回值：对象；
.className // 操作DOM节点上的class属性 原来的类名被完全覆盖为新的类名；
.value //得到节点中的value，更改或查看，  返回值：value值；
.classList 方法：.add（一个或多个类名用，隔开）；
.classList 方法 ：.remove（给元素删除一个或，多个）；
.classList 方法：.toggle（删除指定的类名）有类名就删除，没有就加上；
//返回值：对象 管理类名 ；
.offsetTop //得到某个元素距离他的offsetparent元素的垂直距离，由margin-top+top构成的，只能获取不能设置；
.offsetLeft //得到某个元素距离他的offsetparent元素的水平距离，由margin-left+left构成的，只能获取不能设置；
元素.clientWidth - //可视区域的宽度；
元素.clientHeight- //可视区域的高度；
.offsetParent //没有定位会一直往上找；

自定义属性： //用于存储和DOM节点一一对象关系的数据；
.dataset.自定义名  在html里 data-自定义名；
.getAttribute（'属性名'）//一般情况下用于自定义属性，返回值：查的属性值；
.setAttribute（'属性名'，属性值）//设置自定义属性；
.removeAttribute（'属性名'）//删除自定义属性；

开关属性：
.checked 复选框选项 ；
.selected 下拉框；
.disabled 按钮选项；
// 这种只有两种状态 需要赋值=true、false；

事件对象属性：
事件对象.clientX //鼠标距离可视区域的X轴距离；返回值：距离；
事件对象.clientY //鼠标距离可视区域的Y轴距离；返回值：距离；
事件对象.pageX //鼠标距离bodyX轴的距离；返回值：距离；
事件对象.pageY //鼠标距离bodyY轴的距离；返回值：距离；
事件对象.target //点到谁上面就是谁；返回值：标签；
事件对象.nodeName //返回值：大写的DOM节点的标签名；
事件对象.currentTarget // 事件注册给谁上面就是谁，与this相同；
事件对象.preventDefault //阻止浏览器默认行为；

.innerHTML //向html里添加标签，会覆盖以前的标签；
.innerText // 获取和设置DOM节点的文本信息；
.document.write()//可以识别HTML结构；

父元素.children //获取子元素：返回一个伪数组；
元素.parentNode //获取父亲节点，返回一个父亲节点；
元素.nextElementsibling //得到下一个兄弟元素；
元素.previousElementsibling //得到上一个兄弟元素；
````







# 移动端触摸事件

````js
移动端不适用click事件；

触摸事件：
touchstart- //收回触摸屏幕的时候触发；
touchmove- //会在手指触摸屏幕，移动的过程中触发；
touchend- //会在手指离开屏幕的瞬间触发
推荐使用addEventlistner ， pc端不生效；
在pc端，只能模拟移动端使用；
````



# 移动端事件对象

```` js
事件对象.touches //屏上面触摸点；
事件对象.targetouches //元素上面的触摸点；
事件对象.changedTouches //变化的触摸点；
````









# BOM

把浏览器当成一个对象，就是学历浏览器对象的各种方法和属性；

浏览器对象：window对象；

所有的window对象的属性和方法，使用时都可以忽略window；

所有的全局变量和全局函数，都是window对象的属性和方法；







## 事件 方法

````js
window.onload //等页面全部静态资源加载完毕，后面的函数才会执行；
setTimout 函数，延迟的毫秒数 //一次性定时器：需要传入两个参数，毫秒，延迟一定毫秒之后调用一次，返回值：用于停止定时器；
clearTimout //清除定时器，设定定时器的返回值；
setInterval // 永久性定时器 ； 一次性定时器：需要传入两个参数，毫秒，延迟一定毫秒之后调用一次，返回值：用于停止定时器；
clearInterval //清除永久性定时器；
后边的值前面可以放入任何数据类型，保存后为字符串，
如果存储的是对象等复杂类型，需要先将复杂类型转换为字符串，再存进去，读取时再变回对象
localStorage //可以将数据本地存储，刷新还是操作后的样子
localStorage.setItem（键，值）；//存储数据
localStorage.getItem（键）//读取数据
localStorage.removeItem（键）//删除键的值
localStorage.clear（）//全部清空
JSON //他是个字符串 []-表示数组 {}-对象 所有键必须使用双引号包起来，每个对象用,隔开，用于存储转换的。
JSON.stringify（对象）//将对象转换为JSON格式的字符串， 返回值：一个瞒住JSON格式的字符串。
JSON.parse（json格式字符串） //将JSON格式的字符串转换为对象， 返回值：依赖于你的JSON格式字符串，可能返回数组，或是对象。约定的格式为字符串
````











## 属性

````js
location // 管理浏览器地址相关行为，href='可以跳转页面'；
````









# JS基础总结

## 页面五颜六色的

```js
   <script>
  //设定函数，用一次调用一次
  function color() {
    //设定一个随机小数
    var a = Math.random();
    //将它 放大255倍 ，因为rgb颜色是0~255
    a = a * 256
      //向下取整
    a = Math.floor(a);
    return a
  }
  //设定函数，用一次调用一次
  function ni() {
    //向页面传输一个rgb颜色的值
    var b = `rgb(${color()},${color()},${color()})`
    return b
  }
  //定义颜色的值，在html页面里输出
  document.write(`<div style="background:${ni()}"></div>`)
  document.write(`<div style="background:${ni()}"></div>`)
  document.write(`<div style="background:${ni()}"></div>`)
  document.write(`<div style="background:${ni()}"></div>`)
  document.write(`<div style="background:${ni()}"></div>`)
  document.write(`<div style="background:${ni()}"></div>`)
</script>
```

### 其他

#### 四舍五入

```js
  //四舍五入 ath.round
  var r = Math.round(3.4);
  console.log(r);

  //Math.abs 求一个数的绝对值,就是求正
  var b = Math.abs(-5.5);
  console.log(b);

  //Math.max 求最大值；
  var m = Math.max(8, 6, 9, 7, 3, 2, 15);
  console.log(m);
  //Math.min求最小值
  var i = Math.min(11, 2, 9, 0, 3, 64, );
  console.log(i);
```



# join

join：让数组转换成字符串String类型



# Date

#### 时间对象

```js
  //时间对象 , 每个值后面要加括号
  //输入时间
  var date = new Date();
  //获取年
  var year = date.getFullYear();
  //获取月 月是0-11 要设定12月 要设定12加1;
  var yue = date.getMonth();
  //设定日 
  var ri = date.getDate();
  //设定时
  var shi = date.getHours();
  //设定分
  var fen = date.getMinutes();
  //设定秒
  var miao = date.getSeconds();
  //设定毫秒 1秒等于1000毫秒；
  var hm = date.getMilliseconds();
  //设定一个时间戳 也就是1970年1月1日到现在的毫秒数；
  var sjc = date.getTime();
  //一般需要唯一值得时候一般用时间戳*随机小数
  var wy = Math.random() * date.getTime();
```

# Array

#### 对元素操作

push()（把一个元素或多个元素，从数组后面添加）；

添加的数据会添加原数组里面

返回值：添加后的数组长度

它可以添加多个

```js
  //它是一个复杂数据类型,
  var arr = [1, 2, 3, 6, 4, 8];
  arr.push(9, 10, 50, 60)
  console.log(arr);
```

pop()(删除数组中最后的元素)

返回值：被删除的元素；

```js
  var arr = [1, 2, 3, 6, 4, 8];
  arr.pop()
  console.log(arr);
  
  
```

unshift()从数组前面添加一个或多个元素

返回值：添加后的数组长度

```JS
  var arr = [1, 2, 3, 6, 4, 8];
  arr.unshift(1,1,1)
  console.log(arr);


```

shift()从前面删除第一个元素；

返回值：被删除的元素

```js
 var arr = [1, 2, 3, 6, 4, 8];
  arr.shift(1,1,1)
  console.log(arr);


```

splice（）可以对数组的任何位置的增删改

```js
  var arr = ['a', 'b', 'c', ];
//第一个值是从0下标开始，第二个值是删除的个数，第三以后都是添加的值
  var res = arr.splice(0, 2, 3, 8)
  console.log(arr);
```

#### 数组与字符串互转

```js
  var str = '刘备,关羽,张飞'
  var arr = str.split(',')
  var b = arr.push(9, 10, 50, 60)
  console.log(arr);
```

### 查找元素

indexOf：经常使用，使用这个元素查找元素，能找到这个元素，就返回这个元素的下标，找不到返回-1；

```js
  var arr = [1, 10, 20, 30];
  var res = arr.indexOf(30)
  console.log(res);
  //能找到这个元素，就返回这个元素的下标，找不到返回-1；
```

### 遍历数组

for循环基础语法

forEach 遍历循环

```js
    var arr = [0, 10, 10, 10, 20];
    //可用于数组的循环
    arr.forEach(function(item, index, arr) {
      console.log(item, index, arr)
        //item 第一个循环遍历的值，第二个每个元素的下标，
        //第三个当前循环的数组
    })



    //求和
    var arr = [0, 10, 10, 10, 20];
    //可用于数组的循环
    var sum = 0;
    arr.forEach(function(item, index, arr) {
      console.log(item, index, arr)
        //item 第一个循环遍历的值，第二个每个元素的下标，
        //第三个当前循环的数组
      sum += item
      console.log(sum);

    })


filter方法
  //把数组中满足条件的元素，重新抽取出来，形成一个新的数组；
  var arr = [0, 10, 10, 10, 20];
  var vad = arr.filter(function(item, index, arr) {
    return item > 10
  })
  console.log(vad, arr);
  //arguments 伪数组没有这个方法

```

# 数组的拼接与截取

concat：拼接数组，**不改变原素组** 创建新数组返回

```js
  //他是创建一个新数组返回来，不会对原数组操作。
  var arr = [1, 2, 3];
  var res = arr.concat([4, 5, 8, 9]);
  console.log(arr);
```

slice:截取，**不对原数组操作，返回的是新数组；

```js
  //slice  返回的是新的数组，不会改变新数组
  var arr = ['a', 'b', 'c', 'd', 'e', ];
  //第一个数是从下标1（包括）开始，到下标4结束，（不包括4）
  var res = arr.slice(1, 4)
    //如果第二个参数不加，那么他就从设定的标走，知道读取完全部数组值，
    //如果都不给他就从0开始，一直截取到数组最后
  console.log(arr);
```

### 数组复制

复制不是赋值，赋值是存在一个堆的块中，复制是在堆中有两块，但是存的东西都是一样的。

数组复制有四种，建议先将前两种学明白，在工作里要用后两种方法，更加快捷

```js
  第一种方法 forEach
  var arr = [1, 2, 3, 4, 5, 6];
  var tip = [];
  arr.forEach(function(turm, index) {
    tip.push(turm)
  })
  console.log(tip);


  第二种方法 filter
  var tip = arr.filter(function(turm, index) {
    return turm
  })
  console.log(tip);


  第三种 slice
  var tip = arr.slice();
  console.log(tip);


  第四种 concat
  var tip = arr.concat();
  console.log(tip);
```

Object对象复制

复制用for in

```js
  var arr = {
    name: 1,
    mar: 2,
  }
  var tip = {}
  for (var key in arr) {
    tip[key] = arr[key]
  }
  console.log(tip);
```

# String

### 不可变性

在内存的栈上面进行加减的话会将以前的值给挤下去，处于游离状态，原始状态不会被覆盖，他会在内存上放一个新格子，如果字符串加减的或者替换的多，会使网页变得卡顿，占据内存空间

```js
var a = 'asf'
a = a+'1111'
```

### 查找

indexOf ；字符串中是否存在指定字符，存在就返回找到的下标，没有就是-1

```JS
  var a = '我爱北京天安门'
  var b = a.indexOf('爱')
  console.log(b);
```

charAt：用于查找指定位置的字符

```js
  var a = '我爱北京天安门'

  var b = a.charAt(2)
  console.log(b);
```

charCodeAt:用于查询下标处的字符的ASCII码值;

```js
  var a = '我爱北京天安门'

  var b = a.charCodeAt(2)
  console.log(b);
```

### 转为数组 案例

```js
  var str = 'www.cc.com?name="张三"&age=16'
    //需求：把用户传过来的数 解析出来 目标：{}
    //1.字符串转数组,将?分成两部分
  var arr = str.split('?');
  //将str拿到下标为1的部分
  str = arr[1]
  //再次分割&
  arr = str.split('&')
  //定义一个接受分割的值
  var one;
  //定义一个空对象
  var obj = {}
  //循环遍历，可以使str有几个=就分割几个
  arr.forEach(function(tims, index) {
    //将分割的赋值到one里面
    one = tims.split('=')
    //设定两个值，接受建和值，使他组成键值对
    var key = one[0]
    var keu = one[1]
    //将分割的第一个值和第二个值和成对象
    obj[key] = keu
  })
```

# 字符串拼接和截取

拼接 ：+；

concat ：拼接 返回一个新的拼接后的字符串。

substring：截取字符串，不操作原字符串，返回截取的字符串，

```js
  var str = 'abcdef'
    //第一个参数：截取开始下标，包括
    //第二个参数：截取到结束的下标，不包括
  var are = str.substring(0, 3)
  console.log(are);
```

substr：截取字符串，不操作原字符串，返回截取的字符串，



```js
  var str = 'abcdef'
    //第一个参数：截取开始下标，包括
    //第二个参数：截取到结束的下标，不包括
  var are = str.substr(0, 3)
  console.log(are);
```

