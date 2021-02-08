DOM: Document object model

## important tags

### title

`<h1>` --- `<h6>`

### list

ordered list: (has 1, 2, 3...)
```html
<ol>
	<li></li>
	<li></li>
	<li></li>
</ol>
```

unordered list: each item begins with bullet point
```html
<ul>
	<li></li>
	<li></li>
	<li></li>
</ul>
```

### image

`<img src="path/to/image" alt:"text_appears_when_image_doesn't_show" width="300" height="300" />`

alt: altenative text

### link

`<a href="path/or/url">text_showed</a>`

### table

```
<table>
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
</table>
```

### form  (provide information to pages)

```html
<form>
    <input type="text" placeholder="default_text_in_the_input" name="name_this_input" />
    <input type="submit"/>
</form>
```

A more commplicated example:

```html
<form>
    <div>
        <input name="full name" type="text" placeholder="full name" />
        <input name="password" type="password" placeholder="Password" />
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
</form>
```

`<datalist>` gives a liste of value to choose, if we type some charecters, il will also filter the choices.

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
- 等宽字体

正确显示预留字体：

HTML字符实体 （Character Entities）: 使用*实体编号*或*实体名称*替换均可
| 字符 | 实体编号 | 实体名称 | 英文名 |
| ---- | -------- | -------- | ------ |
| < | `&#60;` | `&lt;` | less-than |
| > | `&#62;` | `&gt;` | greater-than |
| " | `&#34;` | `&quot;` | quotation |
| ' | `&#39;` | `&apos;` | apostrophe |
| & | `&#38;` | `&amp;` | ampersand |

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