# ncmtomp3

1.下载ncmdump-windows-amd64.exe
	[下载链接1](https://github.com/yoki123/ncmdump/releases) | [下载链接2](./ncmdump-windows-amd64.exe)	

2.在ncm文件目录创建bat文件,不会创建可以直接下载也行[下载链接]([https://github.com/bqrookie/Archive/blob/master/%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/ncmtomp3/ncmtomp3.bat](https://github.com/bqrookie/Archive/blob/master/学习笔记/ncmtomp3/ncmtomp3.bat))

```bash
@echo off&&setlocal enabledelayedexpansion

for %%i in (*.ncm) do (
call  ncmdump-windows-amd64.exe "%%i"
)
endlocal
```

**注意**：

​    以上两个文件是同ncm文件放在同一个目录，然后运行bat就行，bat的作用主要是利用命令批量转换，不用一个一个来搞

![result](./images/ls.bmp)
![result](./images/ls1.bmp)
![result](./images/doing.bmp)
![result](./images/end.bmp)

