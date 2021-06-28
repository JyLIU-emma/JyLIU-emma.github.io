DOM: Document object model

## important tags

### title

`<h1>` --- `<h6>`

### list

* ordered list: (has 1, 2, 3...)
```html
<ol type="1|A|a|I|i">
	<li></li>
	<li></li>
	<li></li>
</ol>
```
`<ol reversed>` 列表序号倒序，不影响内容顺序


* unordered list: each item begins with bullet point
```html
<ul>
	<li></li>
	<li></li>
	<li></li>
</ul>
```

* definition list 定义列表 `<dl>` 术语
```html
<dl>
	<dt>item名称</dt>
	<dd>item描述</dd>
</dl>
```


#### list  css
	`ul {list-style-type: square;}` disc 实心圆, circle空心圆, none；有序列表的标志
	`list-style-image: url("img/turtle.png")` 列表自定义标志图片（16*16）

### image

`<img src="path/to/image" alt:"text_appears_when_image_doesn't_show" width="300" height="300" />`

alt: altenative text

### link

`<a href="path/or/url">text_showed</a>`

### table

```
<table>
	<caption>Title of table, must aside by table</caption>
    <thead>
        <tr>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
	<tfoot>
		<td colspan="3"> Personal idea.</td>
	</tfoot>
</table>
```

for `td` 合并： 横向-- colspan; 纵向--rowspan

Pour traiter chaque colonne: `colgroupe` et `col`  
```
<colgroup>
	<col>
	<col style="background: red">
	<col style="background: blue">
</colgroup>
```

### form  (provide information to pages)

```html
<form action="exemple.php" method="post">
    <input type="text" placeholder="default_text_in_the_input" name="name_this_input" />
    <input type="submit"/>
</form>
```
#### `<form>` 
* `action` : 由谁来处理表单，被忽略，则由当前页面处理  
* `method` : 用什么方法来向服务器发送表单，get(提交的数据显示在url里)/post(通过http消息主体（request body），用于提交重要数据)

A more commplicated example:

```html
<form method="post">
    <div>
        <input name="full name" type="text" placeholder="full name" />
        <input name="password" type="password" placeholder="Password" />
		<!--提前填充值，可更改-->
		<input name="gender" type="text" value="female" />
    </div>

    <div>
        Favorite color ?
        <input name="color" type="radio" value="red"> Red
        <input name="color" type="radio" value="yellow"> Yellow
        <input name="color" type="radio" value="blue"> Blue
    </div>
    
    <div>
        <input name="country" list="countries" placeholder="Country" />
        <datalist id="countries">
            <option value="France">
            <option value="Chine">
            <option value="United States">
        </datalist>
    </div>
	
	<div>
		<button type="submit" formmethod="get|post">提交</button>
		<button type="reset">重写</button>
	</div>
</form>
```

####  `<input>`: 

- `autocomplete="off"` 关闭根据历史填写记录自动跳出下拉框的选项
- `autofocus` 自动聚焦，光标自动移至该填写框
- `readonly` 只读，无法更改，信息还是会提交

* type属性

- 单选 radio（同1个name才能实现互斥）

- 多选 checkbox

- 按钮 submit，reset， button（+ onclick插入点击后执行的动作）, value属性里显示按钮上文字

- 时间和日期：time, date, month年月, week星期, datatime-local本地日期和时间  
`<label>Time: <input type="time" name="time"></label>`

- 搜索框  
`<label>Item to search: <input type="search" name="search"></label>`

- 图像按钮
注释：如果type属性设置为image，当用户单击图像时，浏览器将以像素为单位，将鼠标相对于图像边界的偏移量发送到服务器 （以左上角为原点）  
`<label>This image is also a button: <input type="image" src="path/to/image" alt="description of image|Submit"></label>`

- 上传文件  
```
<form action="exemple.php" method="post" enctype="multipart/form-data">
	<!-- 限制文件大小 单位：字节，1024即1KB-->
	<input type="hidden" name="MAX_FILE_SIZE" value="1024">
	
	<!-- accept用于限制文件类型
		".jpg,.html,.avi"
		"image/*" 所有图片类型  类似还有："audio/*"  "video/*"
		MIME类型
	-->
	<label>Choose file: <input type="file" name="file" accept="image/*"></label>
	<!--上传多个文件-->
	<label>Choose file: <input type="file" name="file" accept="image/*" multiple></label>
</form>
```

* `<label>`:  点击提示字符，光标自动出现在填写框
`<label for="name">Name: </label><input name="Name" id="name">`


* `<button>` 中的`formmethod`可以覆盖`<form>` 中的`method`属性

* `<input>` 和 `<button>` 禁用（不能填写(input信息也不会提交,报废)/点击）：`disabled`

* 列表选择
1. **`<input> + <datalist> + <option>`** `<datalist>` gives a liste of value to choose, if we type some charecters, il will also filter the choices. 可以填写列表没有列出的值
2. **`<select> + <option>`**  只能从列表中选择


### 块级元素(block element) 和 行内元素(inline element)

**html将连续空白字符合并为一个空格** 特例：`<pre>`元素，保持原格式，用于预格式化文本

#### 块级元素(block element)
**总是在新行开始，并尽可能地占据本行全部可用宽度。**

- 可以包含行内元素和其他块级元素。(继承)

`<address> <article> <aside> <blockquote> <canvas> <dd> <div> <dl> <dt> <fieldset> <figcaption> <figure> <footer> <form> <h1>~<h6> <header> <hr> <main> <nav> <p> <pre> <section> <noscript> <ol> <ul> <li> <output> <table> <tfoot> <video>`

#### 行内元素(inline element)
** 行内元素不会另起一行，只占用必要的宽度 **

- 一般来说，只能包含数据和其他行内元素。

`<a> <abbr> <acronym> <b> <bdo> <big> <br> <button> <cite> <code> <dfn> <em> <i> <img> <input> <kbd> <label> <map> <object> <q> <samp> <script> <select> <small> <span> <strong> <sub> <sup> <textarea> <time> <tt> <var>`

#### `<pre>`
预格式化：保留文本在源代码中的格式，使得页面中显示的和源代码中的效果完全一致。
- 保留空格和换行符；
- 等宽字体 (Monospaced Font):字体宽度相同的计算机字体（适合编程的字体：Source Code Pro; Anonymous Pro，etc.）     vs    比例字体：字体的宽度不尽相同，增强可读性

### 语义化

使用恰当语义的HTML元素，使页面具有良好结构与含义，便于快速理解网页内容。

#### `<code>` 显示代码

正确显示预留字体：

HTML字符实体 （Character Entities）: 使用*实体编号*或*实体名称*替换均可
| 字符 | 实体编号 | 实体名称 | 英文名 |
| ---- | -------- | -------- | ------ |
| < | `&#60;` | `&lt;` | less-than |
| > | `&#62;` | `&gt;` | greater-than |
| " | `&#34;` | `&quot;` | quotation |
| ' | `&#39;` | `&apos;` | apostrophe |
| & | `&#38;` | `&amp;` | ampersand |

**代码块：使用`<pre>`嵌套`<code>`**

```html
<pre>
	<code>
	&#60;p&#62;喜欢吃的水果是：&#60;/p&#62;
	&#60;p&#62;桃子&#60;/p&#62;
	</code>
</pre>
```

#### `var kbd samp`  与编程有关的元素
* var	程序变量
* kbd	用户的输入
* samp	程序的输出

没有特殊显示格式。

```html
<p>Define a variable <var>user_input</var>, to accept the input</p>
<p>If user's input is <kbd>banana</kbd>, then the program will print <samp>Your favourite fruit is : banana</samp></p>
```

### 引用 `<q> <blockquote> <cite> <address> <abbr> <dfn>` 注音 文本方向

- Quote a sentence (short) inline:  
`<q>` (Default)Add automatically the quotation marks.

- Quote a paragraph (long):
`<blockquote cite="source">` Add indentation.

```html
<p>blablabla</p>
<blockquote>
	<p>1blablabla</p>
	<p>2blablabla</p>
	<p>3blablabla</p>
</blockquote>
```

- Define a work's name: `<cite>` (Default layout: Italic)

- `<abbr>` 缩写

- `<dfn>` 术语   
`<p><dfn>HTML</dfn> is a markup language.</p>`

- `<address>` 文档作者/所有者的联系信息 (Default layout: Italic)

```html
<address>
	<strong>Contact us: </strong><br>
	email:<a href="abcde@fg.com">abcde@fg.com</a><br>
</address>
```

- `<ruby> <rt> <rp>` 注音
`<ruby>斥<rp>(</rp><rt>chì</rt><rp>)</rp></ruby>`

- `<bdo>` 修改默认文本方向  
`dir`属性：
- ltr = left to right
- rtl = right to left

`<bdo dir="rtl"><p>apple</p></bdo><br>` 单词apple右对齐
`<bdo dir="rtl">apple</bdo><br>` 单词apple显示为elppa

### 格式化

- **粗体和斜体**

`<strong>` & `<b>` 都可以**粗体**，但前者有表示**重要**的语义；  
`<em>` & `<i>`  都可以**斜体**，但前者有表示**强调**的语义

建议粗体和斜体用css样式表实现：
`{font-weight: bolder; font-style: italic;}`

- **`<del>`(delete)  `<ins>`(insert)**
`<del>` 删除线  
`<ins>` 下划线

- **`<s>` 错误的内容，也是删除线**
- **`<u>` 拼写错误的单词，汉语专有名词，下划线**
- **`<mark>` 标记文本，黄色surligner**
- **`<sup>` 上标   `<sub>` 下标**
- **`<small>` 指定文本变小**


## CSS (used for layout of the page)

### 引入CSS的三种方法

** 内联样式：使用 `style` 属性(property) **

`<h1 style="color: blue; text-align: center;">Welcome!</h1>`

样式也可从父元素继承

** inline styling 内部样式表 **

在`<head>` 中添加：

```html
<head>
	<style>
		h1 {
			color: blue; 
			text-align: center;
		}
	</style>
<head>
```

** css files 外部样式表 **

```html
<head>
	<title>Document</title>
    <link rel="stylesheet" href="styles.css" />
<head>
```

the `styles.css` file: 

```css
h1 {
    color: blue;
    text-align: center;
}
```

### 宽度(width)，高度(height)，内边距(padding)，外边距(margin)

```css
div {
    background-color: yellowgreen;
    width: 300px;
    height: 300px;
    padding: 20px;
    margin: 20px;
}
```

### font 字体

```css
h1 {
    font-family: 'Times New Roman', Times, serif;
    font-size: 28px;
    font-weight: inherit;
}
```

`font-family` : in case the first one isn't supported by the computer used, add some backup choices.
`font-weight` : 是否粗体

### 边框 border


```css
table {
    border: 1px solid black;
    border-collapse: collapse;
}

td, th {
    border: 1px solid black;
}
```

**多项元素选择器 multiple element selector**

### two important selectors : id (unique) & class (several)

```css
#idName {
	color: blue;
}
.className {
	color: blue;
}
```

### other selectors**



### css样式权重  specificity
- 1. inline 内联样式
- 2. id
- 3. class
- 4. type (body, table, etc.)

```html
<div id="foo">
	Hello!
</div>
```

```css
#foo {
	color: red;
}

div {
	color: blue;
}
```

Result: hello in red, the order is not important





##  快捷键

### 自动生成 html外框结构 ：

`!+tab` 

## url中百分号编码（percent-encoding）:避免url中的歧义
- RFC3986标准

符号与百分号编码对照：
| 符号 | 编码 |
| ---- | ---- |
| `!` | %21 |
| `*` | %2A |
| `"` | %22 |
| `'` | %27 |
| `(` | %28 |
| `)` | %29 |
| `;` | %3B |
| `:` | %3A |
| `@` | %40 |
| `&` | %26 |
| `=` | %3D |
| `+` | %2B |
| `$` | %24 |
| `,` | %2C |
| `/` | %2F |
| `?` | %3F |
| `%` | %25 |
| `#` | %23 |
| `[` | %5B |
| `]` | %5D |


