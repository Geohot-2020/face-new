### 1. box-sizing属性作用，content-box和border-box区别

`box-sizing`用于控制元素宽度和高度的计算方式，包括`content-box`和`border-box`

|        |                   content-box                   |            border-box             |
| :----: | :---------------------------------------------: | :-------------------------------: |
| 默认值 | 仅包括内容区域，不包括内边距padding和边框border |  包括内容区域、内边距和边框尺寸   |
|  计算  |        宽度 = 内容宽度，高度 = 内容高度         | 宽度 = 内容+内边距+边框，高度也是 |

border-box更便于控制元素尺寸的布局，更多

### 2. opacity和rgba()区别

|          |                  opacity                  |                   rgba()                    |
| :------: | :---------------------------------------: | :-----------------------------------------: |
|   定义   | CSS属性，用于设置整个元素和子元素的透明度 |       颜色函数，定义允许透明度的颜色        |
|   取值   |                  [0, 1]                   | [0, 255].rgba(255, 0, 0, 0.5)表示半透明红色 |
| 影响范围 |            该元素和所有子元素             |       影响所应用的颜色，其他元素不会        |

### 3. CSS代表什么

层叠样式表Cascading Style Sheets。用于描述HTML或XML文档的样式和布局的样式表语言

### 4. 引入方式， link和@import区别

**引入方式：**

1. 外部样式表 <link>

   存储在.css文件中，并通过<link>链接，支持样式重用，易于管理和维护。同时由于浏览器缓存的机制，可用加快页面加载速度。

   ```html
   <link rel="stylesheet" type="text/css" href="styles.css">
   ```

   

2. 内部样式表 HTML文档的<head>部分使用<style>标签写

   单个文档，小网站

   ```html
   <style>
       body {
           background-color: lightblue;
       }
   </style>
   ```

3. 内联样式:在HTML元素的style属性中设置

   优先级最高，影响性能

```html
<h1 style="color: blue;">Hello World</h1>
```

|              |       link更优       |                   @import                   |
| :----------: | :------------------: | :-----------------------------------------: |
|   语法位置   | HTML文档的<head>部分 |                CSS规则的顶部                |
|   加载顺序   |   页面加载立即生效   |               等主CSS加载完成               |
| 支持的浏览器 |         所有         |               旧版可能不一致                |
|   使用场景   |  大型网站的样式文件  | 从一份主样式表引入其他样式表，用于模块化CSS |

### 5. 基本语句构成

```css
选择器 {
	属性: 属性值;	
}
```

**选择器：**

- 元素选择器: h1, p
- 类选择器：.className
- ID选择器：#idname
- 组合选择器：div > p

**属性：**

color, font-size, margin...

**属性值：**

red/.. 16px 10%

### 6. 盒模型

1. **内容区域Content**：元素实际显示内容区域，大小由width和height决定。实际内容区域，如文本、图像
2. **内边距Padding**：内容区域和边框之间的空间，背景颜色和元素背景颜色相同。透明
3. **边框Border**：包围内容和内边距的线，通过border设置边框宽度、样式和颜色
4. **外边距**：边框外部的空间，与其他元素或页面边缘距离，通过margin设置，透明而无颜色

通过box-sizing属性，选择使用content-box或border-box盒模型

- **标准盒模型 (W3C Box Model)**：content-box，**宽度和高度只包括内容区域**，内边距和边框的宽度会被加到最终的尺寸上。
- **IE 盒模型**：border-box，**宽度和高度包括了内容、内边距和边框**，使得总宽度和总高度等于指定值。

### 7. CSS规则的组成

1. **选择器**：指定要应用样式的HTML元素
2. **声明块**：包含一个或多个声明
3. **声明**：属性和值组成
4. **属性：**描述样式特征
5. **值**：具体样式值

### 8. CSS选择器种类

1. **基础选择器**

- 元素选择器：指定元素 <div> <p>
- 类选择器：.class-name
- ID选择器：#id-name
- 通配符选择器：*

2. **组合选择器**

- 后代选择器：div p所有div内部的p元素
- 子选择器：ul>li 选中ul下直接的li元素
- 相邻兄弟选择器：h1+p 选中h1后面紧跟的第一个p元素
- 一般兄弟选择器：h1~p 所有h1后面的p元素

3. **属性选择器**

元素的属性值

[type="text"] 所有type为text的输入元素

4. **伪类选择器**

元素的特定状态

:hover 选中鼠标悬停

5. **伪元素选择器**

选中元素的特定部分

::before 在元素前添加内容

6. **群组选择器**

h1, h2, h3同时选中h1/h2/h3

### 9. ID选择器和类选择器区别

|        |         ID选择器         |         类选择器         |
| :----: | :----------------------: | :----------------------: |
|  语法  |         #id-name         |       .class-name        |
| 唯一性 | 唯一，每个元素只能有一个 |   多个元素可共享一个类   |
| 优先级 |            高            |            低            |
|  用途  |     唯一标识单个元素     | 样式相似的多个元素，复用 |

### 10. padding和margin区别

|                |     Padding      |                       Margin                       |
| :------------: | :--------------: | :------------------------------------------------: |
|      定义      | 内边距，元素内部 |                  外边距，元素外部                  |
|  影响元素大小  |       影响       |                       不影响                       |
| 背景颜色和边框 |    和元素同色    |                     不显示颜色                     |
|    合并特性    |      不合并      | 垂直合并，有相同外边距时，合并成为一个较大的外边距 |

### 11. position的值

1. **static**：默认值，正常定位
2. **relative**：相对定位，根据正常定位偏移
3. **absolute**：绝对定位，相对于已定位的父元素定位
4. **fixed**：固定定位，滚动时不移动
5. **sticky**：粘性定位，滚动到指定位置，元素粘在那个位置

### 12. 如何使用媒体查询

基本语法

```css
@media 媒体类型 and (条件) {
	/* CSS样式 */
}
```

查询屏幕宽度

```css
@media (max-width: 600px) {
    body {
        /* 屏幕宽度小于600设置背景色 */
        background-color: lightblue;
    }
}
```

多个条件

```css
@media (min-width: 600px) and (max-width: 1200px) {
    body {
        font-size: 18px; /* 在屏幕宽度在600px到1200px之间时设置字体大小 */
    }
}
```

目标特定设备类型

```css
@media print {
    body {
        font-size: 12pt; /* 在打印时设置字体大小 */
    }
}
```

使用不同媒体特性

```css
@media (orientation: landscape) {
    body {
        background-color: lightgreen; /* 在横屏模式下设置背景色 */
    }
}
```

### 13. 设置边框样式

```css
.box {
    border: 2px solid blue;	/* 所有边框 */
    border-top: 1px;	/* 上下左右 */
    border-right: 1px;
    border-left: 1px;
    border-bottom: 1px;
    border-width: 3px;	  /* 宽度 */	
    border-style: groove; /* 边框样式 */
    border-color: orange; /* 边框颜色 */
}
```

常用的边框样式

- `none`: 没有边框
- `solid`: 实线边框
- `dashed`: 虚线边框
- `dotted`: 点线边框
- `double`: 双线边框
- `groove`: 3D 凹槽效果
- `ridge`: 3D 脊效果
- `inset`: 3D 内嵌效果
- `outset`: 3D 凸起效果

### 14. 隐藏元素但保留占位

```html
<div class="hidden"></div>
```

```css
.transparent {
    opacity: 0; /* 0 代表完全透明，1 代表完全不透明 */
}
```

使用固定的高度和宽度:zero:

### 15. 设置边距和填充

边距：

- 设定元素与**其他元素**之间的空间
- 上下左右：mt mr mb ml
- 可以自动调整，如margin:auto 元素居中
- 支持负值，元素重叠

填充：

- 设定元素与**边框**的空间
- 上下左右：pt pr pb pl
- 影响实际尺寸，不会和其他元素重叠

### 16. CSS样式应用到HTML

1. 内联样式：`style`

```html
<h1 style="color: blue; font-size: 20px;">Hello World</h1>
```

2. 内部样式表： `<style>`

```html
<head>
    <style>
        h1 {
            color: blue;
            font-size: 20px;
        }
    </style>
</head>
<body>
    <h1>Hello World</h1>
</body>
```

3. 外部样式表： `<link>`

```html
<head>
    <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
    <h1>Hello World</h1>
</body>
```

4. import

```html
@import url("another-styles.css");
```

- 内联优先级最高，但不利于维护
- 内部样式表小项目
- 外部样式表大型项目，复用和分离

### 17. 设置背景颜色和图片

```css
/* 设置背景颜色和背景图片 */
.element {
    background-color: #f0f0f0; /* 背景颜色 */
    background-image: url('path/to/your/image.jpg'); /* 背景图片 */
    background-size: cover; /* 让背景图片覆盖整个元素 */
    background-position: center; /* 背景图片居中 */
    background-repeat: no-repeat; /* 不重复背景图片 */
}
```

### 18. 对一个DOM设置CSS

1. 内联样式
2. 内嵌样式表
3. 外部样式表
4. CSS选择器：类、ID、标签名等选择器
5. Js操作：style或classList
6. CSS变量
7. CSS框架：Tailwind CSS
8. 预处理器：LESS或SASS，编译过程中生成CSS
9. 样式组件化： CSS-in-JS，将样式和组件逻辑绑定

### 19. 行内元素和块级元素区别

|                 |             行内元素             |               块级元素                |
| :-------------: | :------------------------------: | :-----------------------------------: |
|    显示行为     |    占整个容器宽度，在前后换行    |      只占内容宽度，不在前后换行       |
|   宽度和高度    |              可设置              |         不可设置，由内容决定          |
|    内部元素     |    包含其他块级元素和行内元素    |      只能包括行内元素，不能块级       |
| Margin和Padding |                有                | 只有左右Padding和margin有效，上下无效 |
|      float      | 可以浮动在左或右且影响周围的布局 |        行内元素浮动影响所在行         |
|      举例       |       <div> <p> <h1> <ul>        |          <span> <a> <strong>          |

### 20. display属性值

- block：块级	<div>
- inline：内联 <span>
- inline-block：元素不会换行，但可以设置宽高
- none：不显示页面，也不占用空间
- flex：弹性容器，根据容器方向调整子容器布局
- grid：网格
- table
- list-item：与<ul> <ol>相关
- run-iun：某些情况下，作为块级或内联元素显示

### 21. position值

- static：默认值，正常流定位，top、right、bottom、left无效
- relative：不受影响，只根据trbl定位
- absolute：根据初始定位，根据父元素
- fixed：即使滚动页面，也不移动
- sticky：跨越指定阈值为relative，达到阈值fixed

### 22. display:none和visibility:hidden区别

| display:none | visibility:hidden |
| :----------: | :---------------: |
|   完全移除   |   占位置和空间    |
| 子元素也隐藏 | 子元素仍占据空间  |

### 23. px、em、rem区别

|            |         px         |     em     |    rem     |
| :--------: | :----------------: | :--------: | :--------: |
|    基准    | 固定值，物理像素点 | 相对父元素 | 相对根元素 |
|  是否继承  |         否         |     是     |     否     |
|  维护难度  |         低         |     高     |     低     |
| 响应式适配 |         弱         |     中     |     强     |

