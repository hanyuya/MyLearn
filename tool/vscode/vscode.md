## 快捷键

### **编辑器与窗口管理**

新建文件:   Ctrl+N

文件之间切换:   Ctrl+Tab

打开一个新的VS Code编辑器:    Ctrl+Shift+N

关闭当前窗口:   Ctrl+W

关闭当前的VS Code编辑器:   Ctrl+Shift+W

切出一个新的编辑器窗口（最多3个):   Ctrl+\

切换左中右3个编辑器窗口的快捷键:   Ctrl+1  Ctrl+2  Ctrl+3

### **代码编辑**

#### 1、格式调整

```
代码行向左或向右缩进:   Ctrl+[ 、 Ctrl+]

复制或剪切当前行/当前选中内容:   Ctrl+C 、 Ctrl+V

代码格式化:   Shift+Alt+F

向上或向下移动一行:   Alt+Up 或 Alt+Down

向上或向下复制一行:   Shift+Alt+Up 或 Shift+Alt+Down

在当前行下方插入一行:   Ctrl+Enter

在当前行上方插入一行:   Ctrl+Shift+Enter
```

#### 2、光标相关

```
移动到行首:   Home

移动到行尾:   End

移动到文件结尾:   Ctrl+End

移动到文件开头:   Ctrl+Home

移动到定义处:   F12

查看定义处缩略图(只看一眼而不跳转过去):    Alt+F12

选择从光标到行尾的内容:   Shift+End

选择从光标到行首的内容： Shift+Home

删除光标右侧的所有内容(当前行):   Ctrl+Delete

扩展/缩小选取范围： Shift+Alt+Right 和 Shift+Alt+Left

多行编辑(列编辑):   Alt+Shift+鼠标左键 或 Ctrl+Alt+Down/Up

同时选中所有匹配编辑(与当前行或选定内容匹配):   Ctrl+Shift+L

下一个匹配的也被选中:   Ctrl+D

回退上一个光标操作:   Ctrl+U

撤销上一步操作: Ctrl+Z

手动保存:   Ctrl+S
```

#### 3、重构代码

```
找到所有的引用:   Shift+F12

同时修改本文件中所有匹配的:   Ctrl+F2

跳转到下一个 Error 或 Warning:   当有多个错误时可以按 F8 逐个跳转
```

#### 4、查找替换

```
查找:   Ctrl+F

查找替换:   Ctrl+H
```

#### 5、显示相关

```
全屏显示(再次按则恢复):   F11

放大或缩小(以编辑器左上角为基准):   Ctrl +/-

侧边栏显示或隐藏： Ctrl+B

显示资源管理器(光标切到侧边栏中才有效):   Ctrl+Shift+E

显示搜索(光标切到侧边栏中才有效):   Ctrl+Shift+F

显示(光标切到侧边栏中才有效):   Git Ctrl+Shift+G

显示 Debug:    Ctrl+Shift+D

显示 Output:    Ctrl+Shift+U
```

#### 6、其他设置

```
自动保存：File -> AutoSave(中文界面下“文件”->“自动保存”) 或者 Ctrl+Shift+P，输入 auto
```

alt + shift + r ：重命名rename

shift + alt + f：格式化代码

Alt + Shift + A : 快速块注释

单行注释：Ctrl + / 或 先按CTRL+K，再按CTRL+U

取消单行注释：Ctrl + / 或 先按CTRL+U，再按CTRL+K

! ：html中生成骨架结构

## 界面

Ctrl+Shift+p ：打开命令面板

## 下载和安装VS Code

### 1、下载地址

https://code.visualstudio.com/

### 2、安装

## 初始设置

## 中文界面配置

- 首先安装中文插件：Chinese (Simplified) Language Pack for Visual Studio Code
- 右下角弹出是否重启vs，点击“yes”
- 有些机器重启后如果界面没有变化，则 点击 左边栏Manage -> Command Paletet...【Ctrl+Shift+p】
- 在搜索框中输入“configure display language”，回车
- 打开locale.json文件，修改文件下的属性 "locale":"zh-cn"

```json
{
    // 定义 VS Code 的显示语言。
    // 请参阅 https://go.microsoft.com/fwlink/?LinkId=761051，了解支持的语言列表。
  
    "locale":"zh-cn" // 更改将在重新启动 VS Code 之后生效。
}
```

- 重启vs

## 插件安装

为方便后续开发，建议安装如下插件（红色矩形框标记的插件）

![](https://github.com/hanyuya/MyLearn/blob/main/%E5%B7%A5%E5%85%B7/vscode/picture/vscode%E6%8F%92%E4%BB%B6%E5%AE%89%E8%A3%85.jpg)

## 创建项目

vscode本身没有新建项目的选项，所以要先创建一个空的文件夹，如project_xxxx。

然后打开vscode，再在vscode里面选择 File -> Open Folder 打开文件夹，这样才可以创建项目。

## 保存工作区

打开文件夹后，选择“文件 -> 将工作区另存为...”，为工作区文件起一个名字，存储在刚才的文件夹下即可

![](https://github.com/hanyuya/MyLearn/blob/main/%E5%B7%A5%E5%85%B7/vscode/picture/%E5%88%9B%E5%BB%BA%E9%A1%B9%E7%9B%AE%E4%BF%9D%E5%AD%98%E5%B7%A5%E4%BD%9C%E5%8C%BA.jpg)

## 预览网页

**以文件路径方式打开网页预览**

需要安装“**open in browser**”插件：

文件右键 -> Open In Default Browser

**以服务器方式打开网页预览**

需要安装“Live Server”插件：

文件右键 -> Open with Live Server

## 设置字体大小

左边栏Manage -> settings -> 搜索 “font” -> Font size

## 开启完整的Emmet语法支持

设置中搜索 Emmet：启用如下选项，必要时重启vs

![img](file:///D:/softwaredata/weizhi/Documents/temp/2bcc1734-b2d3-473b-9e8f-d6cc9cef9a89/128/index_files/259d6137-301e-4f0d-af44-a8bb226ed712.png)

## **在vs code中创建vue代码片段**

文件 =>  首选项 => 用户代码片段 => 新建全局代码片段/或文件夹代码片段：vue-html.code-snippets

**注意：制作代码片段的时候，字符串中如果包含文件中复制过来的“Tab”键的空格，要换成“空格键”的空格**

```json
{
    "vue html": {
        "scope": "html",
        "prefix": "vuehtml",
        "body": [
            "<!DOCTYPE html>",
            "<html lang=\"en\">",
            "",
            "<head>",
            "    <meta charset=\"UTF-8\">",
            "    <meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0\">",
            "    <meta http-equiv=\"X-UA-Compatible\" content=\"ie=edge\">",
            "    <title>Document</title>",
            "</head>",
            "",
            "<body>",
            "    <div id=\"app\">",
            "",
            "    </div>",
            "    <script src=\"vue.min.js\"></script>",
            "    <script>",
            "        new Vue({",
            "            el: '#app',",
            "            data: {",
            "                $1",
            "            }",
            "        })",
            "    </script>",
            "</body>",
            "",
            "</html>",
        ],
        "description": "my vue template in html"
    }
}
```

