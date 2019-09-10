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
