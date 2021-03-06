# JNU-Thesis

**NOTE** 

There may be some incorrect information in the article. I hope i can correct error with you.  you can contact me with Email or PR

## Pull Request welcome:blush:

感谢 [Wang Xuerui](https://github.com/xen0n) 提供的 JNU-Thesis 模板，项目地址：https://github.com/xen0n/JNUthesis

本项目提供了一个用于排版江南大学学位论文的XeLaTeX模板。本项目是[南京大学学位论文模板 NJU-Thesis][njuthesis] 的移植。

[njuthesis]: https://github.com/Haixing-Hu/nju-thesis

目前该模板支持排版学士和硕士（学术型与专业型）的学位论文。

## 使用指南
推荐使用Latex+VSCode进行跨平台的开发

参考[`Guide.md`](./Guide.md)

## 功能特色

* 支持多种江南大学学位论文及相关材料的生成：
	- 学术型硕士：
		- 学位论文：`master` 选项
		- 盲审版论文：`master,blindreview` 选项
	- 专业型硕士：
		- 学位论文：`master,prodegree` 选项
		- 盲审版论文：`master,prodegree,blindreview` 选项
	- 学士：
		- 学位论文：`bachelor` 选项
		- 毕业设计：`bachelordesign` 选项，除“摘要”变为“设计总说明”之外与 `bachelor` 完全相同
		- 相关资料，外文资料翻译：详见 [`bachelor-related.tex`](./bachelor-related.tex)
		- 本科课程设计：`bachelorcoursework`选项，详见 [`bachelor-coursework.tex`](./bachelor-coursework.tex)
* 使用XeLaTeX作为排版引擎，论文源码需要使用UTF-8编码；
* 支持使用思源系列字体（`sourcefonts`选项）进行排版；
* 自动生成中文封面、中文摘要页、英文摘要页、独创性声明页等必需页面；
* 支持硕博学位论文终稿提交前替换独创性声明页，具体方法见下；
* 支持自动替换所有中文句号为英文句点，方便理工科论文排版：`replaceperiod` 选项。

## 注意事项

### 关于目录排版

不要让任何一级章节编号超过个位数，比如10章或者10节。实际上，良好的文章组织以及篇幅要求的存在，一般情况下不需要担心该情况发生；但以防万一。

由于宏包对目录排版的内部设置原因，实现如同Word模板一般的“章节编号与名称之间空一个半角空格”的效果较为困难，实际上该效果是以计算章节编号均为个位数情况下编号的最大长度模拟的。这意味着如果项目编号超长，该行编号与标题文字的间距即被破坏。


### 关于字体要求与等宽字体

**江南大学学位论文只能使用中易宋体与Times New Roman排版。** 实质上相当于本宏包唯一正确的字体选项为`winfonts`，`sourcefonts`等其他字体选项暂无用户尝试，请慎重使用。（这有可能使您不得不重新打印整份论文，造成经济损失；万一成功，请务必报告情况，以便我们更新此处提示！）

**本科生注意：查重系统要求文字可正常复制。鉴于`winfonts`选项的已知问题（见“支持环境”一节），可用`sourcefonts`或`adobefonts`选项专门为查重系统编译。**

该规定意味着任何其他字体均不能使用，包括等宽字体，这对排版程序代码等内容十分不利。本宏包作者及多位使用者均面临过类似的情况，事实证明江南大学许多学院的字体要求没有谈判空间（见下）。因此，本宏包**默认设置使等宽字体与衬线字体相同，使所有`\texttt`等命令实质上无效，以减少您提交论文时的困扰**。

虽然行内代码引用（如变量名、类名、函数/方法调用等）的字体无解，但大段代码引用仍然有可能利用等宽字体。您可以**开启`figure`环境**，将代码置于其中，并在环境中 **设置`\forcedtt`（或`\textforcedtt`）** 以强制选择等宽字体。这样一来，老师会以为等宽排版的代码属于某种形式的截图，而无视字体要求。除了引用代码时要使用“图X-X”这种较为不爽的形式之外，能够使用等宽字体排版代码，应该也属于一种妥协了吧。


确定正文不可使用其他字体的学院：

* 物联网工程学院
* 理学院
* 数字媒体学院


确定正文可少量使用其他字体的学院：

* 法学院（直接引语等情况）


### 硕博学位论文：替换独创性声明页

所有答辩流程结束之后，需要上传包含已签字独创性声明页面的终稿到系统中。为方便该需求，本宏包内置了相应支持，请按以下方法操作：

* 论文撰写时：使用 `\makeoriginalitypage` 命令生成独创性声明模板页；
* 答辩结束，准备提交终稿时：**单独打印**一页独创性声明模板页（重要！之后需要扫描或拍照后处理，胶装之后的页面就不方便了），按照要求与胶装版内的独创性声明一起签字；
* 制作待插入图片：
	- 使用扫描仪：直接使用输出图片；
	- 使用手机：
		- 尽量在良好光照下正对纸张拍照，尽量不要有阴影；
		- 将照片中纸张部分剪裁，宽高比固定为210:297（A4）。由于打印机像素密度较高，一般为300 dpi往上，建议保留区域大小至少为2480x3507（300 dpi）；
		- 用“阈值”等滤镜将图像二值化，缩小体积且方便打印；
		- 推荐保存为PNG格式，由于处理后图像为黑白且大片空白，JPEG的压缩算法既引起压缩噪点，又空间占用较大。
* 最后修改 `\makeoriginalitypage` 为 `\makeoriginalitypage{图片相对路径}`。

如此即可直接生成符合要求的终稿PDF文档，不必手工完成PDF页面的分离、合并等操作了。

## 可参考子项目
感谢 [mchen19](https://github.com/mchen19) 开源的江南大学本科毕业论文模板和Latex开发的答辩PPT

项目地址：https://github.com/JNUGroup/bachelor-thesis

## 支持环境

以下环境测试支持：

* 操作系统
	- Linux
	- macOS
	- Windows
* TeX 发行版
	- TeXLive
* VSCode 
        - 具体参考[`Guide.md`](./Guide.md)
* 字体选项
	- `sourcefonts`
	- `adobefonts`
	- `fandolfonts`

以下环境存在已知问题：

* TeXLive 2016，`winfonts` 选项：PDF 内文字复制粘贴乱码 



