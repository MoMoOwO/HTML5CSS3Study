# HTML5+CSS3学习记录

1. [视频链接](https://www.bilibili.com/video/av53158375)
2. 笔记为个人纪录，章节号与文件夹序号对应

## 01什么是HTML5,HTML5新特性概览

1. H5并不是新的语言，而是HTML语言的第五次重大版本修改
2. 支持：所有的主流浏览器都支持H5（Chrome,FireFox,Safari,IE9及以上版本,IE9为有选择的支持非全部支持）
3. 改变了用户与文档的交互方式：多媒体：video,audio,canvas
4. 增加了其他的新特性：语义特性，本地存储，网页多媒体，二维三维变换，特效(过渡，动画)
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