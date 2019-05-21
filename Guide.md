# Latex+vscode编写江南大学毕业论文

## 简单介绍模板的使用<br/>

### 1. 下载软件
* Latex:&ensp; [官网](http://mirror.ctan.org/systems/texlive/tlnet/install-tl-windows.exe)&ensp;| 
&ensp;[清华镜像](http://mirror.ctan.org/systems/texlive/Images/texlive2018.iso)
### 2. 准备工作
工作区设置 <br/>
`> .vscode > setting.json > 工作区设置` ：
```tex
{
    "latex-workshop.latex.tools": [
        {
            "command": "latexmk",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdfxe",
                "%DOC%"
            ],
            "name": "Step 1: latexmk"
        }
    ],
    "latex-workshop.latex.recipes": [
        {
            "name": "toolchain",
            "tools": [
                "Step 1: latexmk"
            ]
        }
    ],
    "latex-workshop.view.pdf.viewer": "tab",
    "editor.renderControlCharacters": true,
    "workbench.activityBar.visible": false,
    "workbench.statusBar.visible": false,
    "workbench.startupEditor": "newUntitledFile",
    "editor.minimap.enabled": false,
    "explorer.confirmDelete": false
}
```
![工作区设置](/images/工作区设置.png)

### 3. 下载插件 <br/>
![插件下载](/images/插件下载.png)

### 4. 安装字体<br/>
下载字体点&ensp;[这里](https://pan.baidu.com/s/1UkZgWqMfpaEyr4V9vWa46g) &ensp;密码: agsv
<br/>
安装字体将文件移进`>C:/windows>Font`目录下即可。
<br/>
安装完后，确定可以使用的字体有adobefonts和fandolfonts，个别字体如winfonts从PDF复制会出现乱码。
### 5. 加载文件<br/>
最后一步，将本目录下的doc加载到vscode里面.<br/>
ctrl+s即可编译

所需要的所有文件在&ensp;[这里下载](https://pan.baidu.com/s/1pwQXA7vA_jxGatDzEBTKpA) &ensp; 密码: adnb <br/>
有编译错误的请自行baidu,google都可以找到解决方法，可以参考latex教程，一些常见的问题也可以参考[这里](https://github.com/xen0n/JNUthesis/issues)