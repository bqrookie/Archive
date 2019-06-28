## 如何使用sublime编辑器运行python程序

* Tools —> Build System —> New Build System…
* 将下面的代码复制到该文件中，即“untitled.sublime-build”文件中，保存为“Python3.sublime-build”，当然你也可以保存为“Python.sublime-build”

###### 注意:__py路径自己改__

```
{ 
“cmd”: [“F:/softwares/Python27/python.exe”, “-u”, “$file”], 
“file_regex”: “^[ ]File \”(…?)\”, line ([0-9]*)”, 
“selector”: “source.python” 
}
```

* 完成以上设置之后，如果要运行Python文件，只需要使用快捷键CTRL + B就可以了，当然也可以点击以下命令，在命令窗口的下方看到运行结果。
    >Tools —>Build


* 注意
    >1、代码路径和环境变量的路径中不要带中文，对中文支持还不好。

    >2、写完程序后，需要先保存一下，才能够运行。运行时按ctrl+b或者tool-build


---
## sublimeREPL
*  为什么要安装sublimeREPL插件？
> 用sublime运行python，如果有 __input()__ 函数，ctrl+b是不能输入数据的

###### 至于插件请自行安装
*    自定义sublimeREPL快捷键(可以根据以下步骤)

 > Preferences-->Browse Packages-->SublimeREPL文件夹-->config文件夹-->Python文件夹-->Default.sublime-commands(以文本格式打开) 
 
*    得到类似于如下代码：
 ```
 [
    {
        "caption": "SublimeREPL: Python",
        "command": "run_existing_window_command", "args":
        {
            "id": "repl_python",
            "file": "config/Python/Main.sublime-menu"
        }
    },
    {
        "caption": "SublimeREPL: Python - PDB current file",
        "command": "run_existing_window_command", "args":
        {
            "id": "repl_python_pdb",
            "file": "config/Python/Main.sublime-menu"
        }
    },
    {
        "caption": "SublimeREPL: Python - RUN current file",
        "command": "run_existing_window_command", "args":
        {
            "id": "repl_python_run",
            "file": "config/Python/Main.sublime-menu"
        }
    },
    {
        "command": "python_virtualenv_repl",
        "caption": "SublimeREPL: Python - virtualenv"
    },
    {
        "caption": "SublimeREPL: Python - IPython",
        "command": "run_existing_window_command", "args":
        {
            "id": "repl_python_ipython",
            "file": "config/Python/Main.sublime-menu"
        }
    }
]
```
*    注意：这就是repl的配置文件，找到你需要的命令复制下来，粘贴到Preferences-->Key Bindings User

```
[
    {
            "keys": ["ctrl+alt+b"],//这是自己设的快捷键
            "command": "run_existing_window_command", 
            "args":
            {
                "id": "repl_python_run",  //要加_run
                "file": "config/Python/Main.sublime-menu"
            }
    }
]
```
*    最后记得保存

## 建议：
>    建议使用菜单栏View->Layout->Columns:2分成2个窗口显示，方便观察结果。这时候因为选择的窗口是第二个窗口了，所以要再次运行刚才的python文件必须先点击切换到刚才的python文件，再在菜单栏点击Tools->SublimeREPL->Python->Python-RUN current file。