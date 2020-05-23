# HTML5 + CSS3 学习记录，后面增加 Less 与 Sass 学习内容

1. [视频链接](https://www.bilibili.com/video/av53158375)
2. 笔记为个人纪录，章节号与文件夹序号对应

## 01 什么是 HTML5，HTML5 新特性概览-新的标签属性

1. H5 并不是新的语言，而是 HTML 语言的第五次重大版本修改。
2. 支持：所有的主流浏览器都支持 H5（Chrome，FireFox，Safari，IE9 及以上版本，IE9 为有选择的支持非全部支持）。
3. 改变了用户与文档的交互方式：多媒体：video,audio,canvas。
4. 增加了其他的新特性：语义特性，本地存储，网页多媒体，二维三维变换，特效(过渡，动画)。
5. 相对于 HTML4：

    + 进步：抛弃了一些不合理不常用的标记和属性
    + 新增了一些标记和属性--表单
    + 从代码角度而言，H5网页结构代码更加简洁

6. 语义标签：[HTML 标签参考](https://www.w3school.com.cn/tags/index.asp)

    | 标签名  |       作用       |
    | :-----: | :--------------: |
    |   nav   |     表示导航     |
    | header  |     表示页眉     |
    | footer  |     表示页脚     |
    |  main   |   表示主要内容   |
    | article |       文章       |
    |  aside  |   主题内容之外   |
    | footer  | 文档或者页的页脚 |

    + 语义标签兼容性问题的两种解决方式：创建标签，将行级元素设置为块级元素；引入 html5shiv.js 第三方插件

7. 表单新增属性，[type 属性](https://www.w3school.com.cn/html5/html_5_form_input_types.asp)

    + 以下主要针对input标签

      |          type           |                    效果                    |
      | :---------------------: | :----------------------------------------: |
      |          text           |              输入普通文本信息              |
      |        password         |             密码输入，显示为*              |
      |          email          |           邮箱输入，校验邮箱格式           |
      |           tel           | 电话号码输入，主要针对移动端调用数字键盘入 |
      |           url           |                  网址输入                  |
      |         search          |           带有清空按钮的文本输入           |
      |          range          |                  范围滑条                  |
      |          color          |                  颜色拾取                  |
      |          time           |               时间选择，时分               |
      |          date           |              日期选择，年月日              |
      | datetime/datetime-local |           日期时间选择，年月时分           |
      |          month          |                  月份选择                  |
      |          week           |                   周选择                   |

    + 新增其他表单属性

      |    属性名    |                                效果                                |
      | :----------: | :----------------------------------------------------------------: |
      | placeholder  |                      输入框提示信息，提示占位                      |
      |  autofocus   |                            自动获取焦点                            |
      | autocomplete |            自动完成，on/off，需指定name性并成功提交一次            |
      |   require    |                      必须输入，不输入无法提交                      |
      |   pattern    |                    正则匹配，如自定义手机号验证                    |
      |   multiple   |                    文件拾取多选，多个邮箱输入等                    |
      |     form     | 为 form 标签之外的表单元素指定隶属的表单，从而跟随表单一同提交数据 |

8. HTML5 引入一种新的 `select` 下拉选择菜单 `datalist`；`keygen` 元素是密钥对生成器，当提交表单时，会生成两个键，一个是私钥，一个是公钥；`output` 元素用于放置输出内容。
9. HTML5 新增表单事件：`oninput` 监听表单控件的内容改变；`onincalid` 监听表单提交失败的事件，其中 `this.setCustomValidity()` 可以修改表单控件验证的错误提示信息。
10. HTML5 两种进度条：`progress`，`meter`。
11. HTML5 提供的媒体标签：`audio`，`video`，注意 `source` 的使用。
12. HTML5 提供的获取 DOM 元素的两种方式：`querySelector`，`querySelectorAll`。
13. HTML5 提供的类样式操作 `classList.add()` / `.toggle()` / `.remove()` / `.contains()` / `.item()`。
14. HTML5 提供的自定义属性（data-）：定义和获取的方法。

## 02 HTML5 提供的新的接口

1. 网络接口：`online`，`offline`，分别监听网络链接与断开。
2. 全屏 API：`requestFullScreen()`：开启全屏，`cancelFullScreen()`：取消全屏，`fullScreenElement`：监听全屏状态。
3. 文件读取接口 `FileReader`

    + 方法

      | 方法名               | 作用                                                                    |
      | :------------------- | :---------------------------------------------------------------------- |
      | readAsText()         | 读取文本文件(可以使用 txt 打开的件)，返回文本字符串值，默认编码是 UTF-8 |
      | readAsBinaryString() | 读取任意类型的文件，回二进制字符串                                      |
      | readAsDataURL()      | 读取文件获取一段以 data 开头字符串，这段字符串的本质就是DataURL         |
      | abort()              | 中断读取                                                                |

    + FileReader 提供了一个完整的事件模型，用来捕获读取文件时的状态

      | 事件名      | 作用                           |
      | :---------- | :----------------------------- |
      | onabort     | 读取文件断开时触发             |
      | onerror     | 读取错误时触发                 |
      | onload      | 文件读取成功完成时触发         |
      | onloadend   | 读取完成时触发，无论成功还失败 |
      | onloadstart | 开始读取时触发                 |
      | onprogress  | 读取文件过程中持续触发         |

4. HTML5 提供的元素拖拽接口，主要是通过元素拖拽事件来完成，分为两类：

    + 应用于被拖拽元素的事件：

      | 事件名      | 调用时刻                         |
      | :---------- | :------------------------------- |
      | ondrag      | 整个拖拽过程都会调用             |
      | ondragstart | 当拖拽动作开始时调用             |
      | ondragleave | 当鼠标离开拖拽元素原始位置时调用 |
      | ondragend   | 当拖拽结束时调用                 |

    + 应用于目标元素的事件：

      | 事件名      | 调用时刻                                   |
      | :---------- | :----------------------------------------- |
      | ondragenter | 当拖拽元素进入时调用                       |
      | ondragover  | 当停留在目标元素上时调用                   |
      | ondrop      | 当在目标元素上松开鼠标时调用(浏览器默阻止) |
      | ondragleave | 当鼠标离开目标元素时调用                   |

    + 通过事件捕获来获取当前元素 `e.target`

    + 通过事件源参数 `e.dataTransfer()` 来实现数据的存储和获取

5. HTML5 提供的获取地理位置的接口 `navigator.geolocation`，通常浏览器禁止定位获取，需要地图开发的时候采用第三方工具的支持，如百度地图 api。
6. HTML5 提供的两种web存储方式，sessionStorage 和 localStorage

    + sessionStorage，数据存储到当前页面中，页面关闭则数据消失

      | 方法名              | 作用                           |
      | :------------------ | :----------------------------- |
      | setItem(key, value) | 存储数据，键值对方式           |
      | getItem(key)        | 获取数据，按键获取             |
      | removeItem(key)     | 删除数据，按键删除             |
      | clear()             | 清空所有sessionStorage存储数据 |

    + localStorage，数据存储到硬盘中；页面关闭数据不消失，同浏览器不同窗口共享数据，但是不同浏览器不共享数据，删除数据需要手动删除；常用方法与 sessionStorage 相似。

7. HTML5 提供的应用缓存；cache manifest 文件

    + 优势：可配置需要缓存的资源；网络无连接应用仍可使用；本地读取缓存资源，提升访问速度，增加用户体验；减少请求，缓解服务器负担。

    + Cache Manifest 基础：CACHE MANIFEST 文件开头、CACHE：要缓存的文件、NETWORK：需要向服务器请求的文件、FALLBACK：无法获取时替换的文件

8. 视频播放器案例-自定义媒体播放控件。[HTML5 视频/音频参考手册](https://www.w3school.com.cn/tags/html_ref_audio_video_dom.asp)

    + 常用方法

      | 方法名  | 功能 |
      | :------ | :--- |
      | load()  | 加载 |
      | play()  | 播放 |
      | pause() | 暂停 |

    + 常用属性

      | 属性名      | 作用               |
      | :---------- | :----------------- |
      | currentTime | 视频播放的当前进度 |
      | duration    | 视频总时长         |
      | pause       | 当前视频播放状态   |

    + 常用事件

      | 事件名       | 调用时机                           |
      | :----------- | :--------------------------------- |
      | oncanplay    | 视频可以开始播放时触发             |
      | ontimeupdate | currentTime 变化时触发，如开始放等 |
      | onended      | 播放完毕时触发                     |

## 03 CSS3 简介与基本应用

1. CSS3 原则渐进增强，优雅降级。使用手册(语法)

    | 标识         | 表示         |
    | :----------- | :----------- |
    | []           | 表示可选项   |
    | &#124;&#124; | 表示或者     |
    | &#124;       | 表示多选一   |
    | ？           | 表示0个或1个 |
    | {}           | 表示范围     |

2. 选择器

    + 属性选择器

      | 属性选择器     | 介绍                       |
      | :------------- | :------------------------- |
      | E[attr]        | 拥有attr属性的E标签        |
      | E[attr=value]  | attr属性为value的E标签     |
      | E[attr*=value] | attr属性内含value的E标签   |
      | E[attr^=value] | attr属性以value开头的E标签 |
      | E[attr$=value] | attr属性以value结尾的E标签 |

    + 伪类选择器，

      | 锚伪类(a 标签使用) | 状态           |
      | :----------------- | :------------- |
      | a:link             | 未访问的链接   |
      | a:visited          | 已访问的链接   |
      | a:hover            | 鼠标移到的链接 |
      | a:active           | 选定的链接     |

      | 伪类选择器                           | 介绍                                                               |
      | :----------------------------------- | :----------------------------------------------------------------- |
      | 兄弟选择器                           | 选择兄弟元素(同层)                                                 |
      | +                                    | 相邻的指定的兄弟元素                                               |
      | ~                                    | 所有的指定的兄弟元素                                               |
      | 相对于父元素的结构伪类               | 以某元素相对于其父元素或弟元素的位置来获取元素的结构伪类           |
      | E:first-child                        | E的父元素下的第一个元素且为E素                                     |
      | E:last-child                         | E的父元素下的最后一个元素且为E素                                   |
      | E:first-of-type                      | E的父元素下的第一个E元素，滤其他元素                               |
      | E:last-of-type                       | E的父元素下的最后一个E元素，过滤其他元素                           |
      | E:nth-child()                        | E的父元素下指定位置的E元素,括内可以为索引(从1开始)、表达式、关键字 |
      | E:nth-of-type()/E:nth-last-of-type() | E父元素下指定位置的E元素，过滤其他元素                             |
      | E:empty                              | E的父元素下的内容为空的E元素                                       |
      | E:target                             | 配合锚点使用，当元素被触发为锚点元素时候触发此伪类样式             |

    + 伪元素选择器 -- 伪元素：虚拟的元素，不会在DOM元素中生成

      | 伪元素选择器     | 介绍                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
      | :--------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
      | E:before,E:after | 1.是一个行内元素，如果像设宽高则需要转换为块：`display: block`，`float: **position`:  2.必须添加 content，哪怕不设置内容，也要 `content:""`  3.E:after，E:before 在旧版本里是类，在新版本里是为元素，新版本下 E:before、E:after 被自动识别为 E::before、E::after,按为元素来对待，这样做的目的是用来做兼容处理  4.E::before 定义在一个素的内容之前插入 content 属性定义的内容和样式 5.E::after 定义在一个元素的内容之后插入 content 属定义的内容和样式  6.IE6、7、8中不支持此伪元素，CSS 中 E:after、E:before 属于伪类，且没有伪元素的概念 CSS3 中提出为元素的概念 E::after、E:before，并且归到了伪元素当中，伪类里就不再存在E:after、E:befor 了 6.DOM元素的左膀右臂 |
      | E::first-letter  | 文本的第一个字母或字(不是组)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
      | E::first-line    | 文本的第一行                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
      | E::selection     | 可改变选中文本的样式                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

3. 颜色
    + RGBA：R:红色，G:绿色，B:蓝色，A:透明度；数值(0-255)、百分比(0%-100%)，A 取值为 0-1。
    + HSLA：Hue：色相，色调，0(或360)表示红色，120表示绿色，240表示蓝色，也可去其他数值来指定颜色。取值为0-360，过渡为：红橙黄绿青蓝紫红；Saturation：饱和度，取值为 0.0%-100.0%；Lightness：亮度，取值为 0.0%-100.0%，50%为平衡值；Alpha：透明度，取值为 0-1 之间。
    + opacity：只能针对整个盒子设置透明度，子盒子及内容会继承父盒子的透明度；使用 rgba 来控制颜色，相对于 opacity 不具有继承性。
    + transparent：不可调节透明度，始终完全透明。

4. 文本阴影(shadow):text-shadow

    + 语法：

      ``` css
        text-shadow: none|<length>none|[<shadow>,]*<shadow>
        或
        text-shadow: none|<color>[,<color>]*
      ```

      也就是：
    text-shadow: [颜色(color)] x 轴(X Offset) y轴(Y Offset) 模糊半径(Blur),[颜色(color) x轴(X Offset) y轴(Y Offset) 模糊半径(Blur)]...
    或者
    text-shadow: [x轴(X Offset) y轴(Y Offset) 模糊半径(blur) 颜色(color)],[x轴(X Offset) y轴(Y Offset) 模糊半径(blur) 颜色(color)]...

    + 取值：

    &lt;length&gt;：长度值，可以是负值，用来指定阴影的延伸距离。其中X Offset是水平偏移值，Y Offset是垂直偏移值。
    &lt;shadow&gt;：阴影的模糊值，不可以是负值，用来指定模糊效果的作用距离。
    &lt;color&gt;：指定阴影颜色，也可以是rgba透明色。

    + 图示：
    ![text-shadow](https://i.loli.net/2019/09/17/LSpi34w5YXRoDZq.jpg)

5. 盒模型

    + 默认情况下，CSS设置的盒子宽度仅仅是内容区的宽度，而非和子的宽度。同样，高度类似。真正盒子的宽度(在页面呈现出来的宽度)和高度，需要加上一下其他的属性。例如：
    padding + border + width = 盒子的宽度；
    padding + border + height = 盒子的高度；
    很明显，这部只管很容易出错，造成网页中其他元素的错位。

    + CSS3种可以通过box-sizing来制定和模型，即可指定为content-box、border-box,这样我们计算盒子大小的方式就发生了改变；
    content-box：对象的实际宽度等于设置的width值和border、padding之和；
    border-box：对象的实际宽度就等于设置的width值，即使定义有border和padding也不会改变对象的实际宽度。

6. 圆角：border-radius

    + 等宽高容器 - 向圆形进行设置

      | 参数个数   | 修改方面                               |
      | :--------- | :------------------------------------- |
      | 一个参数   | 四个角都改变圆角，容器宽高一半时为正圆 |
      | 两个个参数 | 左上和右下，右上和左下搭配改变圆角     |
      | 三个参数   | 左上，右上和左下，右下搭配进行改变     |
      | 四个参数   | 左上，右上，右下，左下进行改变         |

    + 非等宽高容器 - 向椭圆进行设置，一个角有水平/垂直两个方向上的圆角设置，设置时以“/”进行分割。

    + 单独设置某个角的圆角：border-top-left-radius、border-top-right-radius、border-bottom-left-radius、border-bottom-right-radius

7. 使用 CSS3 设计一个安卓机器人，主要使用圆角、伪元素before、after，盒模型。

8. 边框阴影：box-shadow

    + 语法

      ``` css
        box-shadow: h v blur spread color inset
      ```

    + 参数

      | 参数名 | 作用                                           |
      | :----: | :--------------------------------------------- |
      |   h    | 水平方向的偏移值                               |
      |   v    | 垂直方向的偏移值                               |
      |  blur  | 模糊值，可选                                   |
      | spread | 阴影尺寸，扩展和收缩阴影的大小，可选           |
      | color  | 颜色，可选，默认黑色                           |
      | inset  | 内阴影，可选，不设置默认外阴影，设置后为内阴影 |

## 04 CSS3 中的渐变效果，背景样式，图片边框，过渡效果，变换效果

1. 渐变：渐变是 CSS3 当中比较费夫多彩的一个特性，通过渐变我们可以实现许多绚丽的效果，有效的减少图片的使用数量，并且句有很强的适应性和可扩展性。可分为线性渐变、径向渐变。

    + linear-gradient 线性渐变指沿着某条直线朝一个方向产生渐变效果
    语法：

      ``` html
        linear-gradient([<point>||<angle>,]?<stop>,<stop>[,<stop>]*)
      ```

      参数说明：

      | 参数                     | 说明                                                                                                                                                                                                                                       |
      | :----------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
      | point &#124;&#124; angle | 表示线性渐变的向；to left:设置渐变为从右到左，相当于270deg；toright:设置渐变从左到右，相当于90deg；to top:设置变从下到上，相当于0deg；to bottom:设置渐变从上下，相当于180deg。这是默认值，等同于留空不写。该参也可以直接指定度数，如45deg. |
      | stop                     | 起点颜色，可以指定颜色的位置                                                                                                                                                                                                               |
      | stop                     | 重点颜色，还可以在后面添加更多的参数，表示多种颜色的渐变                                                                                                                                                                                   |

    + radial_gradient 径向渐变值从一个中心点开始沿着四周产生渐变效果
    语法：

      ``` css
        <radial-gradient> = radial-gradient([[<shape>||<size>][at <position>]?, | at <position>,]?<color-stop>[,<color-stop>]+)
      ```

      参数说明：

      | 参数             | 说明                                                                                                                                                              |
      | :--------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
      | &lt;position&gt; | 确定圆心的位置。如果提供2参数，第一个表示横坐标，第二个表示纵坐标；如果只提供个，第二个值默认为50%，即center.                                                     |
      | shape            | 渐变的形状ellipse为椭圆形，circle为形。默认为ellipse，如果元素形状为正方形元素，ellipse和circle效果一样                                                           |
      | size             | 渐变的大小，即渐变到哪里停止，它有四个值closest-side：最近边，farthest-side：最远边closest-corner：最近角；farthest-corner：最角。默认是最远的角farthest-corner。 |
      | color            | 指定颜色rgba、hsla                                                                                                                                                |

    + 重复渐变：`repeating-linear-gradient()`，`repeating-radial-gradient()`。

2. 背景

    + 背景颜色 `background-color: key/rgba/hsla;`

    + 背景图片 `background-image: url();`

    + 背景平铺 `background-repeat: round/space;` round:图片缩放后平铺，space:团片不缩放平铺，在图片之间产生相等的间距值

    + 滚动容器时背景的行为 `background-attachment: fixed/scroll/local`; fixed：背景图片的位置固定不变，scroll：当滚动网页时背景图片也会跟随滚动。当滚动当前容器时 local 和 scroll 的区别：前者背景图片会跟随内容一起滚动，后者不会跟随滚动。

    + 背景图片尺寸 background-size：

      | 参数      | 说明                                                                                                                                                                                                                                                          |
      | :-------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
      | 宽度 高度 | 按设置宽高设置背景图片                                                                                                                                                                                                                                        |
      | 宽度 auto | 按设置宽高等比例缩放图片设置背景图片                                                                                                                                                                                                                          |
      | content   | 按比例调整图片大小使图片宽高自适应整元素的背景区域，使图片全部包含在容器中。1.当图片大容器：将图片缩小，有可能造成容器空白区；2.当图片小容器：将图片放大，有可能造成容器空白区。                                                                              |
      | cover     | 与content正好相反，背景图片按比例缩放适应真个背景区域，如果真个背景区域不足以容纳整个背景片，那么图片会溢出；1.当图片大于容器：等比例缩小，填满整个区域，有可能造成图片某些区域不可见；2.当图小于容器：等比例放大，填满整个区域，有可能造成某个方上内容溢出。 |

    + 背景坐标原点 background-origin

      | 参数        | 效果                                              |
      | :---------- | :------------------------------------------------ |
      | border-box  | 从 border(边框)位置开始填充背景，与border重叠     |
      | padding-box | 从 padding(内边距)位置开始填充景，会与padding重叠 |
      | content-box | 从内容区域开始填充背景                            |

    + 背景裁切 background-clip 设置的是裁切，控制的是显示。与background-origin来配合设计幽灵按钮，提升按钮响应区域。

      | 参数        | 效果                     |
      | :---------- | :----------------------- |
      | border-box  | 实际显示border以内的内容 |
      | padding-box | 显示padding以内的内容    |
      | content-box | 显示content以内的内容    |

3. 边框图片 border-image

    + border-image-source：指定边框图片的路径，默认只是讲整个图片缩放填充到容器四个角点。

    + border-image-slice：设置背景图片的四个方向的裁切距离，fill：设置内容内部填充。

    + border-image-width：边框图片的宽度，如果没有设置，那么默认就是元素的原始边框宽度。图片边框的本质是背景，并不会影响元素内容的放置，内容只会被容器的 border 和 padding 影响。

    + border-image-outside：扩展边框。

    + border-image-repeat：设置边框的平铺，stretch 默认值，拉伸效果；repeat 直接重复平铺；round 将内容缩放进行完整的重复平铺。

4. 过渡 transition 通过过渡 transition，我们可以在不使用 Flash 动画或 JavaScript 的情况下，当元素从一种样式变换为另一种样式是为元素添加效果，要实现这一点，必须规定两项内容：规定希望把效果添加到哪个 CSS 属性上，及规定效果的时长。

    + 语法

      ``` css
        transition: property duration timing-function delay;
      ```

    + 参数说明：
    transition 属性是一个简写属性，用于设置四个过渡属性：`transition-property|transition-duration|transition-timing-function|transition-delay`

      | 参数                       | 说明                           |
      | :------------------------- | :----------------------------- |
      | transition-property        | 规定设置过渡效果的CSS性名称    |
      | transition-duration        | 规定完成过渡效果需要多秒或毫秒 |
      | transition-timing-function | 规定速度效果的度曲线           |
      | transition-delay           | 定义过渡效果同时开始           |

    + 补充transition-timing-function:属性规定过渡效果的速度曲线

      | 值                       | 说明                                                                                 |
      | :----------------------- | :----------------------------------------------------------------------------------- |
      | linear                   | 规定以相同的速度开始至结束夫人过渡效（等于cubic-bezier(0, 0, 1, 1)）                 |
      | ease                     | 规定慢速开始，然后变快，然后提速结束的过效果（等于cubic-bezier(0.25, 0.1, 0.25, 1)） |
      | ease-in                  | 规定以慢速开始的过渡效果（等cubic-bezier(0.42, 0, 1, 1)）                            |
      | ease-out                 | 规定一慢速结束的过渡效果（等cubic-bezier(0, 0, 0.58, 1)）                            |
      | ease-in-out              | 规定一慢速开始和结束的过渡效果（于cubic-bezier(0.42, 0, 0.58, 1)）                   |
      | cubic-bezier(n, n, n, n) | 在cubic-bezier数中定义自己的值。取值0-1。                                            |
      | steps(num)               | 设置过渡效果分几次来完成                                                             |

    + 使用建议：因为 transition 最早是由 webkit 内核浏览器提出来的，mozilla 和opera 都是最近版本才支持这个属性，而我们大众型的浏览器 IE 全家都不支持，另外由于各大现代浏览器 FireFox、Safari、Chrome、Opera 都还不支持 W3C 的标准写法，所以在应用 transition 时，我们有必要加上各自的前缀，最好在放上我们 W3C 的标准前缀的写法，只要浏览器支持我们的 transition 属性，那么这种效果就会自动加上去。

      ``` css
        -moz-transition: all 5s ease 1s;
        -webkit-transition: all 5s ease 1s;
        -o-transition: all 5s ease 1s;
        transition: all 5s ease 1s;
      ```

5. transform 通过 CSS3 transform 变换，我们能够对元素进行移动、缩放、旋转、斜切等操作，执行完毕之后恢复到原状态。

    + 2D 移动：translate()。使用translate可以把元素从原来的位置移动，移动参照元素左上角原点。tx是一个代表X轴(横坐标)移动的向量长度，当其值为正值时，元素向X轴右方向移动，反之既反；ty是一个代表Y轴(纵坐标)移动的向量长度，当其值为正值时，元素向Y轴下方向移动，反之既反；也可以单独设置translateX(tx),translateY(ty)，若参数是百分比，则参照元素本身。
    语法：

      ``` css
        transform: translate(tx) | translate(tx, ty)
      ```

    + 2D 缩放：scale()，缩放 scale() 函数让元素根据中心原点对对象进行缩放，默认的值为 1，因此 0.01 到 0.99 之间的任何值，都使这个元素缩小；而任何大于或等于 1.01 的值，都使这个元素放大，缩放是参照元素的中心。sx：用来指定横向坐标(X轴)方向的缩放量，sy：用来指定纵向坐标(Y轴)方向的缩放量。也可以使用 scaleX(sx)、scaleY(sy) 单独进行设置。
    语法：

      ``` css
        transform: scale(sx | sy) | scale(sx, sy);
      ```

    + 2D 旋转：rotate()，旋转 rotate() 函数通过指定的角度参数对元素根据对象原点指定一个 2D 旋转。它主要在二维控件内进行操作，接受一个角度值，用来指定旋转的幅度，如果这个值为正值(单位deg)，元素相对原点中心顺时针旋转，若这个值为负值，则相对元素中心逆时针旋转。设置旋转轴心在元素中设置样式 transform-origin: 参数：x，y 或者关键字(left top right bottom)
    语法：

      ``` css
        transform: rotate(angle);
      ```

    + 2D 斜切：skew()。能够让元素倾斜显示，它可以将一个对象以其中心位置围绕着X轴和Y轴按照一定的角度倾斜，角度值，单位deg。这与 rotate() 函数旋转不同，rotate() 函数只是旋转，而不会改变元素的形状。skew() 函数不会旋转而是改变元素的形状。ax 用来 指定元素水平方向(X轴)倾斜角度；ay 用来指定元素垂直方向(Y轴)倾斜角度，如果未显式设置这个值，其默认为0。也可以使用 skewX(ax)、skewY(ay) 来进行单独设置。
    语法：

      ``` css
        transform: skew(ax) | skew(ax, ay);
      ```

    + 多个 2D 变化使用一个 transform 属性，用空格隔开。注意旋转时元素的坐标系会变化，所以一般先移动后旋转。

    + 3D 移动：`translate3d(x, y, z)` 使元素在这三个维度中移动，也可以分开设置，如 translateX(length),translateY(length),translateZ(length)。

    + 3D 缩放：`scale3d(number, number, number)` 在这三个维度上进行缩放，也可以分开设置 scaleX()，scaleY()，scaleZ()。

    + 3D 旋转：rotate3d(x, y, z, angle) 指定需要进行旋转的坐标轴上的向量和角度(同时在三个轴进行旋转)，单独设置围绕某个轴旋转 rotateX(angle)，rotateY(angle)，rotateZ(angle)

    + 透视/景深效果：左手法则；
    `perspective(length)` 为一个元素设置三维透视的距离；仅作用于元素的后代，而不是其元素的本身；当 `perspective:none/0` 时，相当于没有设置 `perspective(length)`，比如你要建立一个小立方体，长宽高都是 200px,如果你的perspective<200px,就相当于站在盒子里面开的结果，如果 perspective 非常大，那就是站在非常远的地方看（立方体已经成了小正方形了），一位置 perspective 属性制定了观察者与z=0平面的距离，使具有三维位置变换的元素产生透视效果。perspective-origin 属性规定了镜头在平面上的位置。默认使放在元素的中心。transform-style：使呸转换的子元素保留其 3D 转换(需设置在父元素中)，取值：flat 子元素将不保留其3D位置-平面方式，preserve-3d 子元素将保留其3D位置-立体方式。

6. 动画 animation

    + 动画设置步骤，先创建动画在将动画赋值给某个元素。

    + 创建动画 使用 `@keyframes name{}` 来创建动画；开始可以使用 0% 或 from 来标记，结束可以使用 100% 或 to 来标记，百分比表示动画执行到整个动画耗时时长的百分比时间。

    + 之后在要设置动画的元素上进行配置，animation-name: 指定动画的名称，即使用哪个动画。animation-duration:设置动画的总耗时；这两项必须都要设置。

    + `animation-iteration-count`：设置动画的播放次数，默认为 1，可以使用数值进行设置或者 infinite 设置为无限次。

    + `animation-direction: alternate;` 设置动画来回交替。

    + `animation-delay`: 设置动画开始前的延迟。

    + `animation-fill-mode`: 设置动画结束时的状态，默认情况下，动画执行完毕之后，会回到原始状态。forwards 设置动画结束时的状态，保持动画结束时的状态；backwards：设置动画开始时的状态，如果设置有延迟且元素用开始状态，则延迟时立刻进入开始状态；both：则同时设置开始和结束时的状态，即以上两者都设置。

    + `animation-timing-function`: 设置动画时间函数，linear、ease。

    + `animation-play-state`: 设置动画的播放状态：paused 暂停，running 播放。

7. web 字体和字体图标，可以为自己的网页指定特殊的字体，无需考虑用户电脑上是否安装了此特殊字体，从此吧特殊字体处理成图片的时代便成为了过去，它的支持成都比较好，甚至 IE 低版本浏览器也能支持。

    + 字体格式，不同浏览器所支持的字体格式是不一样的，常见的字体格式：TureTpe(.ttf) 格式、OpenType (.otf格式)、Web Open Type (.woff格式)、Embedded Open Type (.eot)格式、SVG (.svg格式)。阿里巴巴字体库：[iconfont](https://www.iconfont.cn/)

    + 字体图标，常见的是吧网页常用的一些小图标，借助工具帮助我们生成一个字体包，然后就可以想使用文字一样使用图标了。优点：将所有图标打包成字体库，减少请求；具有矢量性，可保证清晰度；使用灵活，便于维护。生成字体图标文件：[iconfont](https://www.iconfont.cn/)

8. 多列布局，CSS3 中心出现得多列布局(multi-column)是传统HTML网页块状布局模式得有力扩充。这种新语法能够让 Web 开发人员轻松的让文本呈现多列显示。我们知道，当一行文字太长时，读者读起来就比较费劲，有可能读错行或读串行；人们的视点从文本的一端移到另一端、然后换到下一行的行首，如果眼球移动浮动过大，他们的注意力就会减退，很难读下去。所以为了最大效率的使用大屏幕显示器，页面设计中需要限制文本的宽度，让文本按多列呈现，就像报纸上的新闻排版一样。

    + 常用属性：
      | 属性名       | 作用                                          |
      | :----------- | :-------------------------------------------- |
      | column-count | 设置列的具体个数                              |
      | column-width | 控制列的宽度                                  |
      | column-gap   | 两列之间的缝隙间隔                            |
      | column-rule  | 规定列之间的宽度、样式和颜色                  |
      | column-span  | 规定元素硬横跨多少列(n：跨n列，all：跨所有列) |

9. 伸缩布局、弹性布局、伸缩盒子：布局的传统解决方案，基于合模型，依赖 display 属性 + position 属性 + float 属性。他对于那些特殊布局非常不方便。CSS3 在布局方面做了非常大的改进，使得我们对块级元素的布局排列边得十分零话，适应性非常强，其强大的伸缩性，在响应式中可以发挥极大的作用。

    + 重要属性
    display: flex：如果一个容器设置了这个属性，那么这个盒子里面的所有直接子元素都会自动的变成伸缩项(flex item)。
    justify-content：设置或检测弹性盒子元素在主轴(横轴)方向上的对齐方式
    对齐语法：

      ``` css
        justify-content: flex-start | flex-end | center | space-between | space-around
      ```

      | 属性值        | 效果                                                                                                 |
      | :------------ | :--------------------------------------------------------------------------------------------------- |
      | flex-start    | 让子元素从父容器起始位置排列                                                                         |
      | flex-end      | 让子元素从父容器的结束位置排列                                                                       |
      | center        | 让子元素从父容器的中间位置开始排列，子素相对于父容器水平居中                                         |
      | space-between | 左右对齐父容器的开始结束位置，间平均分裂，产生相同的间距                                             |
      | space-around  | 将多余的空间平均分布在每一个子素两边，类似于marigin: 0 auto;造成盒子间的间距是两边盒子外围间距的两倍 |

    + flex-flow 属性，是flex-wrap和flex-direction两个属性的综合
      flex-wrap：控制子元素是否换行显示，默认不换行

      | 属性值       | 效果                                   |
      | :----------- | :------------------------------------- |
      | nowrap       | 不换行，宽度不够则子元素收缩           |
      | wrap         | 换行，宽度不够子元素换行               |
      | wrap-reverse | 反转，原来从上到下换行反转为从到上换行 |

      flex-direction：设置子元素的排列方向，就是用来设主轴方向，默认主轴方向是水平的

      | 属性值         | 效果                                           |
      | :------------- | :--------------------------------------------- |
      | row            | 主轴水平方向，从左到右；侧轴垂直方向，从上下   |
      | row-reverse    | 主轴水平方向，从右到左；侧轴垂直向，从上到下   |
      | column         | 主轴垂直方向，从上到下；侧轴水平方向，左到右   |
      | column-reverse | 主轴垂直方向，从下到上；侧轴水平方向，从左到右 |

    + flex属性，flex属性是 flex-grow、flex-shrink 和 flex-basis 的缩写，默认值为 0 1 auto，后两个属性可选。
    `flex-grow`：定义扩张比例，扩展子元素的宽度,设置当前元素应该占据剩余空间的比例值；比例值的计算:当前子元素的flex-grow / 所有兄弟元素的 flex-grow 的和；flex-grow 默认值为0，说明子元素并不去占据父元素剩余空间。
    `flex-shrink`：定义收缩比例，通过设置比例值来计算收缩的控件；比例值的计算：当前子元素 flex-shrink / 所有兄弟元素的 flex-shrink 的和；flex-grow 默认值为1，说明所有子元素等比例缩放。
    `flex-basis`：伸缩盒子布局的的基本参考值，一般使用默认值。
    flex 的语法便是依次为这三个属性赋值，但是大多数情况下没必要使用这种语法，当使用 flex 缩写时，大多数情况下没必要使用这种语法；而是采用直接赋值一个数字来指定伸缩项目该占用的剩余空间比例，本质上是在设置 flex-grow 属性；flex: auto 属性值被设置为 auto 的伸缩项目，会根据主轴自动伸缩以占用所有剩余空间。

    + align-items：设置子元素(伸缩项)在侧轴方向上的对齐方式，在父元素中设置所有的子元素的对齐方式；单独设置某个子元素的在侧轴方向上对齐方式使用 align-self。

      | 属性值     | 作用                                                         |
      | :--------- | :----------------------------------------------------------- |
      | center     | 设置伸缩项在侧轴方向上居中对齐                               |
      | flex-start | 设置伸缩项在侧轴方向上顶部对齐                               |
      | flex-end   | 设置伸缩项在侧轴方向上底部对齐                               |
      | stretch    | 拉伸，让伸缩项(没有设置侧轴方向上的长时)在侧轴方向上拉伸填满 |
      | baseline   | 文本基线对齐                                                 |

10. 栅格系统，栅格布局，该部分学习视频来自于[此处](https://www.bilibili.com/video/av66220144)。

    + display: grid; 可以将一个容器设置为栅格布局容器，栅格容器一般使用块布局，也可以使用行布局 inline-grid。再将一个容器设置为栅格容器后可以通过 grid-template-rows 与 grid-template-columns 两个属性分别对行和列进行分割

      grid-template-rows与grid-template-columns属性值

      | 属性值                         | 说明                                                                                                                  |
      | :----------------------------- | :-------------------------------------------------------------------------------------------------------------------- |
      | 多个像素值                     | 按像素值将栅格容器按行按列进行划分，内部元素依次布局在每个栅格(单元格)中                                              |
      | 多个百分比                     | 按百分比将栅格容器按行按列进行划分，内部元素依次布局在每个栅格(单元格)中                                              |
      | 使用repeat()函数进行重复性设置 | 第一个参数为重复的次数，第二个参数为重复划分的标准，可以为像素百分比等                                                |
      | 按比例划分                     | 使用一定比例划分，即使容器的尺寸发生变化之后，容器内的元素还是按比例布局                                              |
      | 自动填充                       | 在知道容器的宽高的情况下可以考虑自动填充，将repeat()函数的第一个参数设置为auto-fill，第二个参数设置以多大尺寸进行填充 |

    + 控制单元格间距留白，可以使用 padding、margin 等常规手段来实现。其次提供了 row-grap、columns-grap 两个属性来分别设置行间距和列间距，还可以通过 grap 属性来同时设置行列间距。

    + 通过栅格线来放置元素：
    按栅格线编号放置元素，每一行，每一列的栅格线都有编号，行列栅格线的编号都是从1开始。通过设置 grid-row-start 和 grid-row-end 属性设置开始和结束的栅格线可以实现元素跨列；通过设置 grid-column-start 和 grid-column-end 属性设置开始和结束的栅格线可以实现元素跨行。这种设置得出来的元素空间只能为矩形。
    在对 Grid 容器进行行列划分时，可以在中间穿插对栅格线的命名，之后便可以使用栅格线的名字来对元素进行布局；同样也可以使用 repeat() 函数来重复设置，因为重复设置的行列栅格线名称分别相同，所以在使用时，需要再指定列号。

    + 根据起始结束定位元素：
    通过偏移量来定位元素：在 grid-column-end、grid-row-end 通过 span 属性值后跟一个整数，来设置元素跨多少列或跨多少行。
    通过 grid-row、grid-column 两个属性可以直接指定元素的起始与结束位置，中间使用“/”进行分割，其中第二个参数可以时结束位置，也可以是偏移量。

    + 根据栅格区域定位元素：
    可以使用 grid-area 属性来按区域定位元素位置，属性值为：起始行列栅格线编号和结束行列栅格线编号，使用“/”进行分割，即：上栅格线编号/左栅格线编号/下栅格线编号/右栅格线编号；可以理解为是按栅格线编号布局的另一种方式；同样在对栅格线进行命名后可以在栅格线编号先加上名称。
    使用 grid-template-areas 属性来对栅格区域进行命名，一行一行进行命名；属性值：每一行的命名为字符串单元格的命名使用空格分开，不同行命名分别在不同字符串中进行设置；在对单元格(栅格)区域进行命名后，会自动为栅格线进行命名，如“header-start、header-end”；除了使用栅格区域名称来定位元素外，我们同样也可以使用自动生成的栅格线命名来定位元素。
    在对单元格区域进行命名时，如果某些元素就是按顺序在连续的单元格中排列，那么可以不命名单元格，也就没有进行单元格元素定位，只需要按顺序在容器中写入元素即可。但是为了防止对其他行的单元格命名造成影响，需要使用一个点号“.”或多个连续的点号来进行占位。

    + 流动处理机制：
    栅格系统的默认流动方向为先行后列，即一行排列完之后再从下一行开始，使用 grid-auto-flow 属性可以修改栅格的默认流动方向，属性值：row，按行排列；column，按列排列；另外还有一个属性值，dense添加后会将后面的元素填满前面元素偏移留下的空白单元格。

    + 栅格系统中的对齐方式：
      栅格整体对齐方式：元素撑不满容器一行的时候可以使用justify-content属性来设置单元格整体水平对齐方式。
      justify-content属性值:

      | 属性值        | 说明                             |
      | :------------ | :------------------------------- |
      | start         | 元素开始与容器开始对齐           |
      | end           | 元素结束与容器结束对齐           |
      | center        | 所有元素整体处于容器水平中间位置 |
      | space-around  | 元素平均分配容器行空间           |
      | space-between | 元素是与容器两端对齐             |
      | space-evenly  | 元素完全平均分配容器水平空间     |

      同样也有设置元素相对于容器垂直空间的对齐方式的属性：align-content 参数与 justify-content 类似，这两个属性与flex 中的这两个属性类似。可以使用 place-content 属性来设置栅格整体垂直和水平的对齐方式，属性值：垂直对齐方式的参数 水平对齐方式的参数；若只给一个参数，则水平垂直都使用这种对齐方式。
      栅格内元素同样也存在的布局的控制：justify-items、align-items 两个属性用来设置整体栅格内元素的水平和垂直对齐方式；属性值有：start、end、center、stretch，默认为 stretch 拉伸撑满整个单元格。同样也存在类似的属性同时设置整体栅格内元素的对齐方式，place-items。若要对某个单元格进行栅格内对齐方式的控制，则需要 justify-self、align-sel f两个属性进行控制。组合单独设置特定单元格内元素的对齐方式则需要 place-self 属性。

## Less 全面解析

### Less 简介、下载并使用，快速上手案例

1. 有了 CSS，为什么还需要 Less？

    (1) CSS（层叠样式表）是一门历史悠久的标记性语言，同 HTML 一道，被广泛应用于万维网（World Wide Web）中。HTML 主要负责文档结构的定义，CSS 负责文档表现形式或样式的定义。作为一门标记性语言，CSS 的语法相对简单，对使用者的要求较低，但同时也带来一些问题：CSS 需要书写大量看似没有逻辑的代码，不方便维护及扩展，不利于复用，尤其对于非前端开发工程师来讲，往往会因为缺少 CSS 编写经验而很难写出组织良好且易于维护的 CSS 代码，造成这些困难的很大原因源于 CSS 是一门非程序式语言，没有变量、函数、SCOPE（作用域）等概念。

    (2) Less 为 Web 开发者带来了福音，它在 CSS 的语法基础上，引入了变量，Mixin（混入），运算以及函数等功能，大大简化了 CSS 的编写，并且降低了 CSS 的维护成本，就像它的名称所说的那样，Less 可以让我们用更少的代码做更多的事情。

2. 什么是 Less？

    (1) Less CSS 是一种劢态样式语言，属于 CSS 预处理语言的一种，它使用类似 CSS 的语法，为 CSS 的赋予了动态语言的特性，如变量、继承、运算、函数等，更方便 CSS 的编写和维护。

    (2) Less CSS 可以在多种语言、环境中使用，包括浏览器端、桌面客户端、服务端。

    (3) 说明：本质上，Less 包含一套自定义的语法及一个解析器，用户根据 这些语法定义自己的样式规则，这些规则最终会通过解析器，编译生成对应的 CSS 文件。Less 并没有裁剪 CSS 原有的特性，更不是用来取代 CSS 的，而是在现有 CSS 语法的基础上，为 CSS 加入程序式语言的特性。

3. Less 的获取

    (1) 官网： [英文官网](http://lesscss.org/)，[中文官网](http://lesscss.cn/)

    (2) Less.js[下载地址](https://github.com/less/less.js)

    (3) Less.js 最新版本：v3.11.1

4. Less 初体验

    (1) 初始化基本目录结构

    ``` menu
    project
    └───js
    │   │   less.min.js
    └───less
    │   │   style.less
    │   index.html
    ```

    (2) 从官网下载一份 less.js 或 less.min.js 放到 js 目录中

    (3) 自己写一个简单的实例 less 文件，命名为 style.less，内容如下：

    ``` less
    @color: red;
    #header {
        color: @color;
    }
    h2 {
        color: @color;
    }
    ```

    (4) 在 index.html 文件中按如下顺序引入，index.html 内容如下：

    ``` HTML
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <link rel="stylesheet/less" type="text/css" href="./less/01style.less">
        <script type="text/javascript" src="./js/less.min.js"></script>
        <title>Less 初体验</title>
    </head>
    <body>
        <div id="header">
            这是网页头部
        </div>
        <h2>
            这是 h2 标题
        </h2>
    </body>
    </html>
    ```

    (5) 运行查看效果，注意：：JavaScript 无法访问本地的 .less 文件，因此需要一个 http 服务器，可以使用 live-server，相对较为简单。
    ![运行效果](http://image.acmx.xyz/msj%2F01chutiyan.jpg)

    (6) 注意：

    + 一定要注意引用的顺序，一定是先引用 .less 再引入 .js，而且 less 的写法与 css 有点不一样。
    + 上述过程的运行原理图
    ![运行原理](http://image.acmx.xyz/msj%2Flijie.jpg)

### Less 语言特性

1. 概览：作为 CSS 的一种扩展，Less CSS 不仅向下兼容 CSS 的语法，而且连新增的特性也是使用 CSS 的语法。这样的设计使得学习 Less 很轻松，而且你可以在任何时候回退到 CSS。

2. 变量

    (1) 变量基本上是每个语言脚本上都会涉及的一个小小知识点，是学好语言脚本的必备之路。Less 中也可以设置变量，然后通过变量可以改变整个网站的设计风格。良好的掌握 Less 中变量的用法，是 Less 的基础。

    (2) 变量

    + 变量语法：使用方法就是在 `@` 后添加变量名称然后与变量值用冒号 `:` 链接，在使用变量的时候也是以 `@变量名` 的方式使用，如下

      ``` less
      // 01.var.less
      @width: 100px;
      .w {
          width: @width;
      }
      // 编译后的 css 代码
      .w {
          width: 100px;
      }
      ```

    + 变量作用域：如果对同一个变量定义两次的话，在当前作用域中最后一次定义的将被使用。这与 CSS 的机制类似，最后一次定义的值会成为这个属性的值。若定义在嵌套之中，那么这个变量就只能服务于这个嵌套之内的属性了。变量也是没有顺序可言的，只要页面里有，都会按顺序覆盖，按顺序加载。如下案例：

      ``` less
      // 02.scope.less
      @width: 200px;
      .meng {
          @width: 100px;
          .long {
              @width: 50px;
              width: @width;
              @width: 20px;
          }
          width: @width;
      }
      // 编译后的 css 为
      .meng {
          width: 100px;
      }
      .meng .long {
          width: 20px;
      }
      ```

    再如，下面的例子，因为 less 中变量没有顺序而言，这样也是可以的

      ``` less
      // 03.scope.less
      .short {
          width: @w;
          @o: 9%;
      }
      @w: @o;
      @o: 100%;
      // 编译后的 css 代码
      .short {
          width: 9%;
      }
      ```

    + 字符串插值：变量可以用像 `@{name}` 这样的结构，以类似 Ruby 和 PHP 的方式嵌入到字符串中，如：

      ``` less
      // 04strinter.less
      @imgUrl: "http://image.acmx.xyz";
      .bgBox {
          background-image: url("@{imgUrl}/msj%2Flijie.jpg")
      }
      // 编译后的 css 代码
      .bgBox {
          background-image: url("http://image.acmx.xyz/msj%2Flijie.jpg")
      }
      ```

    + 选择器插值：如果需要在选择器中使用 Less 变量，只需要铜鼓哦使用和字符串插值一样的 `@{selector}` 即可，如：

      ``` less
      // 05selectorinter.less
      @myName: redBox;
      .@{myName}{
          width: 500px;
          height: 500px;
          background-color: red;
      }
      // 编译后的 css 代码
      .redBox {
          width: 500px;
          height: 500px;
          background-color: red;
      }
      ```

    + media query 作为变量：如果你希望在 media query 中使用 Less 变量，你可以直接使用普通的变量方式。因为 `~` 后面的值不是被编译的，所以可以用作 media query 的参数，如下例：

      ``` less
      // 06mediaquery.less
      @singleQuery: ~"max-width: 768px";
      .colorBox {
          width: 700px;
          height: 700px;
          background-color: red;
      }
      @media screen and (@singleQuery) {
          .colorBox {
              width: 500px;
              height: 500px;
              background-color: blue;
          }
      }
      // 编译后的 css 代码
      .colorBox {
          width: 700px;
          height: 700px;
          background-color: red;
      }
      @media screen and (max-width: 768px) {
          .colorBox {
              width: 500px;
              height: 500px;
              background-color: blue;
          }
      }
      ```

    + 引用变量值的变量：用一个变量值的变量，在定义变量值时使用其他的变量来赋值，如下：

      ``` less
      // 07varref.less
      @width: size;
      @height: size;
      .box {
          width: @width;
          height: @height;
      }
      // 编译后的 css 代码
      .box {
          width: 200px;
          height: 200px;
      }
      ```

    (3) 混合 Mixins：在 Less 中，混合可以将一个定义好的 class A 轻松的引入到另一个 class B 中，从而简单实现 class B 继承 class A 中的所有属性。我们还可以带参数地调用，就像使用函数一样。

    + 继承类名：在 Less 中，可以定义一些通用的属性集为一个 class，然后在另一个 class 中去调用这些属性。如果我们现在需要在任何 class 中引入那些通用的属性集，那么我们只需要在任何 class 中调用就可以了。任何 CSS class、id 属性集都可以以通样的方式引入。如下：

      ``` less
      // 08extclass.less
      .width {
          width: 500px;
      }
      #height {
          height: 500px;
      }
      .box {
          .width;
          .innerBox {
              #height;
              .width;
          }
          height: 700px;
      }
      // 编译后的 css 代码
      .width{
          width: 500px;
      }
      #height {
          height: 500px;
      }
      .box {
          width: 500px;
          height: 700px;
      }
      .box .innerBox {
        width: 500px;
        height: 500px;
      }
      ```

    + 带参数混合：在 Less 中，你还可以像函数一样定义一个带参数的数形结合，然后在其他选择器中像调用方法一样调用它，如下实例：

      ``` less
      // 09argsmix.less
      .width(@width) {
          width: @width;
      }
      #height(@height) {
          height: @height;
      }
      .box {
          .width(500px);
          .innerBox {
              #height(300px);
              .width(50%);
          }
          #height(500px);
      }
      // 编译后的 css 代码
      .box {
          width: 500px;
          height: 500px;
      }
      .box .innerBox {
          width: 500px;
          height: 500px;
      }
      ```

    + 隐藏属性继承：你也可以定义不带参数属性集集合，如果你想隐藏这个属性集合，不让他暴漏到 CSS 中去，但是你还想在其他的属性集合中引用，你会发现这个方法非常的好用，示例如下：

      ``` less
      // 10hideargs.less
      .width() {
          width: 500px;
      }
      #height() {
          height: 500px;
      }
      .box {
          .width();
          #height();
      }
      // 编译后的 css 代码
      .box {
          width: 500px;
          height: 500px;
      }
      ```

    + 默认值混合：还可以像这样给参数设置默认值，有了默认值，我们可以不用设置属性值也能被调用，如下：

      ``` less
      // 11defaultarg.less
      .width(@width: 500px) {
          width: @width;
      }
      #height(@height: 500px) {
          height: @height;
      }
      .box {
          .width();
          #height(700px);
      }
      // 编译后的 css 代码
      .box {
          width: 500px;
          height: 700px;
      }
      ```

    + 多参数混合：
      + 多个参数可以使用分号或者逗号分隔，这里推荐使用分号分隔，因为逗号有两重含义：它既可以表示混合的参数，也可以表示一个参数中一组值的分割符。
      + 使用分号作为参数分隔符意味着可以将逗号分隔的一组值作为一个变量处理。换句话说，如果编译器在混合的定义或者是调用中找到至少一个分号，就会假设参数是使用分号分隔的，所有的逗号都属于参数中的一组值的分隔符。
      + 2 个参数，每个参数都含有通过逗号分隔的一组值的情况：`.name(1, 2, 3; something, else)`。
      + 3 个参数，每个参数只含一个数字的情况：`.name(1, 2, 3)`。
      + 使用一个象征性的分号可以创建一个只含一个参数，但参数包含一组值的混合：`.name(1, 2, 3;)`。
      + 逗号分隔的一组值参数的默认值：`.name(@param1: red, blue;)`。使用相同的名字和同样数量的参数定义多个混合是合法的。在被调用时，Less 会应用到所有可以应用的混合上，示例如下：

        ``` less
        // 12multparams.less
        .mixin(@color) {
            background-color: @color;
        }
        .mixin(@color; @width: 20px) {
            background-color: @color;
            width: @width;
        }
        .mixin(@color; @width; @height: 20px) {
            background-color: @color;
            width: @width;
            height: @height;
        }
        .div1 {
            .mixin(red);
        }
        .div2 {
            .mixin(blue, 30px);
        }
        .div3 {
            .mixin(green, 30px, 50px);
        }
        // 编译后的 css 代码
        .div1 {
            background-color: red;
            width: 20px;
        }
        .div2 {
            background-color: blue;
            width: 30px;
            height: 20px;
        }
        .div2 {
            background-color: green;
            width: 30px;
            height: 50px;
        }
        ```

    + arguments 变量：提到 arguments，想必对 JavaScript 了解的伙伴大概有所眼熟，这个在 JavaScript 中代表素有参数。而在 Less 中代表的意思是一样的，只不过用法有所不同，如果你不想单独处理每一个参数的话就可以使用 `@arguments`，如下示例：

      ``` less
      // 13arguments.less
      .transition(@moveStyle: all; @delayTime: 4s; @moveType: ease-in; @moveTime: 2s) {
          -webkit-transition: @arguments;
          -moz-transition: @arguments;
          -o-transition: @arguments;
          -ms-transition: @arguments;
          transition: @arguments;
      }
      div {
          .transition;
      }
      span {
          .transition(width);
      }
      h1 {
          .transition(width, 8s);
      }
      h3 {
          .transition(width, 8s, ease-out, 1s);
      }
      // 编译后的 css 代码
      div {
          -webkit-transition: all 4s ease-in 2s;
          -moz-transition: all 4s ease-in 2s;
          -o-transition: all 4s ease-in 2s;
          -ms-transition: all 4s ease-in 2s;
          transition: all 4s ease-in 2s;
      }
      span {
          -webkit-transition: width 4s ease-in 2s;
          -moz-transition: width 4s ease-in 2s;
          -o-transition: width 4s ease-in 2s;
          -ms-transition: width 4s ease-in 2s;
          transition: width 4s ease-in 2s;
      }
      h1 {
          -webkit-transition: width 8s ease-in 2s;
          -moz-transition: width 8s ease-in 2s;
          -o-transition: width 8s ease-in 2s;
          -ms-transition: width 8s ease-in 2s;
          transition: width 8s ease-in 2s;
      }
      h3 {
          -webkit-transition: width 8s ease-out 1s;
          -moz-transition: width 8s ease-out 1s;
          -o-transition: width 8s ease-out 1s;
          -ms-transition: width 8s ease-out 1s;
          transition: width 8s ease-out 1s;
      }
      ```

    + `!important` 关键字：在 CSS 编写的时候经常会碰到在属性值后面添加 `!important` 的时候，而再 Less 中为了能够方便，就设置了 `!important` 关键字混合方法，调用的时候再混合后面加上 `!important` 关键字表示将混合带来的所有属性标记为 `!important`。如下实例：

      ``` less
      // 14.notImportant.less
      .size(@w: 20px; @h: 50px) {
          width: @w;
          height: @h;
      }
      .box1 {
          .size;
          background-color: red;
      }
      .box2 {
          .size(40px);
          background-color: blue;
      }
      .box3 {
          .size(40px, 100px);
          background-color: green;
      }
      .box4 {
          .size !important;
          background-color: yellow;
      }
      .box5 {
          .size(40px) !important;
          background-color: pink;
      }
      .box6 {
          .size(40px, 100px) !important;
          background-color: orange;
      }
      // 编译后的 css 代码
      .box1 {
          width: 20px;
          height: 50px;
          background-color: red;
      }
      .box2 {
          width: 40px;
          height: 50px;
          background-color: blue;
      }
      .box3 {
          width: 40px !important;
          height: 100px !important;
          background-color: green;
      }
      .box4 {
          width: 20px !important;
          height: 50px !important;
          background-color: yellow;
      }
      .box5 {
          width: 40px !important;
          height: 50px !important;
          background-color: pink;
      }
      .box6 {
          width: 40px;
          height: 100px;
          background-color: orange;
      }
      ```

    + 高级参数用法：如果需要在 mixin 中不限制参数的数量，可以在变量名后添加 `...`，表示这里可以使用 N 个参数。示例如下：

      ``` less
      // 15harg.less
      // 接受 0-n 个参数
      .mixin1(...) {
          padding: @arguments;
      }
      // 接受 0-n 个参数
      .mixin2(@a: 1; ...) {
          margin: @arguments;
      }
      // 接受 1-n 个参数
      .mixin3 (@a; ...) {
          margin: @arguments;
      }
      // 接受 2-n 个参数
      .mixin4 (@a; @b; ...) {
          margin: @arguments;
      }
      .div1 {
          .mixin1(20px 30px 40px 50px);
      }
      .div2 {
          .mixin2(5, 20px 30px 40px 50px);
      }
      .div3 {
          .mixin3(10px);
      }
      .div4 {
          .mixin4(10px, 20px)
      }
      // 编译后的 css 代码
      .div1 {
          padding: 20px 30px 40px 50px;
      }
      .div2 {
          margin: 5 20px 30px 40px 50px;
      }
      .div3 {
          margin: 10px;
      }
      .div4 {
          margin: 10px 20px;
      }
      ```

    + 模式匹配与 Guard 表达式：Less 提供了通过参数值控制 mixin 行为的功能。如果要根据 `@switch` 的值控制 `.mixin` 行为，只需要按照下面的方法定义：

      ``` less
      .mixin(dark, @color) {
          color: darken(@color, 10%);
      }
      .mixin (light, @color) {
          color: lighten(@color, 10%);
      }
      .mixin(@A, @color) {
          background-color: @color;
      }
      @switch1: light;

      .box1 {
          .mixin(@switch1, #ccc);
      }
      @switch2: dark;
      .box2 {
          .mixin(@switch2, #ccc);
      }
      /*
      分析：
      传给 .mixin 的颜色执行 lighten 函数，如果 @switch 的值是 dark，那么则会执行 darken 函数输出颜色。
      darken(@color, 10%) 函数的意思是亮度降低 10%；lighten(@color, 10%) 函数的意思是亮度增加 10%。
      以下是整个过程如何发生的：
      第一个 .mixin 没有匹配，因为不满足 dark 条件；
      第二个 .mixin 可以被匹配，因为它满足了 light 条件；
      第三个 .mixin 也可以配匹配，因为他接受任何参数。
      只有满足匹配要求的混合才会被使用。混合中的变量可以匹配任何值，非变量形式的值只能与传入的值完全相等时才可以匹配成功。
      */
      // 解析后的 css 代码
      .box1 {
          color: #e6e6e6;
          background-color: #ccc;
      }
      .box2 {
          color: #b3b3b3;
          background-color: #ccc;
      }
      ```

      我们也可以根据参数的数量进行匹配，示例如下：

      ``` less
      .mixin(@a) {
          color: @a;
      }
      .mixin(@a, @b) {
          color: fade(@a, @b);
      }
      .box1 {
          .mixin(red);
      }
      .box2 {
          .mixin(blue, 10%);
      }
      /*
      调用 .mixin 时，如果使用了一个参乎上，输出第一个 .mixin，使用了两个参数，则输出第二个。
      fade(@color, 10%) 的意思是设定透明度为 10%。
      */
      // 编译后的 css 代码
      .box1 {
          color: red;
      }
      .box2 {
          color: rgba(0, 0, 255, 0.1);
      }
      ```

    + 条件混合（guarded mixins）：与上面匹配值活陪陪参数数量的情况不同，Guards 被用来匹配表达式（expressions）。如果你很熟悉变成函数的用法，那么很可能你已经掌握它的用法了。为了尽可能地符合 CSS 的语言结构，Less 选择使用 guard 混合（guarded mixins，类似于 `@media` 的工作方式）执行条件判断，而不是加入 `if-else` 声明。
        + 通过 Less 自带的函数判断

          ``` less
          // 18guardfun.less
          .mixin(@a) when(lightness(@a) >=50%) {
              background-color: red;
          }
          .mixin(@a) when(lightness(@a) < 50%) {
              background-color: blue;
          }
          .mixin(@a) {
              color: @a;
          }
          .box1 {
              .mixin(#ccc);
          }
          .box2 {
              .mixin(#777);
          }
          // 编译后的 css 代码
          .box1 {
              background-color: red;
              color: #ccc;
          }
          .box2 {
              background-color: blue;
              color: #777;
          }
          ```

        + 运算符判断：Guards 支持的运算符包括：>、>=、=、=<、<。说明一下，true 关键字是唯一判断为真的值，也就是这两个混合是相等的。示例如下：

          ``` less
          // 19guardexp.less
          @IE: true;
          @w: 10px;
          .IE(@bTrue) when(@bTrue) {
              *display: block;
          }
          .IE1(@bTrue) when(@bTrue) {
              margin: 0;
          }
          .IE2(@bTrue) when(@bTrue >=0) {
              padding: 0;
          }
          .IE3(@bTrue) when(@bTrue > 0) {
              height: 100px;
          }
          .box {
              .IE(@IE);
              .IE1(@IE);
              .IE2(@w);
              .IE3(@w);
          }
          // 编译后的 css 代码
          .box {
            *display: block;
            margin: 0;
            padding: 0;
            height: 100px;
          }
          ```

        + 多个条件：多个 Guards 可以通过逗号表示分割，如果其中任意一个结果为 true，则匹配成功。这个相当于脚本中的或运算的意思，如下实例

            ``` less
            // 20guardmulitcond.less
            @IE: true;
            @w: 10;
            .IE(@bTrue, @width) when(@bTrue), (@width < 15) {
                *display: block;
            }
            .IE1(@bTrue, @width) when(@bTrue =true), (@width > 0) {
                margin: 0;
            }
            .IE2(@bTrue, @width) when(@bTrue=false), (@width < 0) {
                padding: 0;
            }
            .IE3(@bTrue, @width) when(@bTrue=false), (@width >=0) {
                height: 100px;
            }
            .box {
                .IE(@IE, @w);
                .IE1(@IE, @w);
                .IE2(@IE, @w);
                .IE3(@IE, @w);
            }
            // 编译后的 css 代码
            .box {
                *display: block;
                margin: 0;
                height: 100px;
            }
            ```

            参数之间比较：值得注意的是不同的参数之间也可以比较，而参与比较的也可以是一个参数都没有判断，示例如下：

            ``` less
            // 21propscomp.less
            @h: 20;
            @w: 10;
            .mixin(@h, @w)when(@h < @w) {
                width: @w;
            }
            .mixin1(@h, @w)when(@h>@w) {
                height: @h;
            }
            .box {
                .mixin(@h, @w);
                .mixin1(@h, @w);
            }
            // 编译后的 css 代码
            .box {
                height: 20
            }
            ```

### Less 函数详解

### Less 经典案例
