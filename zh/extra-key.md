## 快捷键盘

NeoTerm 有丰富的自定义的选项，快捷键盘是其中之一。
无一例外，快捷键盘也使用了 [NeoLang](neo-lang.md) 作为配置文件语法

### 那些快捷键可以自定义？

在 NeoTerm 中，所有的快捷键盘都是自定义的（包括内置）

### 如何编写配置文件？

假定你已有 NeoLang 语言基础，如果没有，请先在左侧阅读 NeoLang 有关的文档。
我们以一个简单的例子来说明

```json
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