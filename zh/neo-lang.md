## NeoLang 语言

### 什么是 NeoLang？
NeoLang 是一门专为 NeoTerm 设计的领域专用语言（DSL），旨在提供统一的配色方案和快捷键盘配置语法。NeoLang 的设计参考了 Json 和 css。但比它们都更加轻量，更适合于嵌入式和移动设备，且更易于学习。

### 我们将要做什么？
我们会逐步使用NeoLang取代较旧版本的一切配置文件，但在这个过程中，我们不会移除对旧版本配置文件的兼容性。直到我们认为旧版本配置文件已经过时，无过多用户仍在使用。

### 概览
为了尽可能的做到轻量化，NeoLang 只提供了描述数据的功能，并没有类似于函数或者其他高级语言里有的东西。一个NeoLang文件一般为以下模样：
```js
color-scheme: {
    name: "Default ColorScheme for NeoTerm"
    version: 1.1
    
    colors: {
        background: #ff000000
        foreground: #7a212121
    }
}
```
在上面的例子中，我们创建了一个叫做 `color-scheme` 的 `块`(`block`)，在这个`块`中我们又定义了`name`和`version`以及`colors`三个`属性`(`attribute`)，`name`属性是个`字符串` (`string`)，`version`属性是`数字`(`number`)，`colors`属性又是一个`块`。

### 数据类型
NeoLang 提供四种内建数据类型，分别是：
* `String` 字符串
* `Number` 数字
* `Block`  块
* `Array`  数组

**注意**：NeoLang 不支持用户自定义数据类型

##### String 字符串
NeoLang 中的字符串支持两种写法：
* 无空格分隔的单个字符串，**不需要**用引号包围，即 `x: hello` 和 `x: "hello"` 是等效的
* 如果字符串中含有空格，**必须**用引号包围，即 `x: "hello world"` 是合法的，但 `x: hello world` 是非法的

##### Number 数字
NeoLang 中的数字类型都是双精度浮点型 (`double`)
NeoLang 支持以下数字字面量：
* 人类使用的十进制，如 `123`, `456`, `3.14`
* `0x` 开头的16进制数字， 如 `0xA`, `0xbcd`
* `0` 开头的8进制数字，如 `0700`, `0644`
* `0b` 开头的二进制数字， 如 `0b1110`, `0b0010`

**注意**: NeoLang 仅允许在十进制字面量中出现小数点

##### Block 块
NeoLang 中的`块`就是一组属性的集合，允许在块中定义任何类型的属性，一个块应由一对大括号包围，如：
```css
empty-block: { }
```
```css
extra-keys: {
    key1: {
        display: Esc
        keyCode: <ESC>
    }
    key2: {
        display: Ctrl-Alt-C
        keyCode: <Ctrl>.<Alt>.C
    }
}
```

##### Array 数组
NeoLang 中的数组与Json中的极为相似，均使用 `[` 和 `]`作为数组的定义标志。数组中可以存放****除数组以外的任何数据类型****，即**不支持多维数组**。

下面是一个数组的例子:
```json
array: [1, 2, 3]
```
当然还可以这样：
```json
array: [hello, "hello world"]
```
NeoLang 是一门动态语言，这意味着你还可以这样：
```json
array: [1, "hello", {
    key: value,
    sub: [3, 1, 4]
}]
```

### 总结
NeoLang 不仅学习成本低，而且开放程度高。通过 NeoLang，NeoTerm 可以达到一个新的高度。
