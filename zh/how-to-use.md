## App 使用攻略

### 字体

使用双指缩放来放大或者缩小终端字号大小。  

在设置菜单中点击个性化选项，可以更换并预览你喜欢的字体和配色方案。

### 快捷键

`ctrl` `shift` `v` : 粘贴  
`ctrl` `shift` `z` : 切换到前一个会话  
`ctrl` `shift` `x` : 切换到下一个会话  
`ctrl` `shift` `n` : 新建会话  
`ctrl` `shift` `f` : 切换全屏  
`ctrl` `shift` `+` : 放大字体  
`ctrl` `shift` `-` : 缩小字体  

`alt` `<number>` : 切换到对应的会话  

### 特别说明
* 请**不要**用 `root` 用户或 `sudo` 执行**任何有关软件包**的操作
* 请不要尝试任何你不明白的命令

### 常见问题（FAQ）

#### 提示找不到 /bin/sh 或者 /usr/bin/env
两种方法:
* 使用软件自带的 execve() 包装器
 1. 打开 app
 2. 进入 设置 | 通用设置
 3. 勾选 "使用自定义的 execve()"
 4. 重启回话即可
* 修改脚本中的路径
 1. 安装 `neoterm-core`
 2. 执行 `neoterm-normalize-binary`（如： `neoterm-normalize-binary your_script.sh`）
 3. 重新执行你需要执行的脚本

#### dpkg 提示 no sh found in PATH
1. 新建一个会话
2. 执行 `cd ../usr/bin; ln -sf bash sh`
3. 重试运行 `dpkg`

#### 无法使用 ping 等基本命令
1. 安装 `neoterm-core`
2. 重试运行 `ping` 等
