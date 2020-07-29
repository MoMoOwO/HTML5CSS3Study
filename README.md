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

        + guard 中的 and

          ``` less
          // 22and.less
          @h: 20;
          @w: 10;
          @bTrue: true;
          .mixin(@h, @w)when(@h>@w) and (@bTrue) {
              background-color: red;
          }
          .box {
              height: 100px;
              width: 100px;
              .mixin(@h, @w);
          }
          // 编译后的 css 代码
          .box {
              height: 100px;
              width: 100px;
              background-color: red;
          }
          ```

        + guard 中的 not

          ``` less
          // 23not.less
          @num: 20;
          .mixin(@h) when not (@h>0) {
              background-color: blue;
          }
          .box {
              height: 100px;
              width: 100px;
              .mixin(@num);
          }
          // 编译后的 css 代码
          .box {
              height: 100px;
              width: 100px;
          }
          ```

    + 嵌套语法：Less 是一种动态语言，属于 CSS 预处理语言的一种。Less 和其他预处理语言一样也支持嵌套的写法。下面我们通过具体示例来了解 Less 中的嵌套书写方式。

      ``` less
      // 24nest.less
      .box {
          background-color: #ddd;
          h4 {
              color: red;
          }
          #mySpan {
              width: 100px;
              .linkA {
                  color: blue;
              }
          }
      }
      // 编译后的 css 代码
      .box {
          background-color: #ddd;
      }
      .box h4 {
            color: red;
      }
      .box #mySpan {
            width: 100px;
      }
      .box #mySpan .linkA {
            color: blue;
      }
      ```

    + `&` 的用法：`&` 符号的使用——如果你想写串联选择器，而不是写后代选择器，就可以用到 `&` 了。这点对伪类尤其有用，如 `:hover` 和 `:focus`。

      ``` less
      // 25use&.less
      .box {
          color: red;
          .myContent {
              font: bold 12px/20px "宋体";
          }
          a {
              color: #000;
              &:hover {
                  text-decoration: none;
              }
              &:focus {
                  color: #999;
              }
          }
          .myText {
              background: yellow;
              &:hover {
                  background: #777;
              }
          }
      }
      // 编译后的 css 代码
      .box {
          color: red;
      }
      .box .myContent {
          font: bold 12px/20px "宋体";
      }
      .box a {
          color: #000;
      }
      .box a:hover {
          text-decoration: none;
      }
      .box a:focus {
          color: #999;
      }
      .box .myText {
          background: yellow;
      }
      .box .myText:hover {
         background: #777;
      }
      ```

    + `&` 的高级用法：用在选择器中的 `&` 还可以反转嵌套的顺序并且可以应用到多个类名上。

      ``` less
      // 26hluse&.less
      .box1, .box2 {
          div & {
              color: black;
          }
          & + & {
              color: red;
          }
          & ~ & {
              color: yellow;
          }
      }
      // 编译后的 css 代码
      div .box1, div .box2 {
          color: black;
      }
      .box1 + .box1,
      .box1 + .box2,
      .box2 + .box1,
      .box2 + .box2 {
          color: red;
      }
      .box1 ~ .box1,
      .box1 ~ .box2,
      .box2 ~ .box1,
      .box2 ~ .box2 {
          color: yellow;
      }
      ```

    + Less 详解之命名空间：提到明明口昂见，大家有一些语言基础的一定会比较熟悉。Less 中也有命名空间的概念。所谓的命名空间，是为了更好组织 CSS 或者单纯是为了更好地封装，将一些变量或者混合模块打包起来，一些属性集之后可以重复使用。

      ``` less
      // 27namespace.less
      @h: 100px;
      .box {
          .box_button() {
              display: block;
              background-color: #ccc;
              border: 1px solid black;
              &:hover {
                  color: red;
              }
          }
          .box_box1() {
              width: 100px;
              height: @h;
              background-color: green;
          }
          .box_box2() {
              @h: 200px;
              width: 200px;
              height: @h;
              background-color: blue;
          }
      }
      .box1 {
          .box>.box_box1;
      }
      .box2 {
          .box>.box_box2;
      }
      .myButton {
          .box>.box_button;
      }
      // 编译后的 css 代码
      .box1 {
          width: 100px;
          height: 100px;
          background-color: green;
      }
      .box2 {
          width: 200px;
          height: 200px;
          background-color: blue;
      }
      .myButton {
          display: block;
          background-color: #ccc;
          border: 1px solid black;
      }
      .myButton:hover {
          color: red;
      }
      ```

### Less 函数详解

1. String 函数系列

    (1) `escape(@string)` 编码：

    + 使用 URL-encoding 的方式编码字符串。如果参数不是字符串的话，函数行为是不可预知的。目前传入颜色值的话会返回 undefined，其他的值会原样返回。
    + 不会被编码的：`, / ? @ & + ' ~ ! $`
    + 最常见的被编码的字符串：`# ^ ( ) { } | : > < ; [ ] =`
    + 参数：需要转移的字符串；返回值：字符串（string）。
    + 实例：

      ``` less
      // 01escape.less
      .box {
          content: escape('a=1');
      }
      // 编译后的 css 代码
      .box {
          content: a%3D1;
      }
      ```

    (2) `e(@string)` 转义，如“~”

    + 用于对 CSS 的转义，与 `~"value"` 类似。他接受一个字符串作为参数，并原样返回内容（不含引号）。它可用于输出一些不合法的 CSS 语法，或者是使用 Less 不能识别的属性。也接受经 `~""` 转义的值或者数字作为参数。
    + 参数：需要转移的字符串；返回值：字符串的内容，不含引号。
    + 实例：

      ``` less
      // 02e.less
      .box {
          filter: e('ms:alwaysHasItsOwnSyntax.For.Stuff()');
      }
      // 编译后的 css 代码
      .box {
          filter: ms:alwaysHasItsOwnSyntax.For.Stuff();
      }
      ```

    (3) `%` 格式化参数

    + 作用：函数 `%(string, arguments...)` 格式化一个字符串
    + 第一个参数是带占位符的字符串，所有占位符包括 - `%s`、`%S`、`%d`、`%D`、`%a`、`%A`；剩下的参数时替换占位符的表达式，如果你需要输出百分号，用双百分号 `%%` 转义，如果需要把特殊字符转义成 utf-8 转义码，需要使用大写字母占位符，该占位符会转义所有的特殊字符，除了 `( ) ' ~ !`。空格会被转译成 `%20`，小写字母占位符会保留特殊字符的原样。
    + 转义字符
      + `%d %D %a %A`：能被任何类型参数替换（颜色值、数字、转义值、表达式...），如果你在字符串中结合使用，整个字符串参数都会替换进去，包括它的引号，然后引号会被替换到字符串参数的原有位置，也许会被转义或者还是不变的，取决于占位符是大写字母还是小写字母。
      + `%s %S`：能被除了颜色值以外任何类型参数替换，如果你在字符串中结合使用，只会替换成字符串参数的值，而字符串参数引号都被忽略。
    + 实例：

      ``` less
      // 03precent.less
      .box {
          // 使用 a/d 格式化
          width: %('repetitions:%a file:%d', 1 + 2, 'directory/file.less');
          // 使用 a/d 格式化
          width: %('repetitions:%a file:%d', '1 + 2', 'directory/file.less');
          // 使用 A/D 格式化
          width: %('repetitions:%A file:%D', 1 + 2, 'directory/file.less');
          // 使用 s 格式化
          width: %('repetitions:%s file:%s', 1 + 2, 'directory/file.less');
          // 使用 s 格式化
          width: %('repetitions:%s file:%S', '1 + 2', 'directory/file.less');
          // 使用 S 格式化
          width: %('repetitions:%S file:%S', 1 + 2, 'directory/file.less');
      }

      // 编译后的 css 代码
      .box {
          width: 'repetitions:3 file:'directory/file.less'';
          width: 'repetitions:'1 + 2' file:'directory/file.less'';
          width: 'repetitions:3 file:'directory%2Ffile.less'';
          width: 'repetitions:3 file:directory/file.less';
          width: 'repetitions:1 + 2 file:directory%2Ffile.less';
          width: 'repetitions:3 file:directory%2Ffile.less';
      }
      ```

    (4) `replace(string, pattern, replacement, flags)` 替换

    + 作用：用另一个字符串替换文本
    + 参数：string - 搜索和替换用的字符串，pattern - 一个字符串或者能搜索的正则表达式，replacement - 匹配模式成功的替换字符串，flags - （可选参数）正则表达式匹配标识（全匹配还是匹配一个等..）；返回值：替换过后的字符串
    + 实例：

      ``` less
      // 04replace.less
      .box {
          width: replace('Hello, Mars?', 'Mars\?', 'World!');
          width: replace('One + One = 2', 'One', '1', 'gi');
          width: replace('This is a string.', '(string)\.$', 'new $1.');
          width: replace(~'bar-1', '1', '2');
      }

      // 编译后的 css 代码
      .box {
          width: 'Hello, World!';
          width: '1 + 1 = 2';
          width: 'This is a new string.';
          width: bar-2;
      }
      ```

2. List 函数系列

    (1) 长度（length）

    + 作用：获取集合中的值的数目。
    + 参数：list - 以逗号或空格隔开的值的计合。返回值：集合的值的个数。
    + 实例：

      ``` less
      // 1length.less
      @list1: 'A' 'B' 'C';
      @list2: 'AA', 'BB', 'CC', 'DD';
      .box {
        width: length(@list1);
        height: length(@list2);
      }
      // 编译后的 css 代码
      .box {
        width: 3;
        height: 4;
      }
      ```

    (2) 提取（extract）

    + 作用：返回集合中指定索引的值。
    + 参数：list - 逗号或者空格隔开的值集合。index - 用于返回集合中指定索引位置的整型数字。返回值：集合指定索引位置的值。
    + 实例：

      ``` less
      // 2extract.less
      @list: 123px 'B' 100px 123;
      .box {
        width: extract(@list, 1);
        height: extract(@list, 3);
        background-color: red;
      }
      // 编译后的 css 代码
      .box {
        width: 123px;
        height: 100px;
        background-color: red;
      }
      ```

3. Math 函数系列

    | 函数名            | 作用                   | 参数                                                                           | 返回值              | 实例                                                                                                          |
    | :---------------- | :--------------------- | :----------------------------------------------------------------------------- | :------------------ | :------------------------------------------------------------------------------------------------------------ |
    | `ceil()`          | 向上取整               | number - 浮点数                                                                | integer 整数        | `ceil(2.4)` 输出：3                                                                                           |
    | `floor()`         | 向下取整               | number - 浮点数                                                                | integer 整数        | `floor(2.6)` 输出：2                                                                                          |
    | `percentage()`    | 将浮点数转换为百分比   | number - 浮点数                                                                | number              | `ceil(0.5)` 输出：50%                                                                                         |
    | `round()`         | 四舍五入               | number - 浮点数，decimaPlaces - 可选参数，四舍五入取整的小数点位置，默认值为 0 | number              | `round(1.67)` 输出：2，`round(1.67, 1)`，输出：1.7                                                            |
    | `sqrt()`          | 计算数字平方根         | number                                                                         | number              | `sqrt(25cm)` 输出：5cm，`sqrt(18.6%)`，输出：4.312771730569565%                                               |
    | `abs()`           | 数字的绝对值           | number                                                                         | number              | `abs(25cm)` 输出：25cm，`abs(-18.6%)`，输出：18.6%                                                            |
    | `sin()`           | sin 函数值             | number                                                                         | number              | `sin(1)` 输出：0.8414709848078965，`sin(1deg)` 输出：0.01745240643728351，`sin(1grad)`：0.015707317311820675  |
    | `asin()`          | asin 函数值            | numbe，[-1, 1]                                                                 | number，[-π/2, π/2] | `asin(-0.8414709848078965)` 输出：-1rad，`asin(0)` 输出：0rag，`asin(2)` 输出：NaNrad                         |
    | `cos()`           | cos 函数值             | number                                                                         | number              | `cos(1)` 输出：0.5403023058681398，`cos(1deg)` 输出：0.9998476951563913，`cos(1grad)`：0.9998766324816606     |
    | `acos()`          | acos 函数值            | number，[-1, 1]                                                                | number，[0, π]      | `acos(0.5403023058681398)` 输出：1rad，`acos(1)` 输出：0rag，`acos(2)` 输出：NaNrad                           |
    | `tan()`           | tan 函数值             | number                                                                         | number              | `tan(1)` 输出：1.5574077246549023，`tan(1deg)` 输出：0.017455064928217585，`tan(1grad)`：0.015709255323664916 |
    | `atan()`          | atan 函数值            | number                                                                         | number，[-π/2, π/2] | `atan(-1.5574077246549023)` 输出：-1rad，`atan(0)` 输出：0rag，`round(atan(22), 6)` 输出：1.525373rad         |
    | `pi()`            | 返回 π 的值            | none                                                                           | number              | `pi()` 输出：3.141592653589793                                                                                |
    | `pow(num1, num2)` | 返回 num1 的 num2 次方 | number - 基数，number - 幂                                                     | number              | `pow(0cm, 0cm) pow(25, -2) pow(25, 0.5) pow(-25, 0.5) pow(-25%, -0.5)` 输出：1cm 0.0016 5 NaN NaN%            |
    | `mod(num1, num2)` | num1 对num2 取余       | number1，number2                                                               | number              | `mod(0cm, 0px) mod(11cm, 6px) mod(-26%, -5)` 输出：NaNcm 5cm -1%                                              |
    | `min()`           | 返回最小值             | value1,...,value2 一个或多个待比较的值                                         | 最小值              | `min(5, 10)` 输出：5，`min(3px, 42px, 1px, 16px)` 输出：1px                                                   |
    | `max()`           | 返回最大值             | value1,...,value2 一个或多个待比较的值                                         | 最大值              | `max(5, 10)` 输出：10，`max(3%, 42%, 1%, 16%)` 输出：42%                                                      |

4. Type 函数系列

    (1) isnumber

    + 作用：判断值或者变量值是否为数值
    + 参数：value - 发i判断的值或变量；返回值：若是数字返回 `true`，否则返回 `false`
    + 实例

      ``` less
      // 1isnumber.less
      @a: 123;
      @b: '222';
      .box {
          width1: isnumber(#ccc);
          width2: isnumber(blue);
          width3: isnumber('string');
          width4: isnumber(1234);
          width5: isnumber(56px);
          width6: isnumber(7.8%);
          width7: isnumber(keyword);
          width8: isnumber(blue);
          width9: isnumber(url(www.baa.com));
          width10: isnumber(@a);
          width11: isnumber(@b);
      }
      // 编译后的 css 代码
      .box {
          width1: false;
          width2: false;
          width3: false;
          width4: true;
          width5: true;
          width6: true;
          width7: false;
          width8: false;
          width9: false;
          width10: true;
          width11: false;
      }
      ```

    (2) isstring

    + 作用：判断值或者变量值是否为字符串
    + 参数：value - 待判断的值或变量；返回值：如果是字符串返回 `true`，否则返回 `false`
    + 实例

      ``` less
      // 2isstring.less
      @a: 123;
      @b: '222';
      .box {
          width1: isstring(#ccc);
          width2: isstring(blue);
          width3: isstring('string');
          width4: isstring(1234);
          width5: isstring(56px);
          width6: isstring(7.8%);
          width7: isstring(keyword);
          width8: isstring(blue);
          width9: isstring(url(www.baa.com));
          width10: isstring(@a);
          width11: isstring(@b);
      }

      // 编译后的 css 代码
      .box {
          width1: false;
          width2: false;
          width3: true;
          width4: false;
          width5: false;
          width6: false;
          width7: false;
          width8: false;
          width9: false;
          width10: false;
          width11: true;
      }
      ```

    (3) iscolor

    + 作用：判断值或者变量值是否为一个颜色值
    + 参数：value - 待判断得值或变量，返回值：若是颜色返回 `true` 否则返回 `false`
    + 实例

      ``` less
      // 3.iscolor.less
      @a: 123;
      @b: '222';
      .box {
          width1: iscolor(#ccc);
          width2: iscolor(blue);
          width3: iscolor('string');
          width4: iscolor(1234);
          width5: iscolor(56px);
          width6: iscolor(7.8%);
          width7: iscolor(keyword);
          width8: iscolor(blue);
          width9: iscolor(url(www.baa.com));
          width10: iscolor(@a);
          width11: iscolor(@b);
      }
      // 编译后的 css 代码
      .box {
          width1: true;
          width2: true;
          width3: false;
          width4: false;
          width5: false;
          width6: false;
          width7: false;
          width8: true;
          width9: false;
          width10: false;
          width11: false;
      }
      ```

    (4) iskeyword

    + 作用：判断值或者变量值是否为一个关键字
    + 参数：value - 带判断的值或变量，返回值：是关键字则返回 `true`，否则返回 `false`
    + 实例：

      ``` less
      // 4iskeyword.less
      @a: 123;
      @b: '222';
      .box {
          width1: iskeyword(#ccc);
          width2: iskeyword(blue);
          width3: iskeyword('string');
          width4: iskeyword(1234);
          width5: iskeyword(56px);
          width6: iskeyword(7.8%);
          width7: iskeyword(keyword);
          width8: iskeyword(blue);
          width9: iskeyword(url(www.baa.com));
          width10: iskeyword(@a);
          width11: iskeyword(@b);
      }
      // 编译后的 css 代码
      .box {
          width1: false;
          width2: false;
          width3: false;
          width4: false;
          width5: false;
          width6: false;
          width7: true;
          width8: false;
          width9: false;
          width10: false;
          width11: false;
      }
      ```

    (5) isurl

    + 作用：判断值或者变量值是否为一个 url 地址
    + 参数：value - 待判断得值或变量，返回值：若是 url 返回 `true`，否则返回 `false`
    + 实例：

      ``` less
      // 5isurl.less
      @a: 123;
      @b: '222';
      .box {
          width1: isurl(#ccc);
          width2: isurl(blue);
          width3: isurl('string');
          width4: isurl(1234);
          width5: isurl(56px);
          width6: isurl(7.8%);
          width7: isurl(keyword);
          width8: isurl(blue);
          width9: isurl(url(www.baa.com));
          width10: isurl(@a);
          width11: isurl(@b);
      }
      // 编译后的 css 代码
      .box {
          width1: false;
          width2: false;
          width3: false;
          width4: false;
          width5: false;
          width6: false;
          width7: false;
          width8: false;
          width9: true;
          width10: false;
          width11: false;
      }
      ```

    (6) ispxel

    + 作用：判断一个值或变量值是否是带像素长度单位得数字
    + 参数：value - 待判断的值或变量，返回值：若是带 `px` 单位得数字返回 `true`，否则返回 `false`
    + 实例：

      ``` less
      // 6ispixel.less
      @a: 123;
      @b: '222';
      .box {
          width1: ispixel(#ccc);
          width2: ispixel(blue);
          width3: ispixel('string');
          width4: ispixel(1234);
          width5: ispixel(56px);
          width6: ispixel(7.8%);
          width7: ispixel(keyword);
          width8: ispixel(blue);
          width9: ispixel(url(www.baa.com));
          width10: ispixel(@a);
          width11: ispixel(@b);
      }

      // 编译后的 css 代码
      .box {
          width1: false;
          width2: false;
          width3: false;
          width4: false;
          width5: true;
          width6: false;
          width7: false;
          width8: false;
          width9: false;
          width10: false;
          width11: false;
      }
      ```

    (7) isem

    + 作用：判断一个值或变量值是否是带 `em` 结尾的数字
    + 参数：value - 待判断的值或变量，返回值：若是带 `em` 结尾的数字则返回 `true`，否则返回 `false`
    + 实例：

      ``` less
      // 7isem.less
      @a: 123;
      @b: '222';
      .box {
          width1: isem(#ccc);
          width2: isem(blue);
          width3: isem('string');
          width4: isem(1234);
          width5: isem(56px);
          width6: isem(7.8%);
          width7: isem(keyword);
          width8: isem(75em);
          width9: isem(url(www.baa.com));
          width10: isem(@a);
          width11: isem(@b);
      }
      // 编译后的 css 代码
      .box {
          width1: false;
          width2: false;
          width3: false;
          width4: false;
          width5: false;
          width6: false;
          width7: false;
          width8: true;
          width9: false;
          width10: false;
          width11: false;
      }
      ```

    (8) isem

    + 作用：判断一个值或变量值是否是百分数
    + 参数：value - 待判断的值或变量，返回值：若是百分数则返回 `true`，否则返回 `false`
    + 实例：

      ``` less
      // 7ispercentage.less
      @a: 123;
      @b: '222';
      .box {
          width1: ispercentage(#ccc);
          width2: ispercentage(blue);
          width3: ispercentage('string');
          width4: ispercentage(1234);
          width5: ispercentage(56px);
          width6: ispercentage(7.8%);
          width7: ispercentage(keyword);
          width8: ispercentage(75em);
          width9: ispercentage(url(www.baa.com));
          width10: ispercentage(@a);
          width11: ispercentage(@b);
      }
      // 编译后的 css 代码
      .box {
          width1: false;
          width2: false;
          width3: false;
          width4: false;
          width5: false;
          width6: true;
          width7: false;
          width8: false;
          width9: false;
          width10: false;
          width11: false;
      }
      ```

    (9) isunit

    + 作用：判断一个值或变量值是否是带有指定单位
    + 参数：value - 待判断的值或变量，返回值：带有指定单位则返回 `true`，否则返回 `false`
    + 实例：

      ``` less
      // 7isunit.less
      @a: 123;
      @b: '222';
      .box {
          width1: isunit(35px, px);
          width2: isunit(10%, px);
          width3: isunit(10%, "%");
          width4: isunit(24em, rem);
          width5: isunit(24em, em);
          width6: isunit(123px, em);
          width7: isunit(123, em);
          width8: isunit(#ccc, pt);
      }
      // 编译后的 css 代码
      .box {
          width1: true;
          width2: false;
          width3: true;
          width4: false;
          width5: true;
          width6: false;
          width7: false;
          width8: false;
      }
      ```

5. 其他杂项函数系列

    (1) color

    + 作用：解析颜色，将代表颜色的字符串转换为颜色值。
    + 参数：string - 代表颜色值得字符串，返回值：color 值。
    + 实例：

      ``` less
      // 1color.less
      .box {
          width: 100px;
          height: 100px;
          background-color: color('red');
      }
      // 编译后的 css 代码
      .box {
          width: 100px;
          height: 100px;
          background-color: #ff0000;
      }
      ```

    (2) convert

    + 作用：将数字从一种类型转换到另一种类型。
    + 第一个参数为带单位的数值，第二个参数为单位。如果两个参数的单位是兼容的，则数字得单位被转换；如果两个参数的单位不兼容，则原样返回第一个参数。
    + 无需转换改变单位的可以参照 `unit`，兼容的单位组（可以转换的单位）：长度 - m、cm、mm、in、pt、pc，时间 - s、ms，角度 - rad、deg、grad、turn。
    + 参数：number - 带单位的浮点数，identifier、string 或 escaped value - 单位，返回值：number
    + 实例：

      ``` less
      // 2convert.less
      .box {
          width: convert(9s, 'ms');
          height: convert(7cm, 'mm');
          color: convert(8, 'deg');
      }
      // 编译后的 css 文件
      .box {
          width: 9000ms;
          height: 70mm;
          color: 8;
      }
      ```

    (3) data-uri

    + 作用：将一个资源内嵌到样式文件，如果开启 ieCompat 选项，而且资源文件的体积过大，或者是在浏览器中使用，则会使用 `url()` 进行后退。如果没有指定 MIME，则 Node.js 会使用 MIME 包来决定正确的 MIMIE。
    + 参数：mimetype - 可选参数，MIME类型字符串，url - 需要内嵌的文件得 URL。
    + 实例：

      ``` less
      // 3data-uri.less
      .box1 {
          width: 768px;
          height: 1024px;
          background-image: data-uri('../img/img.jpg');
      }
      .box2 {
          width: 768px;
          height: 1024px;
          background-image: data-uri('images/jpeg;base64', '../img/img.jpg');
      }
      // 编译后的 css 代码
      .box1 {
          width: 768px;
          height: 1024px;
          background-image: url('http://127.0.0.1:8080/3Less%E5%87%BD%E6%95%B0%E8%AF%A6%E8%A7%A3/5%E5%85%B6%E4%BB%96%E6%9D%82%E9%A1%B9%E5%87%BD%E6%95%B0%E7%B3%BB%E5%88%97/img/img.jpg');
      }
      .box2 {
          width: 768px;
          height: 1024px;
          background-image: url('http://127.0.0.1:8080/3Less%E5%87%BD%E6%95%B0%E8%AF%A6%E8%A7%A3/5%E5%85%B6%E4%BB%96%E6%9D%82%E9%A1%B9%E5%87%BD%E6%95%B0%E7%B3%BB%E5%88%97/img/img.jpg');
      }
      ```

    (4) default

    + 作用：只能边界条件中使用，没有匹配到其他自定义函数（mixin）的时候返回 `true`，否则返回 `false`.
    + 实例：

      ``` less
      // 4 default.less
      .mixin(1) {
          width: 10px;
      }
      .mixin(2) {
          height: 20px;
      }
      .mixin(@x) when (default()) {
          width: @x;
      }
      .box1 {
          .mixin(30px);
          .mixin(2);
      }
      .box2 {
          .mixin(1);
      }
      // 编译后的 css 代码
      .box1 {
          width: 30px;
          height: 20px;
      }
      .box2 {
          width: 10px;
      }
      ```

    + default 的返回值还可以和边界操作一起使用，例如 `.mixin() when not(default()){}` 将会在至少一个除自身外的自定义函数（mixin）满足条件时配调用。
    + 实例：

      ``` less
      // 4default.less
      .mixin1(@value) when (ispixel(@value)) {
          width: @value;
      }
      .mixin1(@value) when not(default()) {
          padding: @value / 5;
      }

      .box3 {
          .mixin1(100%);
      }
      .box4 {
          .mixin1(100px);
      }
      // 编译后的 css 代码
      .box4 {
          width(100px);
          padding: 20px;
      }
      ```

    + 在同一个边界条件或者不同的混合条件中，`default()` 可以被调用多次：
    + 实例：

      ``` less
      // 4default.less
      .box5 {
          .m(@x) when not (default()), (default()) {
              always: 1;
          }
          .m(@x) when not (default()) and (default()) {
              never: 1;
          }
          .m(1);
      }
      // 编译后的 css 代码
      .box5{
          always: 1;
      }
      ```

    + 然而，使用 `default()` 时如果检测到多个混合条件有潜在性冲突，Less 会抛出一个异常
    + 实例：

      ``` less
      // 4default.less
      .box6 {
          .mi(@x) when (default()) {
              a: @x;
          }
          .mi(@x) when not(default()) {
              b: @x;
          }
          .mi(1); // Error
      }
      ```

    + 更多 `default()` 高级用法：

      ``` less
      // 4default.less
      .x {
          .m(red) {
              case-1: darkred;
          }
          .m(blue) {
              case-2: darkblue;
          }
          .m(@x) when (iscolor(@x)) and (default()) {
              default-color: @x;
          }
          .m('foo') {
              case-1: I am 'foo';
          }
          .m('bar') {
              case-2: I am 'bar';
          }
          .m(@x) when (isstring(@x)) and (default()) {
              default-string: and I am the default;
          }

          &-blue {
              .m(blue);
          }
          &-green {
              .m(green);
          }
          &-foo {
              .m('foo');
          }
          &-baz {
              .m('baz');
          }
      }
      // 编译后的 css 代码
      .x-blue {
          case-2: #00008b;
      }
      .x-green {
          default-color: #008000;
      }
      .x-foo {
          case-1: I am 'foo';
      }
      .x-baz {
          default-string: and I am the default;
      }
      ```

    + `default()` 函数只能作为 Less 构建函数在边界条件中使用。如果在混合条件之外使用，`default()`函数只会被解释成普通的 CSS 属性值
    + 实例：

      ``` less
      // 4default.less
      .box7 {
          foo: default();
          bar: default(42);
      }
      // 编译后的 css 代码
      .box7 {
          foo: default();
          bar: default(42);
      }
      ```

    (5) unit

    + 作用：移除或者改变属性值的单位。
    + 参数：dimension - 数字，带或不带单位。unit - 可选参数，将要替换成的代为，如果省略则移除原单位。
    + 转换成指定单位参考 convert
    + 实例：

      ``` less
      // 5unit.less
      .box {
          width: unit(13, px);
          height: unit(25px);
      }
      // 编译后的 css 代码
      .box {
          width: 13px;
          height: 25;
      }
      ```

6. Color 函数系列

    | 函数名                                        | 作用                                                                                                                                                |
    | :-------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------- |
    | `rgb(@r, @g, @b)`                             | 转换为 RGB 颜色值                                                                                                                                   |
    | `rgba(@r, @g, @b, @a)`                        | 转换为 RGBA 颜色值                                                                                                                                  |
    | `argb(@color)`                                | 创建 #AARRGGBB 格式的颜色值                                                                                                                         |
    | `hsl(@hue, @saturation, @lightness)`          | 创建 HSL 颜色值                                                                                                                                     |
    | `hsla(@hue, @saturation, @lightness, @alpha)` | 创建 HSLA 颜色值                                                                                                                                    |
    | `hsv(@hue, @saturation, @value)`              | 创建 HSV 颜色值                                                                                                                                     |
    | `hsva(@hue, @saturation, @value, @alpha)`     | 创建 HSVA 颜色值                                                                                                                                    |
    | `hue(@color)`                                 | 从颜色值中提取 hue 值（色相）                                                                                                                       |
    | `saturation(@color)`                          | 从颜色值中提取 saturation 值（饱和度）                                                                                                              |
    | `lightness(@color)`                           | 从颜色值中提取 lightness 值（亮度）                                                                                                                 |
    | `hsvhue(@color)`                              | 从颜色中提取 hue 值，以 HSV 色彩空间表示（色相）                                                                                                    |
    | `hsvsaturation(@color)`                       | 从颜色中提取 saturation 值，以 HSV 色彩空间表示（饱和度）                                                                                           |
    | `hsvvalue(@color)`                            | 从颜色中提取 value 值，以 HSV 色彩空间表示（色调）                                                                                                  |
    | `red(@color)`                                 | 从颜色值中提取 red 值（红色）                                                                                                                       |
    | `green(@color)`                               | 从颜色值中提取 green 值（绿色）                                                                                                                     |
    | `blue(@color)`                                | 从颜色值中提取 blue 值（蓝色）                                                                                                                      |
    | `alpha(@color)`                               | 从颜色值中提取 alpha 值（透明度）                                                                                                                   |
    | `luma(@color)`                                | 从颜色值中提取 luma 值（亮度的百分比表示法）                                                                                                        |
    | `saturate(@color, 10%)`                       | 饱和度增加 10%                                                                                                                                      |
    | `desaturate(@color, 10%)`                     | 饱和度降低 10%                                                                                                                                      |
    | `lighten(@color, 10%)`                        | 亮度增加 10%                                                                                                                                        |
    | `darken(@color, 10%)`                         | 亮度降低 10%                                                                                                                                        |
    | `fadein(@color, 10%)`                         | 透明度增加 10%                                                                                                                                      |
    | `fadeout(@color, 10%)`                        | 透明度降低 10%                                                                                                                                      |
    | `fade(@color, 50%)`                           | 设定透明度为 50%                                                                                                                                    |
    | `spin(@color, 10)`                            | 色相值增加 10                                                                                                                                       |
    | `mix(@color1, @color2, [@weight: 50%])`       | 混合两种颜色                                                                                                                                        |
    | `greyscale(@color)`                           | 完全移除饱和度，输出灰色                                                                                                                            |
    | `contrast`                                    | `(@color1, [@darkcolor: black], [@lightcolor: white], [@threshold: 43%])` 如果 `@color1` 的 luma 值 > 43% 输出 `@darkcolor`，否则输出 `@lightcolor` |

7. 函数与运算

    (1) 运算提供了加、减、乘、除操作，我们可以做属性值和颜色的运算，这样就可以实现属性值之间的复杂关系。Less 中的函数映射了 JavaScript 代码，如果你愿意的话可以操作属性值。

    (2) 运算使用的实例：

      ``` less
      // opt.less
      @the-border: 1px;
      @base-color: #111;
      @red: #842210;
      #header {
          color: @base-color * 3;
          border-left: @the-border;
          border-right: @the-border * 2;
      }
      #footer {
          color: @base-color + #003300;
          border-color: desaturate(@red, 10%);
      }
      // 编译后的 css 代码
      #header {
          color: #333333;
          border-left: 1px;
          border-right: 2px;
      }
      #footer {
          color: #114411;
          border-color: #7d2717;
      }
      ```

### Less 经典案例

1. 值得参考的 10 个 Less-css 实例：

    (1) 简单的圆角半径

    + 圆角：CSS3 一个非常基本的新属性可以快速的生成圆角效果。要使用 CSS3 的圆角效果我们必须针对不同的浏览器定义各自的前缀，而如果使用了 Less 就可以用不用那么麻烦了。
    + 第一个 Less 代码是最简单的 Less 代码之一，我们需要设置圆角半径，而且我们希望使用一个变量来调整这个半径的大小。
    + 下面代码使用 mixin 技术，通过定义 `.border-radius` 并接收一个 `radius` 参数，该参数默认值是 5px，你可以在多个地方重复使用该 mixin 方法：
    + 实例代码：

      ``` less
      // 1borderradius.less
      .border-radius(@radius: 5px) {
          -webkit-border-radius: @radius;
          -moz-border-radius: @radius;
          border-radius: @radius;
      }
      .box {
          width: 100px;
          height: 30px;
          background-color: red;
          .border-radius(10px);
      }
      // 编译后的 css 代码
      .box {
          width: 100px;
          height: 30px;
          background-color: red;
          -webkit-border-radius: 10px;
          -moz-border-radius: 10px;
          border-radius: 10px;
      }
      ```

    + 效果展示：
    ![效果](https://i.loli.net/2020/06/04/NE2o5ixKrPteaz3.jpg)

    (2) 四角的半径定制

    + 如果你希望用户可以自由定制四个角的半径，那么我们需要对上面的代码做一些改进，使用 4 个变量分别代表四个边角的半径的大小。
    + 实例代码：

      ``` less
      // 2radiuscustom.less
      .border-radius-custom(@topleft: 5px, @topright: 5px, @bottomleft: 5px, @bottomright: 5px) {
          -webkit-border-radius: @topleft @topright @bottomleft @bottomright;
          -moz-border-radius: @topleft @topright @bottomleft @bottomright;
          border-radius: @topleft @topright @bottomleft @bottomright;
      }
      .box {
          width: 100px;
          height: 30px;
          background-color: red;
          .border-radius-custom(10px, 10px, 0px, 0px);
      }
      // 编译后的 css 代码
      .box {
          width: 100px;
          height: 30px;
          background-color: red;
          -webkit-border-radius: 10px 10px 0px 0px;
          -moz-border-radius: 10px 10px 0px 0px;
          border-radius: 10px 10px 0px 0px;
      }
      ```

    + 最终效果：
    ![效果](https://i.loli.net/2020/06/04/LH73K2XEvNFPMZO.jpg)

    (3) 方块阴影

    + 另一个 CSS3 常用道德属性是 `box-shadow`，该属性也有不同浏览器的前缀要求，而使用 Less 的话也可以使用 mixin 来完成。
    + 示例代码：

      ``` less
      // 3boxshoadow.less
      .box-shadow(@x: 0px, @y: 3px, @blur: 5px, @alpha: 0.5) {
          -webkit-box-shadow: @x @y @blur rgba(0, 0, 0, @alpha);
          -moz-box-shadow: @x @y @blur rgba(0, 0, 0, @alpha);
          box-shadow: @x @y @blur rgba(0, 0, 0, @alpha);
      }
      .box {
          width: 100px;
          height: 30px;
          background-color: red;
          .box-shadow(5px, 5px, 6px, 0.3);
      }
      // 编译后的 css 代码
      .box {
          width: 100px;
          height: 30px;
          background-color: red;
          -webkit-box-shadow: 5px 5px 6px rgba(0, 0, 0, 0.3);
          -moz-box-shadow: 5px 5px 6px rgba(0, 0, 0, 0.3);
          box-shadow: 5px 5px 6px rgba(0, 0, 0, 0.3);
      }
      ```

    + 最终效果：
    ![效果](https://i.loli.net/2020/06/04/CjbIzOsqSY2QhZ1.jpg)

    (4) 元素过渡效果

    + CSS3 的过度使用起来更加麻烦，你必须最大化的支持各种浏览器，因此你需要定义 5 个前缀，而通过 Less 的 mixin 更加方便。
    + 示例代码：

      ``` less
      // 4transition.less
      .transition(@prop: all, @time: 1s, @ease: linear) {
          -webkit-transition: @prop @time @ease;
          -moz-transition: @prop @time @ease;
          -o-transition: @prop @time @ease;
          -ms-transition: @prop @time @ease;
          transition: @prop @time @ease;
      }

      .box {
          background-image: url('../img/img.jpg');
          height: 1024px;
          width: 768px;
          .transition(all, 0.5s, ease-in);
      }
      .box:hover {
          opacity: 0.5;
      }
      // 编译后的 css 代码
      .box {
          background-image: url('http://127.0.0.1:8080/4Less%E7%BB%8F%E5%85%B8%E6%A1%88%E4%BE%8B/10%E4%B8%AA%E5%80%BC%E5%BE%97%E5%8F%82%E8%80%83%E7%9A%84Less-css%E6%A1%88%E4%BE%8B/img/img.jpg');
          height: 1024px;
          width: 768px;
          -webkit-transition: all 0.5s ease-in;
          -moz-transition: all 0.5s ease-in;
          -o-transition: all 0.5s ease-in;
          -ms-transition: all 0.5s ease-in;
          transition: all 0.5s ease-in;
      }
      .box:hover {
          opacity: 0.5;
      }
      ```

    + 最终效果：
    ![效果](https://s1.ax1x.com/2020/06/05/tssJld.gif)

    (5) 转换/旋转

    + 同样使用 Less 中的 mixin 也可以很容易实现 CSS3 中元素的角度旋转、缩放和倾斜等效果。
    + 实例代码：

      ``` less
      // 5transform.less
      .transform(@rotate: 90deg, @scale: 1, @skew: 1deg, @translate: 10px) {
          -webkit-transform: rotate(@rotate) scale(@scale) skew(@skew)
            translate(@translate);
          -moz-transform: rotate(@rotate) scale(@scale) skew(@skew)
            translate(@translate);
          -o-transform: rotate(@rotate) scale(@scale) skew(@skew) translate(@translate);
          -ms-transform: rotate(@rotate) scale(@scale) skew(@skew) translate(@translate);
          transform: rotate(@rotate) scale(@scale) skew(@skew) translate(@translate);
      }
      .box {
          background-image: url('../img/img.jpg');
          height: 1024px;
          width: 768px;
          .transform(5deg, 0.5, 1deg, 0px);
      }
      // 编译后的 css 代码
      .box {
          background-image: url('http://127.0.0.1:8080/4Less%E7%BB%8F%E5%85%B8%E6%A1%88%E4%BE%8B/10%E4%B8%AA%E5%80%BC%E5%BE%97%E5%8F%82%E8%80%83%E7%9A%84Less-css%E6%A1%88%E4%BE%8B/img/img.jpg');
          height: 1024px;
          width: 768px;
          -webkit-transform: rotate(5deg) scale(0.5) skew(1deg) translate(0px);
          -moz-transform: rotate(5deg) scale(0.5) skew(1deg) translate(0px);
          -o-transform: rotate(5deg) scale(0.5) skew(1deg) translate(0px);
          -ms-transform: rotate(5deg) scale(0.5) skew(1deg) translate(0px);
          transform: rotate(5deg) scale(0.5) skew(1deg) translate(0px);
      }
      ```

    + 最终效果
    ![效果](https://i.loli.net/2020/06/05/CJEmd2UDMfVLzkI.jpg)

    (6) 线性渐变

    + 渐变是 CSS3 最复杂的属性之一，有上百万不同的设置组合，但我们常用的无非几种。我们还是从最简单的开始，实现两个不同的颜色之间的渐变，你可以定义开始颜色和最终颜色，这里我们使用最新的渐变语法。
    + 实例代码：

      ``` less
      // 5linergradient.less
      .liner-gradient(@origin:to left, @start: #ffffff, @stop: #000000) {
          background-color: @start;
          background-image: -webkit-linear-gradient(@origin, @start, @stop);
          background-image: -moz-linear-gradient(@origin, @start, @stop);
          background-image: -o-linear-gradient(@origin, @start, @stop);
          background-image: -ms-liner-gradient(@origin, @start, @stop);
          background-image: linear-gradient(@origin, @start, @stop);
      }
      .box {
          height: 30px;
          width: 100px;
          .liner-gradient(to right, #663333, #333333);
      }
      // 编译后的 css 代码
      .box {
          height: 30px;
          width: 100px;
          background-color: #663333;
          background-image: -webkit-linear-gradient(to right, #663333, #333333);
          background-image: -moz-linear-gradient(to right, #663333, #333333);
          background-image: -o-linear-gradient(to right, #663333, #333333);
          background-image: -ms-liner-gradient(to right, #663333, #333333);
          background-image: linear-gradient(to right, #663333, #333333);
      }
      ```

    + 最终效果：
    ![效果](https://i.loli.net/2020/06/05/PnodAEteSXWrug5.jpg)

    (7) 快速渐变

    + 创建渐变最讨厌的事情之一就是找出你的颜色。有时你只是想快速在现有颜色上做一些渐变效果。这里我们使用从透明开始到全黑的渐变效果，你需要设置的就是最初颜色以及透明度 `alpha` 值。
    + 示例代码：

      ``` less
      // 7quickgradient.less
      .quick-gradient(@origin:to left, @alpha: 0.2) {
          background-image: -webkit-linear-gradient(
            @origin,
            rgba(0, 0, 0, 0),
            rgba(0, 0, 0, @alpha)
          );
          background-image: -moz-linear-gradient(
            @origin,
            rgba(0, 0, 0, 0),
            rgba(0, 0, 0, @alpha)
          );
          background-image: -o-linear-gradient(
            @origin,
            rgba(0, 0, 0, 0),
            rgba(0, 0, 0, @alpha)
          );
          background-image: -ms-liner-gradient(
            @origin,
            rgba(0, 0, 0, 0),
            rgba(0, 0, 0, @alpha)
          );
          background-image: linear-gradient(
            @origin,
            rgba(0, 0, 0, 0),
            rgba(0, 0, 0, @alpha)
          );
      }
      .box {
          height: 30px;
          width: 100px;
          background-color: red;
          .quick-gradient(to top, 0.2);
      }
      // 编译后的 css 代码
      .box {
          height: 30px;
          width: 100px;
          background-color: red;
          background-image: -webkit-linear-gradient(to top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.2));
          background-image: -moz-linear-gradient(to top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.2));
          background-image: -o-linear-gradient(to top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.2));
          background-image: -ms-liner-gradient(to top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.2));
          background-image: linear-gradient(to top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.2));
      }
      ```

    + 最终效果：
    ![效果](https://i.loli.net/2020/06/05/oPDxjfTwql8IVeu.jpg)

    (8) 镜像效果

    + CSS3 中的镜像效果都是不骗支持的，你需要做的就是设置长度和不透明度这两个参数，通过 Less 的 mixin 更容易实现。
    + 实例代码：

      ``` less
      // 8reflection.less
      .reflection(@length: 50%, @opactiy: 0.2) {
          -webkit-box-reflect: below 0px -webkit-gradient(linear, left top, left bottom, from(transparent), color-stop(@length, transparent), to(rgba(255, 255, 255, @opactiy)));
          -moz-box-reflect: below 0px -moz-gradient(linear, left top, left bottom, from(transparent), color-stop(@length, transparent), to(rgba(255, 255, 255, @opactiy)));
          box-reflect: below 0px
            gradient(
              liner,
              left top,
              left bottom,
              from(transparent),
              color-stop(@length, transparent),
              to(rgba(255, 255, 255, @opactiy))
            );
      }
      .box {
          height: 200px;
          width: 200px;
          background-image: url('../img/pink.jpg');
          .reflection(20%, 0.2);
      }
      // 编译后的 css 代码
      .box {
          height: 200px;
          width: 200px;
          background-image: url('http://127.0.0.1:8080/4Less%E7%BB%8F%E5%85%B8%E6%A1%88%E4%BE%8B/10%E4%B8%AA%E5%80%BC%E5%BE%97%E5%8F%82%E8%80%83%E7%9A%84Less-css%E6%A1%88%E4%BE%8B/img/pink.jpg');
          -webkit-box-reflect: below 0px -webkit-gradient(linear, left top, left bottom, from(transparent), color-stop(20%, transparent), to(rgba(255, 255, 255, 0.2)));
          -moz-box-reflect: below 0px -moz-gradient(linear, left top, left bottom, from(transparent), color-stop(20%, transparent), to(rgba(255, 255, 255, 0.2)));
          box-reflect: below 0px gradient(liner, left top, left bottom, from(transparent), color-stop(20%, transparent), to(rgba(255, 255, 255, 0.2)));
      }
      ```

    + 最终效果：
    ![效果](https://i.loli.net/2020/06/06/JBrXPqzgeVbWm1Q.jpg)

    (9) 互补色方案

    + 互补色方案（Complementary Color Scheme）：Less 和 Sass 最独特的功能就是颜色计算函数，你可以轻松使用 Less 来创建各种调色板，下面是两个简单的例子。
    + 这里我们使用一个基本色，然后通过彩色旋转以及加亮和变暗方法扩展到 5 个不同色板。为了生成互补色，我们使用 `spin` 将颜色旋转 180 度。
    + 实例代码：

      ``` less
      // 9colorscheme.less
      @base: #663333;
      @complement1: spin(@base, 180);
      @complement2: darken(spin(@base, 180), 5%);
      @lighten1: lighten(@base, 15%);
      @lighten2: lighten(@base, 30%);
      .one {
          background-color: @base;
          width: 100px;
          height: 30px;
      }
      .two {
          background-color: @complement1;
          width: 100px;
          height: 30px;
      }
      .three {
          background-color: @complement2;
          width: 100px;
          height: 30px;
      }
      .four {
          background-color: @lighten1;
          width: 100px;
          height: 30px;
      }
      .five {
          background-color: @lighten2;
          width: 100px;
          height: 30px;
      }
      // 编译后的 css 代码
      .one {
          background-color: #663333;
          width: 100px;
          height: 30px;
      }
      .two {
          background-color: #336666;
          width: 100px;
          height: 30px;
      }
      .three {
          background-color: #2b5555;
          width: 100px;
          height: 30px;
      }
      .four {
          background-color: #994d4d;
          width: 100px;
          height: 30px;
      }
      .five {
          background-color: #bb7777;
          width: 100px;
          height: 30px;
      }
      ```

    + 最终效果：
    ![效果](https://i.loli.net/2020/06/06/E2H9QTm3oWAjVIu.jpg)

    (10) 颜色微调

    + 颜色微调（Subtle Color Scheme）：互补色很有用，但在网页设计中另外更有用的是颜色微调。
    + 示例代码：

      ``` less
      // 10subtlecolorscheme.less
      @base: #663333;
      @lighter1: lighten(spin(@base, 5), 10%);
      @lighter2: lighten(spin(@base, 10), 20%);
      @darker1: darken(spin(@base, -5), 10%);
      @darker2: darken(spin(@base, -5), 20%);
      .one {
          background-color: @base;
          width: 100px;
          height: 30px;
      }
      .two {
          background-color: @lighter1;
          width: 100px;
          height: 30px;
      }
      .three {
          background-color: @lighter2;
          width: 100px;
          height: 30px;
      }
      .four {
          background-color: @darker1;
          width: 100px;
          height: 30px;
      }
      .five {
          background-color: @darker2;
          width: 100px;
          height: 30px;
      }
      // 编译后的 css 代码
      .one {
          background-color: #663333;
          width: 100px;
          height: 30px;
      }
      .two {
          background-color: #884a44;
          width: 100px;
          height: 30px;
      }
      .three {
          background-color: #aa6355;
          width: 100px;
          height: 30px;
      }
      .four {
          background-color: #442225;
          width: 100px;
          height: 30px;
      }
      .five {
          background-color: #221112;
          width: 100px;
          height: 30px;
      }
      ```

    + 最终效果：
    ![效果](https://i.loli.net/2020/06/06/2EgOiuDevIZklQr.jpg)

2. Less 综合案例

    (1) 任务：要求页面实现最终如下 CSS 代码：

    ``` css
    .PtzControl-1-out {
        background-position: 0 0px;
    }
    .PtzControl-1-over {
        background-position: 0 -80px;
    }
    .PtzControl-2-out {
        background-position: 0 -160px;
    }
    .PtzControl-2-over {
        background-position: 0 -240px;
    }
    .PtzControl-3-out {
        background-position: 0 -320px;
    }
    .PtzControl-3-over {
        background-position: 0 -400px;
    }
    .PtzControl-4-out {
        background-position: 0 -480px;
    }
    .PtzControl-4-over {
        background-position: 0 -560px;
    }
    .PtzControl-5-out {
        background-position: 0 -640px;
    }
    .PtzControl-5-over {
        background-position: 0 -720px;
    }
    .PtzControl-6-out {
        background-position: 0 -800px;
    }
    .PtzControl-6-over {
        background-position: 0 -880px;
    }
    .PtzControl-7-out {
        background-position: 0 -960px;
    }
    .PtzControl-7-over {
        background-position: 0 -1040px;
    }
    .PtzControl-8-out {
        background-position: 0 -1120px;
    }
    .PtzControl-8-over {
        background-position: 0 -1200px;
    }
    .PtzControl-9-out {
        background-position: 0 -1280px;
    }
    .PtzControl-9-over {
        background-position: 0 -1360px;
    }
    ```

    (2) 分析：

    + 属性名，奇数行为 `PtzControl-*-out`，偶数行为 `PtzControl-*-over`
    + 共 18 行，迭代 9 次
    + 属性值：`background-position: A B` ，A 一直为 0，B 以 80 递减。

    (3) 实现：

    ``` less
    @cons: -80px;
    .myLoop(@counter, @i: 0) when(@i < @counter){
        @c: @i + 1;
        .PtzControl-@{c}-out{
            background-position: 0 @cons * (@i * 2);
        }
        .PtzControl-@{c}-over {
            background-position: 0 @cons * (@i * 2 + 1);
        }
        .myLoop(@counter, @i + 1);
    }
    .myLoop(9);
    ```

    (4) 小结：案例重点主要有以下两点：循环如何表达；字符串的一部分是标量时，如何组装字符串。

### 剖析 BootStrap 的 Less 架构

1. CSS 之殇之 Less 解决方案

    (1) 变量：如何管理网站的主题颜色和主题容器的高度和宽度切实让人有点头疼，大家一定有不断的做 ctrl+c 和 ctrl+v 的操作来反复替换这些常量吧，但是一旦我们用了 Less 来管理这些变量，就能达到牵一发而动全身的效果，管理起来非常方便。

    (2) 混合：还记得之前的 `border-radius` 需要声明冗余的类似 `-moz-border-radius` 和 `-webkit-border-radius` 等属性吧，但是如果我们使用 Less 的混合的特性来管理 `border-radius` 属性来达到重用的效果，那么，代码看起来就会非常简洁了。

    (3) 函数：针对一些复杂的操作，比如栅格布局，数学的加减乘除计算，颜色的变化等等，我们可以用函数来进行操作。

2. BootStrap 之 Less 架构：BootStrap 对 Less 进行了二次封装，提供了很多基础的 Less 变量和函数，下面就来具体看下：

    (1) BootStrap 变量

    (2) BootStrap 混合

    + 基础的混合：混合就是将一段需要进行合并的样式通过 Less 的一种声明方式写在一起，它可以方便的呗其他样式调用从而达到能够重用的目的。
    + 带参数的混合：这种混合和基础混合比较类似，他增加接收参数的功能，当然如果你不传任何参数，它会提供一个默认值。
    + 易于扩展：所有的混合都存储在 mixins.less中的，如果各位有什么需要增加的混合可以直接集成到 utilities.less 中，方便调用。

### 利用 Koala 编译 Less

1. 什么是 Koala？Koala 是一款桌面程序，支持 Less、Sass、Coffeescript 即使编译，帮助 web 开发者更高效的使用 less、sass、coffeescript 开发。[官网](http://koala-app.com/)

2. 为什么要使用 Koala？越来越多的同学开始使用 Less 等预处理器的方式来编写 CSS 跟 JavaScript，比较流行的有 Less、Sass、Coffeescript。Less 等待吗无法直接在浏览器中执行，最终还是需要编译成 CSS 或 JS。他们的语法很棒，但是他们的编译方式却不够灵活。官方基本上都是只提供命令行的方式进行文件编译，Less 还可以在页面中嵌入一个 less.ja 进行在线编译，但这种方法实在是不靠谱。所以大家都喜欢使用图形界面工具来进行编译工作，高效快捷。在 Koala 开发之前已经有一些工具了，比如 winLess、simpleless 等，功能都比较单一，且只支持 Less。还有一些同学折腾编辑器 sublime text 等，但目前还没有一个很完美的方案。还好现在有了 Koala。

3. Koala 特性

    (1) 多语言支持：支持 Less、Sass、Coffeescript 和 compass framework。

    (2) 事实编译：监听文件，当文件改变时自动执行编译，这一切都在后台运行，无需人工操作。

    (3) 编译选项：支持自定义编译选项。

    (4) 代码压缩：Less

4. 使用方法

    (1) 基本功能介绍

    + 安装完成后打开 Koala，吧文件夹拖入界面或者在左侧加好处选择文件夹，此时在界面左边有文件夹路径产生。
    ![启动](https://i.loli.net/2020/06/12/5piu3aKAnzJeQvl.jpg)
    + 同时有 Less 文件将显示再界面中间，右键文件选择输出 CSS 文件的路径。
    ![打开](https://i.loli.net/2020/06/12/VgQu3HhbDneiJEU.jpg)
    + 左键点击 Less 文件再右侧则有功能选项栏弹出，下面将介绍功能。
    ![左键](https://i.loli.net/2020/06/12/CzPANLvmilOpjI1.jpg)

    (2) 自动编译（实时编译）：当启动自动编译时，使用编辑器按下 Ctrl+S保存时，CSS 文档会自动更新。如果没有打开这个功能，那么需要使用者再自行点击“执行编译”才更新 CSS 文档。当左键单击一个 Less 文档时则右侧会弹出配置选项。
    ![自动编译](https://i.loli.net/2020/06/12/RDjpeuLaN4kl2qI.jpg)

    (3) 编译选项

    + 行注释（line comments）：这个功能会在 css 文件里对应的 Less 编译出来的 CSS 带马上发提供一个注释。注释的额呢绒分别来说明来自 Less 的第几行开始，同时标明来自那个 Less 文件。

      ``` less
      // color.less
      @color: #4d926f;
      .box {
        color: @color;
      }
      // 编译后的 css 代码
      /* line 2, F:\HTML5+CSS3Study\08CSS进阶-Less\4Less经典案例\Less-css综合案例\less\color.less */
      .box {
        color: #4d926f;
      }
      ```

    + 输出方式（代码压缩）：正常（normal）：顾名思义，就是不压缩；压缩（compress）：顾名思义就是压缩。

      ``` less
      // out.less
      @size: 100px;
      .box1 {
        height: @size;
        width: @size;
      }
      .box2 {
        height: @size;
        width: @size;
      }
      // normal 编译后的 css 文件
      .box1 {
        height: 100px;
        width: 100px;
      }
      .box2 {
        height: 100px;
        width: 100px;
      }
      // compress 编译后的 css 文件
      .box1{height:100px;width:100px}.box2{height:100px;width:100px}
      ```

## Sass 全面解析

### Sass 入门

1. 简介：

   (1) 作为前端开发人员，你肯定对 CSS 很熟悉，但是你知道 CSS 可以自定义吗？大家都知道 js 中可以自定义变量，CSS 仅仅是一个标记语言，不是编程语言，因此不可以自定义变量，不可以引用等等。面对这些问题，我们现在来引进 Sass，简单地说，它是 CSS 的升级版，它可以自定义变量，可以有 if 语句，还可以嵌套等等。

   (2) Sass 的英文全称是 Syntactically Awesome Stylesheets，最早由 Hampton Catlin 开发和设计。一种帮助你简化 CSS工作流程的方式，帮助你更容易的维护和开发 CSS 内容。

   (3) [官网](https://www.sass.hk/)

2. 安装：

    (1) Sass 是 Ruby 语言写的，但是两者的语法没有关系。不懂 Ruby照样使用。只是必须先安装 Ruby，然后再安装 Sass。

    (2) Windows 下安装 Ruby

    + 去 [Ruby 官网](https://rubyinstaller.org/downloads/)下载 Ruby with DevKit 的安装包，直接选择下载最新版本。
    + 运行安装包。
    + 安装完成后，打开命令行，运行命令 `ruby -v`，检查是否安装成功。

    (3) 安装 Sass

    + 打开终端或命令提示符。
    + 运行命令 `gem install sass`，Ruby 使用 Gems 来管理他的各种包的代码。
    + 安装 sass 命令可能会报错，原因是因为 GFW 的原因或者说网络服务器不稳定，解决方法是使用淘宝镜像。
    + 验证 Sass 是否成功安装，运行命令 `sass -v`

3. 快速上手

    (1) 新建 input.scss 文件，内容如下

    ``` Scss
    $blue: blue; // color
    .blueBox{
        background-color: $blue;
    }
    ```

    (2) 命令行或终端输入如下命令进行编译：`sass input.scss output.css`，得到编译后的 css 文件。

    (3) 创建 html 文档，引入编译得到的 css 文件测试。

4. 使用 Sass

    (1) Sass 有三种使用方式：命令行工具、独立的 Ruby 模块，以及包含 Ruby on Rails 和 Merb 作为支持 Rack 的框架的插件，所有这些方式的第一步都是安装 Sass：`gem install sass`

    (2) 如果你使用的是 Windows，就需要先安装 Ruby。

    (3) 如果要在命令行中运行 Sass，只需要输入 `sass input.scss output.css`

    (4) 你还可以命令 Sass 监视文件的改动并更新 CSS：`sass --watch input.scss:output.css`，注：Ctrl + C 可以终止监视。

    (5) 如果你得目录里面有很多 Sass 文件，你还可以使用 Sass 监视整个目录：`sass --watch inpu.scss:output.css`

    (6) 如果你想一次性编译一个文件夹里所有 `.scss` 文件到另一个目录中，相关命令为： `sass --update input_path:output_path`

    (7) 命令 `sass --help` 查看帮助文档

### Sass 语法

1. Sass 文件后缀名：Sass 有两种后缀名文件：一种后缀名为 .sass，即不适用大括号和分号的 sass 文件；另一种就是我们刚刚使用过的 .scss 文件，这种和我们平时写的 css 文件格式差不多，使用大括号和分号。接下来的 Sass 学习，使用 .scss 结尾的文件。也建议使用 .scss 结尾的文件，以避免 sass 后缀名的严格格式要求报错。

2. 使用变量

   (1) Sass 让人们受益的一个重要特性就是它为 css 引入了变量。你可以把反复使用的 css 属性值定义成变量，然后通过变量名来引用他们，而无需重复书写这一属性值。或者，对于仅使用过一次的属性值，你可以赋予其一个易懂的变量名，让人一眼就知道这个属性值的用途。

   (2) Sass 使用 `$` 符号来标识变量（老版本的 Sass 使用 `!` 来表示变量。改成 `$` 多半原因因为 `!highlight-color` 看起来太丑了）。比如 `$highlinht-color` 和 `$sidebar-width`。为什么选择 `$` 符号呢？因为它区别度高更具美感，且在 CSS 中并无他用，不会导致与现存或未来的 css 语法冲突。

    (3) 变量的声明

    + Sass 变量的声明和 CSS 属性的声明很像：`$highlight-color: #F90;`
    + 这意味着变量 `$highlight-color` 现在的值是 `#F90`。任何可以用作 CSS 属性值的赋值都可以用作 Sass 的变量值，甚至是以逗号分隔的多个属性值，如 `$basic-border: 1px solid black;`，或以逗号分割的多个属性值，如 `$plain-font: "Myriad Pro", Myriad, "Helvetica Neue", Helvetica, "Liberation Sans", Arial, "sans-serif", "sans-serif";`。这是变量还没有生效，除非你引用这个变量，我们很快就会了解如何引用变量了。
    + 与 CSS 属性不同，变量可以在 CSS 规则快定义之外存在。当变量定义在 CSS 规则快内，那么该变量只能在此规则块内使用。如果它们出现在任何形式的 `{...}` 块中（如 `@media` 或者 `@font-face` 块），情况也是如此；在下面这段代码中， `$nav-color` 这个变量定义在了规则快外边，所以在这个样式表中都可以像 `nav` 规则那样引用它。`$width` 这个变量定义在了 nav 的 `{}` 规则快内，所以它只能在 `nav` 规则块内使用。这一位置是你可以在样式表的其他地方定义和使用 `$width` 变量，不会对这里造成影响。

      ``` scss
      $nav-color: #F90;
      nav {
          $width: 100px;
          width: $width;
          color: $nav-color;
      }
      // 编译后
      nav {
          width: 100px;
          color: #F90;
      }
      ```

    (4) 变量引用：

    + 凡是 CSS 属性的标准值（比如说 `1px` 或者 `bold`）可存在的地方，变量就可以使用。CSS 生成时，变量会被他们的值所替代。之后，如果你需要一个不同的值，只需要改变这个变量的值，则所有引用此变量的地方生成的值都会随之改变。如下面的实例中的 `$hightligh-color` 变量，它被直接赋值给 `border` 属性，放这段代码被编译输出 CSS 时，`$highlight-color` 会被 `#F90` 这一颜色值所替代。产生的效果就是给 `.selected` 这个类一条 1 像素宽、实心且颜色值为 #F90 的边框。

      ``` scss
      $highlight-color: #F90;
      .selected {
          border: 1px solid $highlight-color;
      }
      // 编译后
      .selected {
          border: 1px solid #F90;
      }
      ```

    + 在声明变量时，变量值也可以引用其他变量。当你通过粒度区分，为不同的值取不同名字时，这相当有用。下例在独立的颜色值粒度上定义了一个变量，且在另一个更复杂的边框之力度上也定义了一个变量。看上去示例中的 `$highligh-color` 变量，他被直接赋值给 border 属性，当这段代码被编译输出 CSS 时，`$hightligh-color` 会被 #F90 这个以颜色值所代替。产生的效果就是给 `.selsected` 这个类设置一条 1 像素宽，实心且颜色值为 #F90 的边框。这里，`$highlight-border` 变量的生命中使用了 `$highlight-color` 这个变量。产生的效果就跟你直接为 `border` 属性设置一个 `1px solid #F90;` 的值的效果是一样的。

      ``` scss
      $hightlight-color: #F90;
      $highlight-border: 1px solid $highlight-color;
      .selected{
        border: $highlight-border;
      }
      // 编译后
      .selected {
        border: 1px solid #F90;
      }
      ```

    (5) 变量名

    + Sass 的变量名可以与 CSS 中的属性名和选择其名称相同，包括中划线和下划线。这完全取决于个人的喜好，有些人喜欢使用中华先来分割变量中的多个词（如 `$highlight-color`），而有些人喜欢是用下划线（如 `$highlight_color`）。使用中划线的方式更为普遍，这也是 `compass` 和中文都用的方式。
    + 不过 Sass 并不像强迫任何人一定使用中划线或下划线，所以这两种用法相互兼容。用中划线声明的变量可以使用下划线的方式医用，反之亦然。这意味着即使 `compass` 选择用中划线的命名方式，这并不影响你在使用 `compass` 的样式中用下划线的命名方式进行引。在下面这个例子中，`$link-color` 和 `$link_color` 起始指向的是同一个变量。实际上，在 Sass 的大多数地方，中划线命名的内容和下划线命名的内容是互通的，除了变量，也包括对混合器和 Sass 函数的命名。但是在 Sass 中纯 CSS 部分不互通，比如类名、ID 或 属性名。

      ``` scss
      $link-color: blue;
      a {
        color: $lick_color;
      }
      // 编译后
      a {
        color: blue;
      }
      ```

    + 尽管变量自身提供了很多有用的地方，但是 Sass 基于变量提供的跟更为强大的工具才是我们关注的焦点。只有当变量与 Sass 的其他特性一起使用时，才能发挥其全部潜能。

3. 嵌套 CSS 规则

    (1) CSS 中重复写选择器是非常恼人的。如果要写一大串指向页面中同一块的样式时，往往需要一遍又一遍地写同一个 ID，如下代码所示。

    ``` css
    #content article h1 { color: #333; }
    #content article p { margion-bottom: 1.4em; }
    #contne aside { background-color: #EEE; }
    ```

    像这种情况 Sass 可以让你只写一遍，且使样式可读性更高。在 Sass 中，你可以向套娃那样在规则块中嵌套规则块。Sass 在输出	CSS 时会帮你把这些嵌套规则处理好，避免你的重复书写。

    ``` scss
    // 1nested_intro.scss
    #content{
      article{
        h1 { color: #333; }
        p { margin-bottom: 1.4em; }
      }
      aside {
        background-color: #EEE;
      }
    }
    // 编译后的 CSS 代码
    #content article h1 { color: #333; }
    #content article p { margion-bottom: 1.4em; }
    #contne aside { background-color: #EEE; }
    ```

    多数情况下这种简单的嵌套都没问题，但是有些场景下不行，比如你想要在嵌套的选择器里面立刻应用一个类似于 `:hover` 的伪类。为了解这种以及其他情况，Sass 提供了一个特殊结构 `&`。

    (2) 父选择器的标识符，连体符号 `&`

    + 一般情况下，Sass 在解开一个嵌套规则时就会把父选择器（`#content`）通过一个空格连接到子选择器（`article` 和 `aside`）的前边 形成（`#content article` 和 `#content aside`）这种在 CSS 里面被称为后台选择器，因为他选择 ID 为 `content` 的元素内所有命中标签选择器 `article` 和 `aside` 的元素。但在有些情况下你却不会希望 Sass 使用这种后台选择器的方式生成这种连接。
    + 最常见的一种情况是当你为链接之类的元素写 `:hover` 这种伪类时，你并不希望一后代选择器的方式连接。比如说，下面这种情况 Sass 就无法正常工作：

      ``` scss
      // 不能正常达到目的
      article a {
        color: blue;
        :hover {
          color: red;
        }
      }
      // 编译后
      article a {
        color: blue;
      }
      article a :hover {
        color: red;
      }
      ```

    + 在上面这段代码中 `color: red` 这条规则将会被应用到选择器 `article a :hover`，`article` 元素内连接的所有子元素在被 `hover` 时都会变成红色，这是不正确的。你想把这条规则应用到超链接滋生，而后代选择器的方式无法帮你实现。 解决之道为使用一个特殊的 Sass 选择器，即父选择器。在使用嵌套规则时，父选择器对于嵌套规则如何解开提供更好的控制。他就是一个简单的 `&` 符号，且可以放在任何一个选择器可出现的地方。

      ``` scss
      // 2conjoin_label.scss
      article a {
        color: blue;
        &:hover {
          color: red;
        }
      }
      // 编译后
      article a {
        color: blue;
      }
      article a:hover {
        color: red;
      }
      ```

    + 在为父选择器添加 `:hover` 等伪类时，这种方式非常有用。同时父选择器标识符还有另一种用法，你可以在父选择器之前添加选择器。举例来说，当用户在使用 IE 浏览器时，你会通过 JavaScript 在 `<body>` 标题前上添加一个 `ie` 的类名，为这种情况编写特殊的样式，如下：

      ``` scss
      #content aside{
        color: red;
        body.ie & { color: green; }
      }
      // 编译后
      #content aside { color: red; }
      body.ie #content aside { color: green; }
      ```

      Sass 在选择器嵌套上非常的智能，即使带有父选择器的情况。当 Sass 遇到群组选择器（由多个逗号分割开的选择器形成）也能完美地处理这种嵌套。

    (3) 群组选择器的嵌套

    + 在 CSS 里面，选择器 `h1,h2,h3` 会同时命中 `<h1></h1>`、`<h2></h2>` 和 `<h3></h3>` 元素。与此类似 `.button button` 会命中 `<button></button>` 和类名为 `.button` 的元素。这种选择器成为群组选择。群组选择器的规则会对命中群组中任何一个选择器的元素生效。

      ``` css
      .butto,button {
        margin: 0;
      }
      ```

    + 当看到上面这段代码时，你可能还没意识到会有重复性的工作。但是会很快发现，如果你需要在一个特定的容器元素内对这样一个群组选择器进行修饰时，情况就不同了。CSS 的写法会让你在群组选择器中的每一个选择器前面都重复一边容器元素的选择器，如下：

      ``` css
      .container h1, .container h2, .container h3{
        margin-bottom: .8em;
      }
      ```

    + 非常幸运，Sass 的嵌套特征在这种场景下也非常有用。当 Sass 解开一个群组选择器规则内嵌的规则时，它会把每一个内嵌选择器的规则都正确的解释出来：

      ``` scss
      // 4group.scss
      .container {
        .h1, .h2, .h3{
          margin-bottom: .8em;
        }
      }
      // 编译后 css 代码
      .container h1, .container h2, .container h3{
        margin-bottom: .8em;
      }
      ```

    + 首先 Sass 将 `.container` 和 `h1`、`.container` 和 `h2`、`.container` 和 `h3` 组合，然后将三者重新组合成一个群组选择器，生成你前面看到的普通 css 样式。对于内嵌在群组选择器内的嵌套规则，处理方式也一样，如：

      ``` scss
      nav, aside{
        a { color: blue; }
      }
      // 编译后
      nav a, aside a{
        color: blue;
      }
      ```

    + 处理这种群组选择器规则嵌套上的强大能力，正是 Sass 在减少重复敲写方面的贡献之一。尤其当嵌套级别达到两层甚至三层以上时，与普通的 CSS 编写方式相比只写一边群组选择器大大减少了工作量。
    + 有利有弊，你需要特别注意群组选择器的规则嵌套生成的 CSS。虽然 Sass 让你的样式表看上去很小，但实际生成的 CSS 非常庞大，这会降低网站的速度。

    (4) 子组合选择器和同层组合选择器：`>`、`+`、`~`

    + 上面着三个组合选择器必须和其他选择器配合使用，以制定浏览器进选择某种特定上下文中的元素，如

      ``` css
      article section {
        margin: 5px;
      }
      article > section {
        border: 1px solid #ccc;
      }
      ```

    + 子组合选择器 `>` 选择一个元素的直接子元素。上例中，第一个选择器会选择 `article` 下的所有命中 `section` 选择器的元素。第二个选择器只会选择 `article` 下紧跟着的子元素中命中的 `section` 选择器的元素。
    + 在下例中，你可以用同层相邻组合选择器 `+` 选择 `header` 元素后紧跟的 `p` 元素。

      ``` css
      header + p {
        font-size: 1.1em;
      }
      ```

    + 你也可以用同层全体组合选择器 `~`，选择所有跟在 `article` 后面的同层 `article` 元素，不管它们之间隔了多少其他元素。

      ``` css
      article ~ article {
        border-top: 1px dashed #ccc;
      }
      ```

    + 这些组合选择器可以毫不费力地应用到 Sass 的规则嵌套中。可以把它们发在外层选择器后面，或者里层选择器前边，如：

      ``` scss
      article {
        ~ article {
          border-top: 1px dashed #ccc;
        }
        > section {
          background: #eee;
        }
        dl > {
          dt { color: #333; }
          dd { color: #555; }
        }
        nav + & {
          margin-top: 0;
        }
      }
      // Sass 会如你所愿的将这些嵌套规则解开组合在一起
      article ~ article { border-top: 1px dashed #ccc; }
      article > section { background: #eee; }
      article dl > dt { color: #333; }
      article dl > dd { color: #555; }
      nav + article { margin-top: 0; }
      ```

    + 在 Sass 中，不仅 CSS 规则可以嵌套，对属性进行嵌套也可以减少很多重复性的工作。

    (5) 嵌套属性

    + Sass 中，除了 CSS 选择器，属性也可以进行嵌套，尽管编写属性涉及的重复不想编写选择器那么糟糕，但是反复写 `border-style`、`border-color`、`border-width` 以及 `border-*` 等类似情况也是非常烦人的。在 Sass 中，你只需敲写一遍 `border`：

      ``` scss
      // 6attr_nested.scss
      nav {
        border: {
          style: solid;
          width: 1px;
          color: #ccc;
        }
      }
      ```

    + 属性嵌套规则：把属性名从中划线 `-` 的地方短卡，在根属性后面添加一个冒号并紧跟一个花括号 `: {}`，把子鼠星部分写在这个花括号中。就像 CSS 选择器嵌套一样，Sass 会把你的子属性一一解开，把根属性和子属性部分通过中划线 `-` 连接起来，最后生成的效果与你手动一遍遍写的 CSS 样式一样。

      ``` CSS
      /* 上面代码编译后 */
      nav {
        border-style: solid;
        border-width: 1px;
        border-color: #ccc;
      }
      ```

    + 对于属性的缩写形式，你甚至可以像下边这样来嵌套，指明例外规则：

      ``` scss
      // 6attr_nested.scss
      .box {
        border: 1px solid #ccc {
          left: 0px;
          right: 0px;
        }
      }
      // 编译后
      .box {
        border: 1px solid #ccc;
        border-left: 0px;
        border-right: 0px;
      }
      ```

4. 导入 Sass 文件

    (1) 导入 Sass 简介

    + CSS 有一个特别不常用的特征，即 `@import` 规则，它允许在一个 CSS 文件中导入其他 CSS 文件。然而，后果是只有执行到 `@import` 时，浏览器才会下载其他 CSS 文件，这导致页面加载起来特别慢。
    + Sass 也有一个 `@import` 规则，但不同的是 Sass 的 `@import` 规则在生成 CSS 文件时就把县官文件导入进来。这意味着所有的相关的样式被归纳到统一个 CSS 文件中，而无需发起额外的下载请求。另外，所有在被导入文件中定义的便来给你和混合器均可在导入文件中使用。
    + 使用 Sass 的 `@import` 规则并不需要知名被导入文件的全名。你可以省略 `.sass` 或 `.scss` 文件后缀名。这样，在不修改样式表的前提下，你完全可以随意修改你或别人写的被导入的 Sass 样式文件语法，在 Sass 和 scss 语法之间随意切换。举例来说，`@import "sidebar";` 这条命令将把 sidebar.scss 文件中所有样式添加到当前样式表中。
    + 接下来我们将介绍如何使用 Sass 的 `@import` 来处理多个 Sass 文件。首先，我们将学习编写那些被导入的 Sass 文件，因为在一个大型 Sass 项目中，这样的文件是你最常编写的那一类。接着，了解集中导入 Sass 文件的方法，使你得样式可重用性更高，包括声明可自定义的变量值，以及在某一个选择器范围内导入 Sass 文件。最后介绍如何在 Sass 中使用 CSS 原生的 `@import` 命令。
    + 通常，有些 Sass 文件用于导入，你并不希望为每个这样的文件单独生成一个 CSS 文件。对此 Sass用一个特殊的约定来解决。

    (1) 使用 Sass 部分文件

    + 当通过 `@import` 把 Sass 样式分散到多个文件时，你通常只想生成少数几个 CSS 文件。那些专门为 `@import` 命令而编写得 Sass 文件，并不需要生成对应的独立 CSS 文件，这样的 Sass 文件称为局部文件。对此，Sass 又有一个特殊的约定来命名这些文件。
    + 此约定即：Sass 局部文件的文件名以下划线 `_` 开头。这样，Sass 就不会在编译时单独编译这个文件输出为 CSS 文件了，而知识把这个文件用作导入。当你 `@import` 导入一个局部文件是，还可以不写文件的全名，即省略文件名开头的下划线。
    + 局部文件可以被多个不同的文件引用。当一些央视需要在多个页面甚至多个项目中使用时，这非常有用。在这种情况下，有时需要在你的样式表中对导入的样式稍作修改，Sass 有一个功能刚好可以解决这个问题，即默认变量值。

    (2) 默认变量值

    + 一般情况下，你反复声明一个变量，只有最后一处声明有效且他会覆盖前边的值。

      ``` scss
      $link-color: blue;
      $link-color: red;
      a {
        color: $link-color;
      }
      ```

    + 在上边的例子中，超链接的 `color` 会被设置为 `red`。这可能并不是你想要的结果，加入你写了一个可被他人通过 `@import` 导入的 Sass 库文件，你可能希望导入者可以定制修改 Sass 库文件中的某些值。使用 Sass 的 `!default` 关键词可以实现这个目的。它很像 CSS 属性中的 `!important` 关键字的对里卖弄，不同的是 `!default` 用于变量，含义是：如果这个变量被声明复制了，那就用它声明的值，否则就用这个默认值。

      ``` scss
      // _2defalut_var.scss
      $fancybox-width: 500px;
      // 2default_demo.scss
      @import '2default_var';
      $fancybox-width: 400px !default;
      .fancybox {
        height: 500px;
        width: $fancybox-width;
      }
      // 编译后 css 文件
      .fancybox {
        height: 500px;
        width: 500px;
      }
      ```

    + 在上例中，如果跟用户在导入你的 Sass 局部文件之前声明了一个 `$fancybox-width` 变量，那么你的据部分文件中对 `$fancybox-width` 赋值 `500px` 就徐笑了。如果用户没有做 `!default` 的修饰，那么 `$fancybox-width` 的值将为 `400px`。

    (3) 嵌套导入

    + 跟原生的 CSS 不同，Sass 允许 `@import` 命令写在 CSS 规则内。这种导入方式下，生成对应的 CSS 文件时，局部文件被直接插入到 CSS 规则内导入它的地方，如下例：

      ``` scss
      // _blue-theme.scss
      aside {
        background: blue;
        color: white;
      }
      // 导入到 CSS 规则内，如下
      .blue-theme {
        @import 'blue-theme';
      }
      // 生成的结果根直接在 .blue-theme 选择器内写 _blue-theme.scss 文件的内容完全一样
      .blue-theme aside {
        background: blue;
        color: white;
      }
      ```

    + 被导入的局部文件中定义的所有变量和混合器，也会在这个规则范围内生效。这些变量和混合器不会全局有效，这样我们就可以通过嵌套导入只对站点内某一特定区域运用某种颜色主题或其他通过变量配置的样式。

    (4) 原生的 CSS 导入

    + 由于 Sass 兼容原生的 CSS，所以它也支持原生的 CSS `@import`。尽管通常在 Sass 中使用 `@import` 时，Sass 会尝试找到对应的 Sass 文件并导入进来，但在下列三种情况下生成原生的 CSS `@import`，尽管这会造成浏览器解析 CSS 时的额外下载。
      + 被导入文件的名字以 `.css` 结尾；
      + 被导入文件名字是一个 URL 地值（如：http://www.sass.hk/css/css.css），由此可用谷歌字体 API 提供的相应服务；
      + 被导入文件的名字时 CSS 的 `url()` 值。
    + 这就是说，你不能用 Sass 的 `@import` 直接导入一个原始的 CSS 文件，因为 Sass 会以为你想用 CSS 原生的 `@import`。但是，因为 Sass 的语法完全兼容 CSS，所以你可以把原始的 CSS 文件改名为 `.scss` 后缀，即可直接导入了。

5. 静默注释

    (1) 文件导入是保证 Sass 的代码可维护性和可读性的重要一环。次之但也非常重要的就是注释了。注释可以帮助样式作者记录写 Sass 的过程中的想法。在原生的 CSS 中，注释对于其他人是直接可见的，但 Sass 提供了一种可在生成 CSS 文件中按需抹掉的注释。

    (2) CSS 中注释的作用包括帮助你组织样式、以后你看自己的代码时明白为什么这样写，以及简单的央视说明。但是你并不希望每个浏览网站源码的人都能看到所有注释。Sass 另外提供了一种不同于 CSS 标准注释格式 `/*...*/` 的注释语法，即静默注释，其内容不会出现在生成的 CSS 文件中。静默注释的语法跟 JavaScript 等语言中单行注释的语法相同，它们以 `//` 开头，注释内容直到行末。

    ``` scss
    body {
      color: #333; // 这种注释内容不会出现在生成的 CSS 文件中
      padding: 0; /* 这种注释内容会出现在生成的 CSS 文件中 */
    }
    ```

    (3) 实际上，CSS 标准注释格式 `/*...*/` 内的注释内容可再生成CSS 文件中抹去。当注释出现在原生 CSS 不允许的地方，如在 CSS 属性或选择器中，Sass 将不知如何将其生成到对应的 CSS 文件中的相应位置，于是这些注释被抹掉。

    ``` scss
    body {
      padding: 1 /* 这块注释内容不会出现在生成的 CSS 文件中 */ 0;
    }
    ```

    (4) 注意事项，中文编译报错问题解决方案

    + Sass 文件编译时候使用 Ruby 环境，在 Windows XP 环境中没有任何问题，但是在 Windows 7 环境下无论是界面化的 Koala 工具还是命令行模式的都会出现以下错误：

      ``` shell
      Syntax error: Invalid GBK character "xE5"
      ...
      Use -trace for backtrace
      ```

    + 解决方法：
      + Koala 可视化编译工具：找到安装目录里面 sass 模块下面的 engine.rb 文件，例如 `D:\Program Files (x86)\Koala\rubygems\gems\sass-3.5.2\lib\sass\engine.rb`，在文件 engine.rb 文件中添加一行代码：`Encoding.default_external = Encoding.find('utf-8')`，这行代码放在所有 `require` 语句后面就可以。
      + 命令行工具同理，需要在 Ruby 目录下找到 engine.rb 添加这行代码，路径参考：`C:\Ruby27-x64\lib\ruby\gems\2.7.0\gems\sass-3.7.4\lib\sass`

6. 混合器

    (1) 混合器简介

    + 如果你的整个网站中有几处小小的样式类似（例如一致的颜色和字体），那么使用变量来统一处理这种情况是非常不错的训责。但是当你的样式变得越来越复杂，你需要大段大段的宠用样式的代码，独立的变量就没办法应付这种情况了。你可以通过 Sass 的混合器实现大段样式的重用。
    + 混合器使用 `@mixin` 标识符定义。看上去很像其他的 CSS `@` 标识符，比如说 `@media` 或者 `@font-face`。这个标识符给一大段样式赋予一个名字，这样你就可以轻易的通过引用这个名字重用这段样式。下面的这段 Sass 代码，定义了一个非常简单的混合器，目的是添加跨浏览器的圆角边框。

      ``` scss
      @mixin rounded-corners {
        -moz-border-radius: 5px;
        -webkit-border-radius: 5px;
        border-radius: 5px;
      }
      ```

    + 然后就可以在你的样式中通过 `@include` 来使用这个混合器，放在你希望的任何地方。`@include` 调用会把混合器中所有样式提取出来放在 `@inlude` 被调用的地方，如下所示：

      ``` scss
      .notice {
        background-color: green;
        border: 2px solid #00aa00;
        @include rounded-corners;
      }
      // 最终的 sass 文件
      .notice {
        background-color: green;
        border: 2px solid #00aa00;
        -moz-border-radius: 5px;
        -webkit-border-radius: 5px;
        border-radius: 5px;
      }
      ```

    + 在 `.notice` 中的属性 `border-radius` `-moz-border-radius` `-webkit-border-radius` 全部来自 `rounded-corners` 这个混合器。这一节将介绍使用混合器来避免重复。通过使用参数，你可以使用混合器把你样式中的通用样式抽离出来，然后轻松地在其他地方重用。实际上，混合器太好用了，一不小心你可能会过度使用。大量的宠用可能会导致生成的样式表过大，导致加载缓慢；所以，首先我们将讨论混合气的适用场景，避免滥用。

    (1) 何时使用混合器？

    + 利用混合器，可以很容易的在样式表的不同地方共享样式。如果你发现自己在不停重复一段样式，那就应该把这段样式构造成优良的混合器，尤其是这段样式本身就是一个逻辑单元，比如说是一组放在一起有意义的属性。
    + 判断一组属性是否应该组成一个混合器，一条经验法则就是你能否为这个混合器想出一个有意义的名字。如果你能找到一个很好的段名字来描述这些属性修饰的样式，比如 `rounded-corners` `fancy-font` 或者 `no-bullets`，那么往往能够构造一个合适的混合器。如果你找不断哦，这时候构造一个混合器可能并不合适。

    (2) 混合器的 CSS 规则

    + 混合器中不仅可以包含属性，也可以包含 CSS 规则，包含选择器和选择器中的属性，如下：

      ``` scss
      @mixin no-bullets {
        list-style: none;
        li {
          list-style-image: none;
          list-style-type: none;
          margin-ledt: 0px;
        }
      }
      ```

    + 当一个包含 CSS 规则的混合器通过 `@include` 包含在一个父规则中时，在混合器中的规则最终会生成父规则中的嵌套规则。举个例子，看看下边的 Sass 代码，这个例子中使用了 `no-bullets` 这个混合器

      ``` scss
      ul.plain {
        color: #444;
        @include no-bullets();
      }
      ```

    + Sass 的 `@include` 指令将引入混合器的那行代码替换成混合器里边的内容。最终生成如下代码：

      ``` CSS
      ul.plain {
        color: #444;
        list-style: nonel
      }
      ul.plain li {
        list-style-image: none;
        list-style-type: none;
        margin-left: 0px;
      }
      ```

    (3) 给混合器传参

    (4) 默认参数值
