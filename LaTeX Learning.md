# 十二分钟入门篇（语法）
## 基本信息
排版功能极强的神器：将内容与文档分开来。
## texlive和overleaf
### texlive:文本编辑器
## 语法
注意：每一个命令前都有==反斜杠==！
### title命令
1. 所有命令都以反斜杠开头，花括号（命令参数，比如article/beamer(幻灯片））在后面。
2. 使用中文：\docum[UTF8]{ctexart}。这支持中文和英文的混排。%%此方法好像不可用。%%
3. \usepackage{ctex}引入此宏包，才可处理中文。文件一定要以utf-8编码保存（vscode右下角可以修改)。
4. 位于\begin{document}之前的内容称作preamble(前言)，可以指定文档的格式、页面的尺寸、指定文档中需要导入的宏包。
5. 正文：begin和end中间。
6. 前言可以有：\title{文章的标题} \author{作者名字} \date{\today}。要显示这些信息，需要在文档的正文添加一个\maketitle命令。
### 格式化命令
1. \texbf{}：加粗文字；\textit{}：设置斜体；\underline{}:设置下划线；
2. 输入两个换行符：生成新的段落。（单独一个换行符生成空格）
3. \section{}：开启新的章节，花括号中代表章节的名字。 子章节（二级章节）：\subsection{}；三级章节：\subsubsection{}。
4. 对书籍排版：\documentclass{ctexbook}，则可以加入比section更大的\chapter{}；比chapter更大的是\part{}，通常表示书籍中的第几部。
5. 如果要在文档中添加图片，则需要在引言中引入宏包：\usepackage{graphicx}，在正文中可以用\includegraphics{}命令在当前位置添加一张图片（花括号是相对路径/绝对路径，注意保存图片到一个特定的文件夹中）,在花括号前加入[]里面存放参数：比如width=0.5\(除以)textwidth。
6. 如果要给图片添加标题，可以先将图片嵌套在一个figure环境中（如图），在中间可以通过\caption{}命令指定图片的标题（看来还是overleaf好用）,也可以通过\centering命令将图片居中显示。
7. 列表创建：
	 - 环境是LaTeX中的一个专用术语。任何介于\begin{}与\end{}中的所有内容都属于一个环境。
	 - 对于无序列表的创建，可以使用itemize环境(\begin{itemize})，列表中的每一个元素都需要以\item开头。
	 - 对于有序列表的创建，可以使用enumerate环境(\begin{enumerate})，列表中的元素同样需要以\item开头。
8. 对数学公式的排版：
	- LaTeX允许在段内直接加入公式，它们被称作行内公式，需要写在两个$之间，比如写入E=mc^2，将直接生成方程。
	- 如果希望将公式写在单独的一行，可以使用equation这个环境，可以将该环境简写为\[...\]的形式。
	- 对于复杂的公式，需要熟记公式中经常用到的一些指令。
		- \over代表几分之几，分子在前，分母在后。
		- \varphi代表小写的phi符号，\phi代表大写的phi符号。
		- [在线LaTeX公式编辑器](https://www.latexlive.com/)，可以快速测试想要排版的公式，也可以快速查询公式的语法。
		- mathpix，扫描图片可以生成公式对应的LaTeX代码。
	- 当然，数学公式一般用mathpix。
9. 表格的用法：
	- 可以使用tabular环境在当前位置创建一个表格。
	-  此环境要求我们传入一个参数，用来指定表格的尺寸。比如{c c c}代表表格有三列，其中每一列的内容居中对齐。
	- 可以替换c为l来表示左对齐，r来表示右对齐。
	- begin与end区域中定义了表格中需要显示的内容。
	- 每一列的数据需要以&符号隔开，每一行的数据需要以双反斜杠分割。
	- 可以加入竖线{|c|c|c|}为表格添加竖直的边框，水平方向的边框则需要通过\hline命令添加。甚至可以输入两次hline（\hline\hline）来添加双横线的效果。
	- 如果需要单独指定每一列的宽度，可以将c改成p，并在花括号里输入列宽
	- 如果需要添加标题，可以将整个表格放在一个table环境里，可以通过\caption{}命令指定表格的标题，并通过\center{}命令将表格居中显示。
# 系统学习
## 一.环境的安装与配置
必备：texlive。
教程用的编译器：TeXStudio
## 二.源文件的基本结构
### 摘要
abstract为其环境，比如：
```tex
\begin{abstract}
This is a simple paragraph at the beginning of the 
document. A brief introduction about the main subject.
\end{abstract}
```
### 分区
正文区和导言区。
导言区可以设置author、title、date。
正文区`\maketitle`使得导言区的设置生效。
### 分段
不同段之间用==换行==隔开，或者在一行最后使用`\\`（换行的效果），或者使用`\par`。
### 数学模式
  `$`符号表示行内数学模式，输入数学公式。
  `$$`符号表示行外数学模式，会自动占据一行。
## 三.中文处理办法
### 乱码解决
\usepackage{ctex}引入此宏包，才可处理中文。文件一定要以utf-8编码保存（vscode右下角可以修改)。可以直接在文字的前面设置字体，比如\kaishu
### equation
一种环境，可以写行外==带编号==的数学公式。
### ctex
在cmd中输入texdoc ctex，可以查看ctex宏集手册，了解用法。
比如：
```
\documentclass{article}
\usepackage{ctex}
```
与 \documentclass{ctexart}是一致的。
还有ctexbook/ctexreport等。
### texdoc
通过Texdoc可以查看texlive中的任意一个文件，比如可以查看texdoc lshort-zh(一份不太简短的latex介绍文档)。 
## 四.字体字号设置
### 字体属性
#### 1.字体编码
1. 正文字体编码：OT1/T1/EU1...
2. 数字字体编码:OML/OMS/OMX...
#### 2.字体族
1. 罗马字体：笔画起始处有装饰
2. 无衬线字体：笔画起始处无装饰
3. 打字机字体（等宽字体）：每个字符宽度相同
对应：
```
\textrm{文本}%罗马字体
\textsf{文本}%无衬线字体
\texttt{文本}%打字机字体
```
或
```
\rmfamily try
\sffamily try
\ttfamily try
```
可以用大括号对字体（示例为try）括住，声明字体的限制范围。如果不用大括号，则后续的文字皆为该字体族。
#### 3.字体系列
- 粗细：` \textmd{}`或`\mdseries`（可以在外面有大括号限制范围）。
- 宽度：`\textbf{}`或`\bfseriess`（可以在外面有大括号限制范围）。
#### 4.字体形状
- 直立:`\textup{}`或`\upshape`
- 斜体:`\textit`或`\itshape`
- 伪斜体:`\textsl`或`slshape`
- 小型大写:`\textsc`或`scshape`
#### 5.字体大小
```
{\tiny hello}\\
{\scriptsize hello}\\
{\footnotesize hello}\\
{\small hello}\\
{\normalsize hello}\\
{\large hello}\\
{\Large hello}\\
{\LARGE hello}\\
{\huge hello}\\
{\Huge hello}\\
```
输出hello的不同大小。
normalsize的大小是由文档类的参数决定的，比如
`\documentclass[10pt]/{article}`  一般只有10、11、12磅
#### 6.中文字体设置
- `{\songti} {heiti} {\fangsong } {\kaishu }`
- `\textbf() \textit()`
- 字号设置命令 \zihao{-0}更大一些，\zihao{5}更小一些。具体细节可以查看ctex文档。
#### 7.自定义
比如
`\newcommand{\myfont}{\textit{\textbf{\textsf{Fancy Text}}}}`
那么就可以在正文利用myfont设置你自己的字体
`\myfont text`
## 五.文档的基本结构
### Article排版
#### 提纲撰写
`\section`：构建一小节：比如{引言小节},`\subsection`,`\subsubsection`等诸如此类，完成==提纲==的撰写。
也可以使用ctexarticle这样的文档类来进行操作，此时section标题居中排版。
#### section格式设置
可以利用`ctexset{section={},subsection={}}`来对section等的格式进行设置。详细ctexset命令可以查阅ctex宏包手册。
### Book排版
`\chapter`产生章节的大纲。注意对应的文档类为book类，非article。而此时的subsubsection命令不起作用。还可以使用`tableofcontents`命令展示书本目录。
查阅ctex：直接在Windows搜索texdoc cetx，搜索格式设置。
==一定要养成内容与格式分离的习惯。==
## 六.特殊字符
### 1.空白符号
对于英文段落，如果在单词间添加n个空格，排版只会有一个空格；对于中文段落，不论添加几个空格，排版为PDF都不会出现空格；中英混排，在中文和英文之间会自动产生空格。
#### 空行空白
- 空行分段，多个空行等同一个。
- ==自动缩进，绝对不能使用空格代替。==
- 英文中多个空格处理为一个空格，中文中空格将被忽略。
- 汉字与其他字符的间距会自动由XeLaTeX处理。
- 禁止使用中文全角空格。
#### 打出空格
- `\quad`用来打空格，表示1em；`\\qquad`表示2em的空格。
- `a\,b`或`a\thinspace b`用来表示a与b之间1/6个em。
- `\enspace`表示0.5个em。
- `\ `表示空格。
- ~表示硬空格。
- `a\kern 1pc b` **or** `a\hskip -1em b` **or** `a\hspace{35pt}b` **or** `a\hphantom{xyz}b`表示指定宽度的空格。
- `a\hfill b`表示弹性长度，用于充满整个空间。
### 2.控制符
\#  \$   \%  \{   \}  \~  \{}  \_{}  \^{} \textbackslash  \&
是latex的控制符，前面加上反斜杠就可以在文章中加入，双反斜杠用反斜杠+textbackslash表示。
### 3.排版符号
![image.png](https://zhangzinuo.oss-cn-beijing.aliyuncs.com/img/202308202112797.png)
\S  \P \dag  \ddag  \copyright \pounds
这些符号，输出如上。（均有反斜杠）
### 4.标志符号
1. `\ Te{}  \LaTeX{}  \LaTeXe{}
2. 引入xltxtra宏包后，可以有`XeLaTeX{}`命令。
3. texnames宏包：`\AmSTeX{} \AmS-\LaTeX{} \BibTeX{}  \LuaTeX{}`
4. mflgo宏包：`\METAFONT{}  \MF{} \MP{}`
### 5.引号
左单引号：数字1左边的键。
右单引号：单引号字符。
左双引号：连续两个左单引号。
右双引号：连续两个单引号字符。
### 6.连字符
一个、两个、三个-：生成不同长度的连字符。
### 7.非英文字符
`\oe \OE \ae \AE \aa \AA \o \O \l \L \ss \SS 
!\`   ?\`|
结果如下：
![image.png](https://zhangzinuo.oss-cn-beijing.aliyuncs.com/img/202308202126567.png)
### 8.重音符号（以o为例）
\`o  \'o \^o \''o  \~o \=o \.o  \u{o}  \v{o} \H{o} \r{o} \t{o} \b{o}
\c{o} \d{o}(均有反斜杠在前)，结果为：
![image.png](https://zhangzinuo.oss-cn-beijing.aliyuncs.com/img/202308202131764.png)
## 七.插图
### 基本
宏包：graphix
语法：\includegraphics[<选项>]{<文件名>}
格式：EPS,PDF,PNG,JPEG,BMP
路径：\\graphicspath{{figures/}，{pics/}} 指的是图片在当前目录下的figures目录下的pics目录。
语法中直接输入文件名即可，因为已经指定了路径。
### 参数
[]内可选参数：
1. 缩放因子：scale=0.3/0.03...
2. 固定值的图像高度：height=2cm...
3. 图像宽度：width=2cm...
4. 版型文本高度倍数：height=0.1\\textheight（0.1倍）
5. 版型文本宽度倍数：width=0.2\\textwidth
6. 旋转角度：angle=-45...
### 环境figure
figure是插入图片可用的环境，创建\\begin,\\end的figure环境。
#### 位置
figure有个参数指定放置的位置，这一可选参数项可以是下列字母的任意组合。
- h 当前位置。将图形放置在 正文文本中给出该图形环境的地方。如果本页所剩的页面不够，这一参数将不起作用。
- t 顶部。将图形放置在页面的顶部。
- b 底部。将图形放置在页面的底部 。
- p 浮动页。将图形放置在一只允许 有浮动对象的页面上。
- 如果在图形环境中没有给出上述任一参数，则缺省为 [tbp]。
- 给出参数的顺序不会影响到最后的结果。因为在考虑这些参数时 LaTeX 总是尝试以 h-t-b-p 的顺序来确定图形的位置。所以 [hb] 和 [bh] 都使 LATEX 以 h-b 的顺序来排版。
- 给出的参数越多， LaTeX 的排版结果就会越好。 [htbp], [tbp], [htp], [tp] 这些组合得到的效果不错。
#### 标题
- \\caption{}表示标题。
- 其他控制，要引入宏包caption2：
	- \usepackage[选项]{caption2}
	- 选项参数有：
		- 标题样式
			- normal 标题文本两边对齐，其中最后一行为左对齐。
			- center 标题文本居中。
			- flushleft 标题文本左对齐。
			- flushright 标题文本右对齐。
			- centerlast 标题文本两边对齐，其中最后一行居中。
			- indent 与 normal 式样相似，只是标题文本从第二行开始， 每行行首缩进由命令 `\captionindent` 给出的长度。因为 `\captionindent` 的缺省值为零，通常用像 `\setlength{\captionindent}{1cm}` 这样的命令 来设置缩进值。
			- hang 与 normal 式样相似，只是标题文本从第二行开始， 每行行首缩进与标题标记宽度相等的长度。
		- 标题字号
		scriptsize,footnotesize,small,normalsize,large,Large
		- 标记字形
		up,it,sl,sc
		- 字体序列 mb,bf
		- 标记字族 sl,sf,tt
		- 单行标题 oneline,nooneline
#### 并列图形
多个图形并列于一个图形环境中，比如：
```tex
\begin{figure}
  \centering
  \includegraphics[scale=0.5]{d.jpg}
  \hspace{1in}
  \includegraphics[scale=0.5]{c.jpg}
  \caption{两张图片并排在一个浮动体}
\end{figure}
```
若想同时插入一组图片，共用一个大标题且为每张子图设小标题，要同时引入 \\usepackage{graphicx} 和 \\usepackage{subfigure} 宏包。比如：
```tex
\begin{figure}[htbp]
\centering
\subfigure[Fig1]{    
\includegraphics[scale=0.25]{Fig1.png} \label{1}
}
\quad
\subfigure[Fig2]{
\includegraphics[scale=0.25]{Fig2.png} \label{2} 
}
\quad
\subfigure[Fig3]{
\includegraphics[scale=0.25]{Fig3.png}\label{3}
}
\caption{Experimental results of the authors}
\end{figure}
```
代码说明：  
\subfigure[Fig1] 为子图的标题；  
\\caption{Experimental results of the authors} 为总标题。
### 手册
在电脑开始中查找texdoc graphix，即可得到graphicx的详细介绍。
### VsCode
使用了Paste Image插件，直接ctrl+alt+v便可以粘贴图片。也可以直接在保存图片时放入figures文件夹。注意figures要在图片路径中写入。
## 八.表格
- 环境：**tabular**，该环境需要在后面加入花括号设置表格参数，**l左对齐，c居中对齐，r右对齐**。在环境中编写表格的内容。
- 不同列之间用 **\&** 隔开。用`\\`结束本行。
- 可以在列之间竖线符号表示产生表格竖线，比如：
`\begin{tabular}{ | l | c| c|c|r |}`。可以用两个竖线符号产生表格双竖线
- 不同行之间使用`\hline`来产生表格横线。两个\\hline产生双横线。
- 在环境的参数中，可以在任何需要的地方添加表格线。
- 在列参数中，可以用**p{}** 产生制定参数的列宽，比如把上面例子中的r换成p{1.5cm}。当内容超过宽度时，会自动换行。
- 还有更多其他的三线表格等，都有对应的宏包，可以命令行运行texdoc booktab（三线表）、texdoc longtab（长表格）、texdoc tabu（综合表格），查看这些宏包的具体内容。
## 九.浮动体
要灵活实现对表格和插图的管理，需要使用浮动体。
### figure浮动体
将插图放入figure环境。——实现浮动
### table浮动体
将生成表格的tabular环境放入table环境中。
### 命令
- \\centering命令，实现居中排版。
- 通过可选参数 h t b p指定浮动体的排版位置，比如`\begin{figure}[htbp]`。
	- h：此处（here）
	- t：页顶（top）
	- b：页底（bottom）
	- p：独立一页（page）
- \\caption命令设置标题。详细：caption bicaption等宏包。
- \\label命令为浮动体设置标签。利用\ref命令可以引用标签，从而实现交叉引用。比如为其设置标签\\label{lion}（在\\caption后设置），在原文中如果用\ref{lion}，就可以实现交叉引用。
- 并排与子图表：subcaption subfig floatrow等宏包
- 绕排：picinpar  wrapfig等宏包。
### 示例
```tex
\documentclass{ctexart}

\usepackage{graphicx}
\graphicspath{{figures/}}%表示图片在当前目录下的figures目录
\usepackage{ctex}
%正文区
\begin{document}
	\LaTeX{}中\TeX 系统的吉祥物--小狮子见图\ref{fig-lion}
	\begin{figure}[htbp]%[htbp]表示浮动体的排版位置
		\centering%使得以下内容居中
		\includegraphics{two2.jpg}
		%\label命令为浮动体设置标签，\ref引用该标签
		\caption{\TeX 系统的吉祥物---小狮子}\label{fig-lion}
	\end{figure} 

在\LaTeX{}中也可以使用表\ref{tab-score}所示的表格
	\begin{table}[htbp]
		\centering
		\caption{成绩单}\label{tab-score}
			\begin{tabular}{|l| c| c| c|  r|}%会有5列，指定每列的居中形式,|表示每列中间有竖线分开
			\hline%每行之间由横线分开
			姓名&语文&数学&外语&政治\\%\\表示换行
			\hline
			张三&87&120&25&36\\
			\hline
			张1&87&120&25&36\\
			\hline
			张2&87&120&25&36\\
			\hline
		\end{tabular}
	\end{table}	
\end{document}
```
## 十.数学公式初步
LaTeX将排版内容分为文本模式和数学模式。
### A.行内公式 
#### 1.美元符号
\$ \$之间为数学公式。
#### 2.小括号
比如：`交换律是\(a+b=b+a\)`。
#### 3.math环境
比如：`交换律是 \begin{math}a+b=b+a\end{math}`。
### B.上下标
#### 上标
\^表示次方。如果是两位以上数，或一个式子，要用大括号，比如：
`$3x^{20}$`   `$3x^{3x^{20}-x+2}$`
#### 下标
\_实现下标
比如：`a_0` 多个字符时依然要用花括号。
### C.希腊字母
```tex
$\alpha$
    $\beta$
    $\gamma$
    $\epsilon$
    $\pi$
    $\omega$
    $\Gamma$
    $\Delta$
    $\Theta$
    $\Pi$
    $\Omega$
```
###  D.数学函数
```tex
$\log$
    $\sin$
    $\cos$
    $\arccos$
    $\arcsin$
    $\ln$
    $\sin^2x+\cos^2x=1$
    $\sqrt{2}$  %开方排版
    $\sqrt{x^2+y^2}$
    $\sqrt{2+\sqrt{2}}$
    $\sqrt[4]{x}$  %指定开方次数，这是x开4次方
```
### E.分式
```tex
大约是原体积的$3/4$
    大约是原体积的$\frac{3}{4}$ %两个花括号，分别代表分子/分母
  $\frac{\sqrt{x-1}{\sqrt{x+1}}$
```
### F.行间公式
#### 1.美元符号
双 `$$`符号
#### 2.中括号
`\[a+b=b+a\]`
#### 3.displaymath环境
```tex
\begin{displaymath}
        2x^2+5x+3=6
    \end{displaymath}
```
#### 4.自动编号公式equation环境
```tex
\begin{equation}
        a+b=b+a \label{test}
    \end{equation}
```
可以给公式用\\label命令添加标签，在其他位置就可以通过\ref引用这个标签，从而实现公式的交叉引用。
==公式的引用采用`\eqref`命令，页码的引用采用`\pageref`命令，图表以及其他引用，采用`\ref`命令。==
#### 5.不编号公式equation\*环境
注意：需要引入amsmath宏包。
```tex
\begin{equation*}%需要使用\usepackage{amsmath}
        a+b=b+a
    \end{equation*}
```
## 十一.数学公式矩阵
### 基础（matrix）
- matrix环境，与表格排版的tabular环境使用方法十分类似。\$分割列，`\\`分割行。
- 需要引入amsmath宏包。
- 换进begin与end前后要有\\[   和\\]。
- 也可以使用下划线和\^写上下标。
#### pmatrix
矩阵两端会有小括号。
#### bmatrix
矩阵两端中括号。
#### Bmatrix
矩阵两端大括号。
#### vmatrix
两端加单竖线。
#### Vmatrix
两端双竖线。
### 高阶
#### 省略号
\\dots \\vdots  \\ddots 右倾斜省略号需要自己创建。
比如：
```tex
\[
    \begin{bmatrix}
        a_{11}&\dots&a_{1n}\\
        &\ddots&\vdots\\
        0&\dots & a_{nn}
    \end{bmatrix}_{n\times n}
        \]
```
输出：
![image.png](https://zhangzinuo.oss-cn-beijing.aliyuncs.com/img/202308211825409.png)
#### 乘号
\\times表示乘号 比如n \times n表示n **x** n。
#### 分块矩阵（矩阵嵌套）
比如：
```tex
\[\begin{pmatrix}%分块矩阵(矩阵嵌套)
\begin{matrix}1&0\\0&1\end{matrix}
& \text{\Large 0}\\
\text{\Large 0}&\begin{matrix}
1&0\\0&1\end{matrix}
\end{pmatrix}
\]
```
输出：![image.png](https://zhangzinuo.oss-cn-beijing.aliyuncs.com/img/202308211830346.png)
此处的\\text命令用于切换到==文本模式==。
#### 三角矩阵
```tex
\[\begin{pmatrix}%三角矩阵
a_{11}&a_{12}&\cdots&a_{ln}\\
&a_{22}&\cdots&a_{2n}\\
&       &\dots &\vdots \\
\multicolumn{2}{c}{\raisebox{1.3ex}[0pt]{\Huge 0}}
&       &a_{nn}
\end{pmatrix}
\]
```
输出：![image.png](https://zhangzinuo.oss-cn-beijing.aliyuncs.com/img/202308211833988.png)
\\multicolumn命令合并多列，\\raisebox命令调整高度。
#### 跨列省略号
\\hdotsfor{<列数>}
```tex
\[\begin{pmatrix}%跨列的省略号：\hdotsfor{<列数>}
1&\frac 12 &\dots &\frac ln \\
\hdotsfor{4}\\
m&\frac m2& \dots &\frac mn
\end{pmatrix}
\]
```
输出：![image.png](https://zhangzinuo.oss-cn-beijing.aliyuncs.com/img/202308211836490.png)
注： latex中的省略号用\dots(横向...)或\vdots（竖向...）或\ddots（斜着的...）。分数表示：  \frac {分子}{分母}，也可以\frac 1 2，表示1/2，如果是1/20，需要\frac 1 2。
### 行内小矩阵
smallmatrix环境
```tex
复数$z=(x,y)$也可以用矩阵
\begin{math}
   \left(%需手动加上左括号
   \begin{smallmatrix}
  x& -y\\y&x
   \end{smallmatrix}
   \right)%需手动加上右括号
\end{math}来表示
```
输出：![image.png](https://zhangzinuo.oss-cn-beijing.aliyuncs.com/img/202308211839558.png)
### array环境
#### 简单
与tabular环境格式十分类似
```tex
\[
\begin{array}{r|r}
\frac 12&0\\
\hline
0& -\frac abc\\
\end{array}
\]
\end{document}
```
输出：![image.png](https://zhangzinuo.oss-cn-beijing.aliyuncs.com/img/202308211840490.png)
#### 复杂
array环境可以排版更为复杂的矩阵，此处不予说明。
## 十二.数学公式的多行公式
### 宏包
引入amsmath和amssymb宏包。
### gather环境
- 双反斜杠命令实现换行。
直接带编号。
- 在`\\`前使用\\notag可以阻止编号。
### gather\*环境
不带编号。
### align和align\*环境
公式排版中指定位置用&对齐，比如：
```tex
\begin{align}
        x &=t+\cos t+1\\
        y &=2 \sin t
    \end{align}
```
结果：![image.png](https://zhangzinuo.oss-cn-beijing.aliyuncs.com/img/202308211908511.png)
align\*环境没有编号。
### split环境
- 在euqtion环境中的环境（一个公式）。
- 对齐和align环境一样的方式，编号在中间。
```
\begin{equation}
    \begin{split}
    \cos 2x &=\cos^2 x- \sin^2 x\\
    &=2\cos^2 x-1
    \end{split}
    \end{equation}
```
![](https://zhangzinuo.oss-cn-beijing.aliyuncs.com/img/202308211911913.png)
### cases环境
- 每行公式中使用&分隔为两部分，对齐。
- 通常表示值和后面的条件。
```tex
\begin{equation}
        D(x)=\begin{cases}
        1,& \text{如果} x \in \mathbb{Q};\\
        0,& \text{如果} x \in \mathbb{R}\setminus\mathbb{Q}
        \end{cases}
    \end{equation}
```
输出：![image.png](https://zhangzinuo.oss-cn-beijing.aliyuncs.com/img/202308211913966.png)
`\in`命令用于输出**属于**符号，`\mathbb`命令用于输出花体字符，`\setminus`输出非集。
数学模式中的`\text`模式用于临时切换到文本模式。
## 十三.参考文献BibTex
- 一次管理，一次使用。
### thebibliography环境：
```tex
\begin{thebibliography}{编号样本}
  \bibitem[记号]{引用标志}文献条目1
   \bibitem[记号]{引用标志}文献条目2
...
    \end{thebibliography}
```
其中文献条目包括：作者、题目、出版社、年代、版本、页码等。比如：
```tex
\begin{document}
    \maketitle%使得导言区的设置生效
    引用一篇文章\cite{article1},引用一本书\cite{book1}
    \begin{thebibliography}{99}
        \bibitem{article1}马化腾，雷军，李彦宏，张一鸣.\emph{基于LaTex的Web数学公式提取方法研究}[J].计算机科学.2014(06)
        \bibitem{book1}Andy H,Bob,Cat,\emph{what does the fox say}
    \end{thebibliography}  
\end{document}
```
生成：
![image.png](https://zhangzinuo.oss-cn-beijing.aliyuncs.com/img/202308222206039.png)注意：
1. 引用要用`\cite{}`。花括号中是`\bibitem`花括号里设置的引用名字。
2. 文献名字在名字后面，要用`\emph{}`表示。
3. 也可以在参考文献中使用`\texttt{}`。花括号中可以是所在的网址等。
### 文件处理
将文献放置在==同一个文件==中，统一处理，便于排版。
1. 创建新文件，在新文件中填写文献的详细信息。例如：
```bib
@BOOK{mittelbach2004,  
title={腾讯传},  
publisher={广东教育出版社},  
year={2004},  
author={Frank Mittelbach and Michel Goossens},  
series={Tools and Techniques},  
address={广东},  
edition={First}  
}
```
**大括号**中第一个参数是引用标志，其他为title、publisher、year、author、series、address、edition等，每一个字段用**逗号**实现分割。每一对参考文献使用大括号进行分组。
2. 将文件保存为后缀名为.bib的格式。
3. 在导言区使用`\bibliographystyle{}`命令，指定参考文献的排版样式，可选的样式（写入大括号）有：`plain  unsrt  alpha  abbrv`。
4. 在正文需要写入（申明）参考文献的地方写入`\bibliography{}`，大括号内为参考文献数据库（可以省略.bib）。若有多个数据库，不同数据库之间用逗号分隔。
5. 在TEX工具的Build LaTeX project中选取**xelatex->biblatex->xelatex`*`2**的recipe方式（在settings.json）中可以自行配置。
6. 对于bib文件中的引用文献格式，最好：、
	- 可以去**google scholar**中搜索bibtex，搜索结果中有一个引用链接，点击打开。下方有一个BibTex链接，点击打开可以得到该文献的数据，可以直接将该数据复制过来修改成为你自己的文献内容。
	- 也可以去知网中获取文献格式，我们用**zotero**，打开zotero网站，获取文献，导出文献条目即可。
7. 如果要在参考文献列表中排版==未引用==的参考文献，需要使用`\nocite{}`命令，花括号中的参数为`*`，用于指定所有参考文献。在nocite命令中也可以指定特定的参考文献。
8. 如果有修改要重新编译生成PDF，==注意要先清理掉编译过程中产生的附加文件==。
9. 还可以通过`natbib`宏包指定不同的参数来设定不同的排版格式，比如 `\usapackage[round]{natbib}`。并且natbib宏包提供了`\citet`与`\citep`命令，用于实现不同的引用格式。
10. 更多功用查看相应宏包手册。
## 十四.参考文献BibLaTeX
略。
## 十五.自定义命令和环境
### \\newcommand
1. 命令只能由字母组成，不能以\\end开头。
2. `\newcommand<命令>[<参数个数>][<首参数默认值>]{<具体定义>}`为格式。
#### 简单字符串替换
比如：
```tex
\documentclass[10pt]{article}
\title{First Tex File}
\author{Andy}
\date{\today}
\usepackage{ctex}
\newcommand\PRC{People's Republic of \emph{China}}
\begin{document}
\PRC
\end{document}
```
#### 使用参数
参数个数可以从1到9，使用时用\#1,......\#9表示。
可以为参数设置默认值。
比如：
```tex
\newcommand\loves[2]{#1 喜欢 #2}%#1表示第一个参数，#2表示第二个参数
%整体就是参数一喜欢参数二
%参数采用位置参数，第二个传入的参数即为#2
\newcommand\hatedby[2]{#2 不受 #1 喜欢}
%\newcommand的参数可以有默认值
%指定参数个数的同时指定了首个参数的默认值
%第一个参数就成为你了可选的参数(要使用中括号指定)，比如：
\newcommand\love[3][喜欢]{#2#1#3}%[3]表示有3个参数，第一个参数的默认值是“喜欢”
%正文区
\begin{document}
\loves{猫}{鱼}
\hatedby{猫}{萝卜}
\love[最爱]{猫}{鱼}
\end{document}
```
结果：![image.png](https://zhangzinuo.oss-cn-beijing.aliyuncs.com/img/202308222337336.png)
比如最后的\\love中`[最爱]`使得最爱取代了“喜欢”成为第一个参数的默认值。
### \\renewcommand
重定义命令，与newcommand用法相同，但只能用于==已有==命令。
比如，可以`\renewcommad\abstractname{内容简介}`，重新定义了abstractname的内容，修改abstract环境的样式。
### \\newenvironment
renewenvironment与其语法一样:
`\newenvironment{<环境名称>}[<参数个数>][<首参数默认值>]{<环境前定义>}{<环境后定义>}`。
# 模板
## OverLeaf
## VsCode





