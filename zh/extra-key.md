## 快捷键盘

NeoTerm 有丰富的自定义的选项，快捷键盘是其中之一。
无一例外，快捷键盘也使用了 [NeoLang](neo-lang.md) 作为配置文件语法

### 那些快捷键可以自定义？

在 NeoTerm 中，所有的快捷键盘都是自定义的（包括内置）

### 如何编写配置文件？

假定你已有 NeoLang 语言基础，如果没有，请先在左侧阅读 NeoLang 有关的文档。
我们以一个简单的例子来说明

```js
extra-key: {
    program: [ "vim", "vi", "neovim" ]
    with-default: true
    key: [
        {
            display: Quit
            code: ":q!"
        },
        {
            display: Esc
            code: "<Esc>"
        },
        ...
    ]
}
```
* 我们需要定义一个叫做 `extra-key` 的全局块来告诉 app，这里面的内容是用来定义快捷键的。

* `program` 属性是一个字符串数组，**任何快捷键配置都需要指定该属性，不可为空**，数组中的元素为**该快捷键配置文件允许在执行哪些程序时可用**，在这里为：运行 `vim`, `vi`, `neovim` 这些程序时，会在屏幕下方的快捷键盘栏里新增上面定义的快捷键。特殊：当 `program` 属性只有一个元素且值为 `default` 时，该快捷键配置为默认快捷键，实例见 `~/.neoterm/eks/default.eks`。

* `with-default` 属性用来表示**是否连同默认快捷键一起显示**，如果不指定，默认为 `true`

* `key` 属性是一个数组，定义快捷键，每个元素也是块，支持如下属性。

    * `display` 指定显示在快捷键栏中的字符，如果为空或未定义，则与 `code` 一致
    
    * `code` 快捷键的编码，不可为空，支持 **NeoTerm 键盘组合序列**

    * `with-enter` 发送 code 时是否一起发送回车键，默认为 `false`