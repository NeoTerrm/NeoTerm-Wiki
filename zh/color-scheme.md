## 配色方案

NeoTerm 有丰富的自定义的选项，配色方案是其中之一。
无一例外，配色方案也使用了 [NeoLang](neo-lang.md) 作为配置文件语法

### 那些配色可以自定义？

在 NeoTerm 中，任何一种颜色都可以被自定义，这些颜色可以在 NeoTerm 源码中的 [TerminalColorScheme.java](https://github.com/NeoTerm/NeoTerm/blob/master/app/src/main/java/io/neoterm/backend/TerminalColorScheme.java) 中找到，共 256 种。

### 如何编写配色文件？

假定你已有 NeoLang 语言基础，如果没有，请先在左侧阅读 NeoLang 有关的文档。
我们以下面这个例子进行分析（该示例来自于[NeoTerm源码](https://github.com/NeoTerm/NeoTerm/blob/master/app/src/main/assets/colors/SolarizedDark.nl)中的部分）：
```css
color-scheme: {
    name: "Solarized Dark"
    version: 1.1

    colors: {
        background: #002b36
        foreground: #839496
        cursor: #93a1a1

        color0: #073642
        color1: #dc322f
        ...
    }
}
```

在上面的例子中，我们定义了一个全局块: `color-scheme`，在这个块之下，我们又定义了三个`字段`，它们分别是两个`属性`和一个`内部块`。
两个属性中一个是 `字符串`类型的 `name`，一个是 `数字`类型的`version`。内部块是 `colors`。
我们对每一个字段进行分析：

* *name*：配色方案的名字，这里是 `Solarized Dark`。这个名字会被展示在 NeoTerm 的个性化设置中
* *version*：配色方案的版本号，方便编写人员。不会被展示在 NeoTerm 中
* *colors*：配色方案的具体实现，定义需要的颜色，`colors`中的颜色名如下表所示:

|   属性名       | 说明           |
| ------------- |:-------------:|
|   background  | 背景颜色        |
|   foreground  | 文字颜色        |
|   cursor      | 光标颜色        |
|   color0      | 黑色            |
|   color1      | 红色           |
|   color2      | 绿色           |
|   color3      | 黄色           |
|   color4      | 蓝色           |
|   color5      | 洋红色          |
|   color6      | 青色           |
|   color7      | 白色           |
|   color8      | 亮黑色          |
|   color9      | 亮红色          |
|   color10     | 亮绿色          |
|   color11     | 亮黄色          |
|   color12     | 亮蓝色          |
|   color13     | 亮洋红色        |
|   color14     | 亮青色          |
|   color15     | 亮白色          |