# HTML5+CSS3学习记录

1. [视频链接](https://www.bilibili.com/video/av53158375)
2. 笔记为个人纪录，章节号与文件夹序号对应

## 01什么是HTML5,HTML5新特性概览-新的标签属性

1. H5并不是新的语言，而是HTML语言的第五次重大版本修改。
2. 支持：所有的主流浏览器都支持H5（Chrome,FireFox,Safari,IE9及以上版本,IE9为有选择的支持非全部支持）。
3. 改变了用户与文档的交互方式：多媒体：video,audio,canvas。
4. 增加了其他的新特性：语义特性，本地存储，网页多媒体，二维三维变换，特效(过渡，动画)。
5. 相对于HTML4:

    + 进步：抛弃了一些不合理不常用的标记和属性
    + 新增了一些标记和属性--表单
    + 从代码角度而言，H5网页结构代码更加简洁

6. 语义标签：[HTMl标签参考](https://www.w3school.com.cn/tags/index.asp)

    | 标签名 | 作用 |
    | :---: | :-: |
    | nav | 表示导航 |
    | header | 表示页眉 |
    | footer | 表示页脚 |
    | main | 表示主要内容 |
    | article | 文章 |
    | aside | 主题内容之外 |
    | footer | 文档或者页的页脚 |

    + 语义标签兼容性问题的两种解决方式：创建标签，将行级元素设置为块级元素；引入html5shiv.js第三方插件

7. 表单新增属性，[type属性](https://www.w3school.com.cn/html5/html_5_form_input_types.asp)

    + 以下主要针对input标签

    | type | 效果 |
    | :---: | :-: |
    | text | 输入普通文本信息 |
    | password | 密码输入，显示为* |
    | email | 邮箱输入，校验邮箱格式 |
    | tel | 电话号码输入，主要针对移动端调用数字键盘输入 |
    | url | 网址输入 |
    | search | 带有清空按钮的文本输入 |
    | range | 范围滑条 |
    | color | 颜色拾取 |
    | time | 时间选择，时分 |
    | date | 日期选择，年月日 |
    | datetime/datetime-local | 日期时间选择，年月日时分 |
    | month | 月份选择 |
    | week | 周选择 |

    + 新增其他表单属性

    | 属性名 | 效果 |
    | :---: | :-: |
    | placeholder | 输入框提示信息，提示占位 |
    | autofocus | 自动获取焦点 |
    | autocomplete | 自动完成，on/off，需指定name属性并成功提交一次 |
    | require | 必须输入，不输入无法提交 |
    | pattern | 正则匹配，如自定义手机号验证 |
    | multiple | 文件拾取多选，多个邮箱输入等 |
    | form | 为form标签之外的表单元素指定隶属的表单，从而跟随表单一同提交数据 |

8. HTML5引入一种新的select下来选择菜单datalist；keygen元素是密钥对生成器，当提交表单时，会生成两个键，一个是私钥，一个是公钥；output元素用于放置输出内容。
9. HTML5新增表单事件：oninput监听表单控件的内容改变；onincalid监听表单提交失败的事件，其中this.setCustomValidity()可以修改表单控件验证的错误提示信息。
10. HTML5两种进度条：progress,meter。
11. HTML5提供的媒体标签：audio，video，注意source的使用。
12. HTML5提供的获取DOM元素的两种方式：querySelector，querySelectorAll。
13. HTML5提供的类样式操作classList.add()/.toggle()/.remove()/.contains()/.item()。
14. HTML5提供的自定义属性(data-)：定义和获取的方法。

## 02HTML5提供的新的接口

1. 网络接口：online，offline，分别监听网络链接与断开。
2. 全屏API：requestFullScreen():开启全屏,cancelFullScreen()：取消全屏,fullScreenElement:监听全屏状态。
3. 文件读取接口FileReader

    + 方法

    | 方法名 | 作用 |
    | :--: | :--: |
    | readAsText() | 读取文本文件(可以使用txt打开的文件)，返回文本字符串值，默认编码是UTF-8 |
    | resadAsBinaryString() | 读取任意类型的文件，返回二进制字符串 |
    | readAsDataURL() | 读取文件获取一段以data开头的字符串，这段字符串的本质就是DataURL |
    | abort() | 中断读取 |

    + FileReader提供了一个完整的事件模型，用来捕获读取文件时的状态

    | 事件名 | 作用 |
    | :--: | :--: |
    | onabort | 读取文件断开时触发 |
    | onerror | 读取错误时触发 |
    | onload | 文件读取成功完成时触发 |
    | onloadend | 读取完成时触发，无论成功还失败 |
    | onloadstart | 开始读取时触发 |
    | onprogress | 读取文件过程中持续触发 |

4. HTML5提供的元素拖拽接口，主要是通过元素拖拽事件来完成，分为两类：

    + 应用于被拖拽元素的事件：

    | 事件名 | 调用时刻 |
    | :--: | :--: |
    | ondrag | 整个拖拽过程都会调用 |
    | ondragstart | 当拖拽动作开始时调用 |
    | ondragleave | 当鼠标离开拖拽元素原始位置时调用 |
    | ondragend | 当拖拽结束时调用 |

    + 应用于目标元素的事件：

    | 事件名 | 调用时刻 |
    | :--: | :--: |
    | ondragenter | 当拖拽元素进入时调用 |
    | ondragover | 当停留在目标元素上时调用 |
    | ondrop | 当在目标元素上松开鼠标时调用(浏览器默认阻止) |
    | ondragleave | 当鼠标离开目标元素时调用 |

    + 通过事件捕获来获取当前元素e.target

    + 通过事件源参数e.dataTransfer()来实现数据的存储和获取

5. HTML5提供的获取地理位置的接口navigator.geolocation，通常浏览器禁止定位获取，需要地图开发的时候采用第三方工具的支持，如百度地图api。
6. HTML5提供的两种web存储方式，sessionStorage和localStorage

    + sessionStorage，数据存储到当前页面中，页面关闭则数据消失

    | 方法名 | 作用 |
    | :--: | :--: |
    | setItem(key, value) | 存储数据，键值对方式 |
    | getItem(key) | 获取数据，按键获取 |
    | removeItem(key) | 删除数据，按键删除 |
    | clear() | 清空所有sessionStorage存储数据 |

    + localStorage，数据存储到硬盘中；页面关闭数据不消失，同浏览器不同窗口共享数据，但是不同浏览器不共享数据，删除数据需要手动删除；常用方法与sessionStorage相似。

7. HTML5提供的应用缓存；cache manifest文件

    + 优势：可配置需要缓存的资源；网络无连接应用仍可使用；本地读取缓存资源，提升访问速度，增加用户体验；减少请求，缓解服务器负担。

    + Cache Manifest基础：CACHE MANIFEST文件开头、CACHE:要缓存的文件、NETWORK:需要向服务器请求的文件、FALLBACK:无法获取时替换的文件

8. 视频播放器案例-自定义媒体播放控件。[HTML5视频/音频参考手册](https://www.w3school.com.cn/tags/html_ref_audio_video_dom.asp)

    + 常用方法

    | 方法名 | 功能 |
    | :--: | :--: |
    | load() | 加载 |
    | play() | 播放 |
    | pause() | 暂停 |

    + 常用属性

    | 属性名 | 作用 |
    | :--: | :--: |
    | currentTime | 视频播放的当前进度 |
    | duration | 视频总时长 |
    | pause | 当前视频播放状态 |

    + 常用事件

    | 事件名 | 调用时机 |
    | :--: | :--: |
    | oncanplay | 视频可以开始播放时触发 |
    | ontimeupdate | currentTime变化时触发，如开始播放等 |
    | onended | 播放完毕时触发 |

## 03CSS3简介与基本应用

1. CSS3原则渐进增强，优雅降级。使用手册(语法)

    | 标识 | 表示 |
    | :--: | :--: |
    | [] | 表示可选项 |
    | &#124;&#124; | 表示或者 |
    | &#124; | 表示多选一 |
    | ？ | 表示0个或1个 |
    | {} | 表示范围 |

2. 选择器

    + 属性选择器

    | 属性选择器 | 介绍 |
    | :--: | :--: |
    | E[attr] | 拥有attr属性的E标签 |
    | E[attr=value] | attr属性为value的E标签 |
    | E[attr*=value] | attr属性内含value的E标签 |
    | E[attr^=value] | attr属性以value开头的E标签 |
    | E[attr$=value] | attr属性以value结尾的E标签 |

    + 伪类选择器，

    | 锚伪类(a标签使用) | 状态 |
    | :--: | :--: |
    | a:link | 未访问的链接 |
    | a:visited | 已访问的链接 |
    | a:hover | 鼠标移到的链接 |
    | a:active | 选定的链接 |

    | 伪类选择器 | 介绍 |
    | :--: | :--: |
    | 兄弟选择器 | 选择兄弟元素(同层) |
    | + | 相邻的指定的兄弟元素 |
    | ~ | 所有的指定的兄弟元素 |
    | 相对于父元素的结构伪类 | 以某元素相对于其父元素或兄弟元素的位置来获取元素的结构伪类 |
    | E:first-child | E的父元素下的第一个元素且为E元素 |
    | E:last-child | E的父元素下的最后一个元素且为E元素 |
    | E:first-of-type | E的父元素下的第一个E元素，过滤其他元素 |
    | E:last-of-type | E的父元素下的最后一个E元素，过滤其他元素 |
    | E:nth-child() | E的父元素下指定位置的E元素,括号内可以为索引(从1开始)、表达式、关键字 |
    | E:nth-of-type()/E:nth-last-of-type() | E的父元素下指定位置的E元素，过滤其他元素 |
    | E:empty | E的父元素下的内容为空的E元素 |
    | E:target | 配合锚点使用，当元素被触发为锚点元素的时候触发此伪类样式 |

    + 伪元素选择器 -- 伪元素：虚拟的元素，不会在DOM元素中生成

    | 伪元素选择器 | 介绍 |
    | :--: | :--: |
    | E:before,E:after | 1.是一个行内元素，如果像设置宽高则需要转换为块：display: block，float: **,position:  2.必须添加content，哪怕不设置内容，也需要content:""  3.E:after,E:before在旧版本里是伪类，在新版本里是为元素，新版本下E:before、E:after会被自动识别为E::before、E::after,按为元素来对待，这样做的目的是用来做兼容处理  4.E::before定义在一个元素的内容之前插入content属性定义的内容和样式  5.E::after定义在一个元素的内容之后插入content属性定义的内容和样式  6.IE6、7、8中不支持此伪元素，CSS2中E:after、E:before属于伪类，且没有伪元素的概念，CSS3中提出为元素的概念E::after、E:before，并且归属到了伪元素当中，伪类里就不再存在E:after、E:before了 6.DOM元素的左膀右臂 |
    | E::first-letter | 文本的第一个字母或字(不是词组) |
    | E::first-line | 文本的第一行 |
    | E::selection | 可改变选中文本的样式 |

3. 颜色
    + RGBA：R:红色，G:绿色，B:蓝色，A:透明度；数值(0-255)、百分比(0%-100%)，A取值为0-1。
    + HSLA：Hue：色相，色调，0(或360)表示红色，120表示绿色，240表示蓝色，也可去其他数值来指定颜色。取值为0-360，过渡为：红橙黄绿青蓝紫红；Saturation：饱和度，取值为0.0%-100.0%；Lightness：亮度，取值为0.0%-100.0%，50%为平衡值；Alpha：透明度，取值为0-1之间。
    + opacity：只能针对整个盒子设置透明度，子盒子及内容会继承父盒子的透明度；使用rgba来控制颜色，相对于opacity不具有继承性。
    + transparent：不可调节透明度，始终完全透明。

4. 文本阴影(shadow):text-shadow

    + 语法：

    ``` html
    text-shadow: none|<length>none|[<shadow>,]*<shadow>
    或
    text-shadow: none|<color>[,<color>]*
    ```

    也就是：
    text-shadow: [颜色(color)] x轴(X Offset) y轴(Y Offset) 模糊半径(Blur),[颜色(color) x轴(X Offset) y轴(Y Offset) 模糊半径(Blur)]...
    或者
    text-shadow: [x轴(X Offset) y轴(Y Offset) 模糊半径(blur) 颜色(color)],[x轴(X Offset) y轴(Y Offset) 模糊半径(blur) 颜色(color)]...

    + 取值：

    <length>：长度值，可以是负值，用来指定阴影的延伸距离。其中X Offset是水平偏移值，Y Offset是垂直偏移值。
    <shadow>：阴影的模糊值，不可以是负值，用来指定模糊效果的作用距离。
    <color>：指定阴影颜色，也可以是rgba透明色。

    + 图示：
    ![text-shadow](https://i.loli.net/2019/09/17/LSpi34w5YXRoDZq.jpg)

5. 盒模型

    + 默认情况下，CSS设置的盒子宽度仅仅是内容区的宽度，而非和子的宽度。同样，高度类似。真正盒子的宽度(在页面呈现出来的宽度)和高度，需要加上一下其他的属性。例如：
    padding + border + width = 盒子的宽度；
    padding + border + height = 盒子的高度；
    很明显，这部只管很容易出错，造成网页中其他元素的错位。

    + CSS3种可以通过box-sizing来制定和模型，即可指定为content-box、border-box,这样我们计算盒子大小的方式就发生了改变；
    content-box：对象的 实际宽度等于设置的width值和border、padding之和；
    border-box：对象的实际宽度就等于设置的width值，即使定义有border和padding也不会改变对象的实际宽度。

6. 圆角:border-radius

    + 等宽高容器 - 向圆形进行设置

    | 参数个数 | 修改方面 |
    | :--: | :--: |
    | 一个参数 | 四个角都改变圆角，容器宽高一半时为正圆 |
    | 两个个参数 | 左上和右下，右上和左下搭配改变圆角 |
    | 三个参数 | 左上，右上和左下，右下搭配进行改变 |
    | 四个参数 | 左上，右上，右下，左下进行改变 |

    + 非等宽高容器 - 向椭圆进行设置，一个角有水平/垂直两个方向上的圆角设置，设置时以“/”进行分割。

    + 单独设置某个角的圆角：border-top-left-radius、border-top-right-radius、border-bottom-left-radius、border-bottom-right-radius

7. 使用CSS3设计一个安卓机器人，主要使用圆角、伪元素before、after，盒模型。

8. 边框阴影：box-shadow

    + 语法

    ``` html
    box-shadow: h v blur spread color inset
    ```

    + 参数

    | 参数名 | 作用 |
    | :--: | :--: |
    | h | 水平方向的偏移值 |
    | v | 垂直方向的偏移值 |
    | blur | 模糊值，可选 |
    | spread | 阴影尺寸，扩展和收缩阴影的大小，可选 |
    | color | 颜色，可选，默认黑色 |
    | inset | 内阴影，可选，不设置默认外阴影，设置后为内阴影 |

## 04CSS3中的渐变效果，背景样式，图片边框，过渡效果，变换效果

1. 渐变：渐变是CSS3当中比较费夫多彩的一个特性，通过渐变我们可以实现许多绚丽的效果，有效的减少图片的使用数量，并且句有很强的适应性和可扩展性。可分为线性渐变、径向渐变。

    + linear-gradient线性渐变指沿着某条直线朝一个方向产生渐变效果
    语法：

    ``` html
    linear-gradient([<point>||<angle>,]?<stop>,<stop>[,<stop>]*)
    ```

    参数说明：
    | 参数 | 说明 |
    | :--: | :--: |
    | point || angle | 表示线性渐变的方向；to left:设置渐变为从右到左，相当于270deg；to right:设置渐变从左到右，相当于90deg；to top:设置渐变从下到上，相当于0deg；to bottom:设置渐变从上到下，相当于180deg。这是默认值，等同于留空不写。该参数也可以直接指定度数，如45deg. |
    | stop | 起点颜色，可以指定颜色的位置 |
    | stop | 重点颜色，还可以在后面添加更多的参数，表示多种颜色的渐变 |
