## 用户脚本

NeoTerm 提供了一种与文件交互的方式，即 “用户脚本”。通过用户脚本，用户可以很方便的调用 NeoTerm 的众多软件包来处理文件，如编译程序，解压压缩文件，编译文档等等...

### 如何使用？

在文件管理器中，通过 “分享” 或 “打开方式” 功能将文件用 “NeoTerm-用户脚本” 打开。然后在 NeoTerm 中选择使用的脚本，然后静待脚本执行完毕。

### 脚本位于哪里？

在 `~/.neoterm/script` 下可以找到所有可用的用户脚本
每次 NeoTerm 启动时，都会刷新用户脚本列表，所以不用担心编写了脚本但是 NeoTerm 却没有显示的问题。

### 可以自己编写脚本吗？

当然可以，就当成一般的 shell 脚本来编写即可。不过请注意: **在文件管理器中传入的文件会以参数形式传给用户脚本**，即在脚本中表示为：`$1`, `$2`...`$@`
更多关于shell脚本的编写技巧请查阅[此处](http://www.runoob.com/linux/linux-shell.html)


下面是一个解压文件的例子（支持 7z, rar, zip, tar），可以直接复制到 `~/.neoterm/script` 下 命名为 `extract-archive` 测试

```shell
#!/data/data/io.neoterm/files/usr/bin/bash

function file_suffix() {
    echo "${1##*.}"
}

function detect_program() {
    case "$1" in
        *.tar.* | *.tar ) echo "tar xvf %s" ;;
        *.7z )    echo "7za x %s" ;;
        *.rar )   echo "unrar x %s" ;;
        *.zip )   echo "unzip %s" ;;
        * )       echo "" ;;
    esac
}

function do_extract() {
    local file="$1"
    local dir="$(dirname $file)"
    
    if [[ ! -f "$file" ]]; then
        echo "$file: no such file or directory"
        return 1
    fi
    
    local program="$(detect_program $file)"
    
    if [[ "$program" == "" ]]; then
        echo "Unsupported format: $(file_suffix $file)"
        return 1
    fi
    
    local command="$(printf "$program" "$file")"
    
    if [[ ! -w "$dir" || ! -r "$file" ]]; then
        command="sudo $command"
    fi
    
    cd "$dir" || {
        echo "Failed to cd: $dir"
        return 1
    }
    
    eval "$command"
}

if [[ "$#" == 0 ]]; then
    echo "You must specific at least a file to extract."
    exit 1
fi

clear
while [[ "$#" != 0 ]]; do
    file="$1"; shift
    echo "[Extracting] $(basename $file)"
    do_extract "$file"
done
```