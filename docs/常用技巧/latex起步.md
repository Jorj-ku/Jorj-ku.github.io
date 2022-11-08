
# 前言：
>有模板最好  :joy:
>1. [国内高校模板](https://zhuanlan.zhihu.com/p/401278365)
>2. [英文免费模板](http://www.latextemplates.com/)

# 1.TeX常用文档类型
- 对于英文，可以用   `book、article、beamer`；
- 对于中文，可以用   `ctexbook、ctexart` 和   `ctexbeamer`，这些类型自带了对中文的支持。
常用的有：
`article`(`ctexart`)排版科学期刊、演示文档、短报告、程序文档、邀请函
`proc`一个基于article的会议文集类
`minimal`非常小的文档类。只设置了页面尺寸和基本字体。主要用来查错。
`report`(`ctexrep`)排版多章节长报告、短篇书籍、博士论文…
`Book`(`ctexbook`)排版书籍。
`slides`排版幻灯片。该文档类使用大号sans serif字体。也可以选用FoilTEXa来得到相同的效果。
>不同的文件类型，编写的过程中也会有一定的差异，如果直接修改文件类型的话，甚至会报错。以下统一选用`ctexart`。在编辑框第一行，输入如下内容来设置文件类型：

# 2.tex文档头部
`documentclass{ctexart}`或`\documentclass[UTF8]{ctexart}`
其中 UTF8 代表中文

>另外，一般也可以在\documentclass处设置基本参数，笔者通常设置 默认字体大小为12pt，纸张大小为A4，单面打印。需要将第一行的内容替换为：
>`\documentclass[12pt, a4paper, oneside]{ctexart}`

以下为代码示例：

```tex
\documentclass[12pt, a4paper, oneside]{ctexart}

\begin{document}            %文件的正文部分需要放入document环境中，在document环境外的部分不会出现在文件中。

这里是正文. 

\end{document}
			
```
# 3.  宏包
  - 为了完成一些功能（如定理环境），还需要在导言区，也即document环境之前加载宏包。加载宏包的代码是  `\usepackage{}`
  - 本份教程中，与 数学公式 与 定理环境 相关的宏包为：    `amsmath、amsthm、amssymb`；   
  用于插入图片的宏包为  `graphicx` 
  
>代码如下：
`\usepackage{amsmath, amsthm, amssymb, graphicx}`   
- 另外，在加载宏包时还可以设置基本参数，如使用超链接宏包  `hyperref`，可以设置引用的颜色为黑色等，
   
>代码如下：
`\usepackage[bookmarks=true, colorlinks, citecolor=blue, linkcolor=black]{hyperref}`
   
# 4.  标题
	
标题可以用  `\title{}`设置，    作者可以用  `\author`  设置，   日期可以用  `\date{}`设置，这些都需要放在导言区。
为了在文档中显示标题信息，需要使用  `\maketitle`  
例如代码：
```tex
\documentclass[12pt, a4paper, oneside]{ctexart}
\usepackage{amsmath, amsthm, amssymb, graphicx}
\usepackage[bookmarks=true, colorlinks, citecolor=blue, linkcolor=black]{hyperref}
% 导言区
\title{我的第一个\LaTeX 文档}
\author{Dylaaan}
\date{\today}
\begin{document}
\maketitle
  这里是正文. 
\end{document}
```

# 5.  正文
- 正文可以直接在`document`环境中书写，没有必要加入空格来缩进，因为文档默认会进行首行缩进。
- 相邻的两行在编译时仍然会视为同一段。
>在LaTeX中,        **另起一段的方式 : 使用一行相隔 ! ! !**在正文部分，多余的空格、回车等等都会被自动忽略，这保证了全文排版不会突然多出一行或者多出一个空格。
- 另外，另起一页的方式是：  `\newpage`
- 在正文中，还可以设置局部的特殊字体：

	| 字体 |	   命令  |
	| :------- | :------: |
	| 直立	  |          `\textup{}`
	| 意大利	|      `\textit{}`
	| 倾斜	       |      `\textsl{}`
	| 小型大写	     |    `\textsc{}`
	| 加宽加粗	      |   `\textbf{}`
# 6.  章节
对于ctexart文件类型，章节可以用` \section{} `和 ` \subsection{}  `命令来标记

 例如代码：
```tex
	\documentclass[12pt, a4paper, oneside]{ctexart}
	\usepackage{amsmath, amsthm, amssymb, graphicx}
	\usepackage[bookmarks=true, colorlinks, citecolor=blue, linkcolor=black]{hyperref}
	% 导言区
	\title{我的第一个\LaTeX 文档}
	\author{Dylaaan}
	\date{\today}
	\begin{document}
	\maketitle

	\section{一级标题}

	\subsection{二级标题}

		这里是正文. 

	\subsection{二级标题}

		这里是正文. 

	\end{document}
```

# 7. 目录
在有了章节的结构之后，使用   `\tableofcontents`   命令就可以在指定位置生成目录。
 >通常带有目录的文件需要编译两次！！！！！！！！！！！！！！！！！！！，           因为需要先在目录中生成.toc文件，再据此生成目录。

代码示例：
```tex
\documentclass[12pt, a4paper, oneside]{ctexart}
\usepackage{amsmath, amsthm, amssymb, graphicx}
\usepackage[bookmarks=true, colorlinks, citecolor=blue, linkcolor=black]{hyperref}

% 导言区

\title{我的第一个\LaTeX 文档}
\author{Dylaaan}
\date{\today}

\begin{document}

\maketitle

\tableofcontents

\section{一级标题}

\subsection{二级标题}

这里是正文. 

\subsection{二级标题}

这里是正文. 

\end{document}
```
# 8. 图片
注意：  插入图片需要使用`graphicx`宏包
建议使用如下方式：
```tex
\begin{figure}[htbp]
	\centering
	\includegraphics[width=8cm]{图片.jpg}
	\caption{图片标题}
\end{figure}      
```
 其中，`[htbp]`的作用是自动选择插入图片的最优位置，`\centering` 设置让图片居中，`[width=8cm]`设置了图片的宽度为8cm，
`\caption{}`用于设置图片的标题。
# 9. 表格
 LaTeX中表格的插入较为麻烦，   可以直接使用[Create LaTeX tables online – 网页表格编辑](https://www.tablesgenerator.com/)来生成。
 
 其他建议使用如下方式：
```tex
\begin{table}[htbp]
	\centering
	\caption{表格标题}
	\begin{tabular}{ccc}
	\hline
		1 & 2 & 3 \\
		\hline
		4 & 5 & 6 \\
		\hline
		7 & 8 & 9
	\end{tabular}
\end{table}
```

# 10. 列表


LaTeX中的列表环境包含  无序列表`itemize`、  有序列表`enumerate`和   描述`description`，  

以`enumerate`为例，用法如下：
```tex
\begin{enumerate}
	\item 这是第一点; 
	\item 这是第二点;
	\item 这是第三点. 
\end{enumerate}
```

另外，也可以自定义`\item`的样式：
```tex
\begin{enumerate}
	\item[(1)] 这是第一点; 
	\item[(2)] 这是第二点;
	\item[(3)] 这是第三点. 
\end{enumerate}
```

# 11. 定理环境
定理环境需要使用  `amsthm`  宏包，
		   
首先在导言区加入：
```tex
\newtheorem{theorem}{定理}[section]
```

>其中{theorem}是环境的名称，{定理}设置了该环境显示的名称是“定理”，[section]的作用是让theorem环境在每个section中单独编号。
在正文中，用如下方式来加入一条定理：
```tex
\begin{theorem}[定理名称]     %其中[定理名称]不是必须的。
	这里是定理的内容. 
\end{theorem}
```
此外，我们还可以建立新的环境，如果要让新的环境和`theorem`环境一起计数的话，可以用如下方式：
```tex
\newtheorem{theorem}{定理}[section]
\newtheorem{definition}[theorem]{定义}
\newtheorem{lemma}[theorem]{引理}
\newtheorem{corollary}[theorem]{推论}
\newtheorem{example}[theorem]{例}
\newtheorem{proposition}[theorem]{命题}
```
另外，定理的证明可以直接用`proof`环境。
# 12. 页面
   
最开始选择文件类型时，我们设置的页面大小是  a4paper  ，除此之外，我们也可以修改页面大小为  b5paper  等等。
一般情况下，LaTeX默认的页边距很大，为了让每一页显示的内容更多一些，我们可以使用  `geometry`宏包 ，并在导言区加入以下代码：
```tex
\usepackage{geometry}
\geometry{left=2.54cm, right=2.54cm, top=3.18cm, bottom=3.18cm}
```
另外，为了设置行间距，可以使用如下代码：
~~~tex
\linespread{1.5}
~~~

# 13. 页码
   
默认的页码编码方式是阿拉伯数字, 用户也可以自己设置为 小写罗马数字：
 
~~~tex
 \pagenumbering{roman}
~~~
>aiph 表示小写字母，   Aiph 表示大写字母，   Roman 表示大写罗马数字，  arabic 表示默认的阿拉伯数字。

如果要设置页码的话，可以用如下代码来设置页码从0开始：
~~~tex
\setcounter{page}{0}
~~~
  
# 14. 数学公式的输入方式
## 1. 行内公式
行内公式通常使用`$..$`来输入，这通常被称为公式环境，例如：
~~~tex
若$a>0$, $b>0$, 则$a+b>0$.
~~~
公式环境通常使用特殊的字体，并且默认为斜体。

需要注意的是，只要是公式，就需要放入公式环境中。
如果需要在行内公式中展现出行间公式的效果，可以在前面加入`\displaystyle`，
例如
```tex
设$\displaystyle\lim_{n\to\infty}x_n=x$.
```


## 2. 行间公式
行间公式需要用`$$..$$`来输入，笔者习惯的输入方式如下：
```tex
若$a>0$, $b>0$, 则
$$
  a+b>0.
$$
```
这种输入方式的一个好处是，这同时也是Markdown的语法。
>需要注意的是，行间公式也是正文的一部分，需要与正文连贯，并且加入标点符号。
关于具体的输入方式，可以参考在线LaTeX公式编辑器-编辑器 [妈咪叔latexlive]( https://www.latexlive.com/ )，

在这里只列举一些需要注意的：

- 上下标
  上标可以用  `^`  输入，例如 `a^n`，效果为$a^n$ ；下标可以用  `_`  来输入，例如  `a_1` ，效果为$a_1$ 。上下标只会读取第一个字符，如果上下标的内容较多的话，需要改成  `^{}`  或  `_{}`  。
  
- 分式
分式可以用\dfrac{}{}来输入，例如`\dfrac{a}{b}`，效果为 $\dfrac{a}{b}$。为了在行间、分子、分母或者指数上输入较小的分式，可以改用`\frac{}{}`，例如`a^\frac{1}{n}`，效果为 $a^\frac{1}{n}$。

- 括号
括号可以直接用(..)输入，但是需要注意的是，有时候括号内的内容高度较大，需要改用`\left(..\right)` 效果： $\left(..\right)$ 。例如  `\left(1+\dfrac{1}{n}\right)^n`，效果是 $\left(1+\dfrac{1}{n}\right)^n$。
在中间需要隔开时，可以用  `\left(..\middle|..\right)` *(效果：$\left(..\middle|..\right)$)*
另外，输入大括号{}时需要用  `\{..\}` ，其中  “\”  起到了转义作用。

- 加粗
  对于加粗的公式，建议使用bm宏包，并且用命令`\bm{}`来加粗，这可以保留公式的斜体。
  
- 大括号
  在这里可以使用`cases`环境，可以用于分段函数或者方程组，
  例如：
```tex
  $$
	f(x)=\begin{cases}
		x, & x>0, \\
		-x, & x\leq 0.
	\end{cases}
  $$
```
# 15. 多行公式
多行公式通常使用  `aligned`  环境，
		
例如
~~~tex
$$
	\begin{aligned}
	a & =b+c \\
	& =d+e
	\end{aligned}
$$
~~~
# 16. 矩阵和行列式
矩阵可以用  `bmatrix` 环境和 `pmatrix` 环境，分别为方括号和圆括号，例如
~~~tex
$$
\begin{bmatrix}
	a & b \\
	c & d
\end{bmatrix}
$$
~~~
如果要输入行列式的话，可以使用 `vmatrix` 环境，用法同上。
# 17. 文献添加  (不使用`BibTeX`)
先在文章末尾`(\end {document}`之前)写好需要插入的参考文献，逐一写出，例如：
~~~tex
\begin{thebibliography}{99}  
	\bibitem{ref1}Zheng L, Wang S, Tian L, et al., Query-adaptive late fusion for image search and person re-identification, Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, 2015: 1741-1750.  
	\bibitem{ref2}Arandjelović R, Zisserman A, Three things everyone should know to improve object retrieval, Computer Vision and Pattern Recognition (CVPR), 2012 IEEE Conference on, IEEE, 2012: 2911-2918.  
	\bibitem{ref3}Lowe D G. Distinctive image features from scale-invariant keypoints, International journal of computer vision, 2004, 60(2): 91-110.  
	\bibitem{ref4}Philbin J, Chum O, Isard M, et al. Lost in quantization: Improving particular object retrieval in large scale image databases, Computer Vision and Pattern Recognition, 2008. CVPR 2008, IEEE Conference on, IEEE, 2008: 1-8.  
\end{thebibliography}
~~~
上面列出了4个参考文献，`{thebibliography}`的选项99指的是参考文献的个数最大为99，可以设置为别的数。

在正文中引用参考文献的方法是：
~~~tex
\cite{ref1}
\cite{ref1, ref4}
~~~
