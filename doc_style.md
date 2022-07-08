中文文档 (特别是 LaTex) 的写作规范。

本规范：

1. 从写[《BasicSR 入门教程》](https://github.com/XPixelGroup/BasicSR-docs)的过程中总结而来
1. 参考了[阮一峰的写作规范](https://github.com/ruanyf/document-style-guide)
1. 原则：
    1. 易读
    1. 风格统一

## 插件

使用 VSCode 编辑，善用插件帮助 format (主要是缩进)。

插件：[latex-formatter](https://marketplace.visualstudio.com/items?itemName=nickfode.latex-formatter)

注意：使用 latex-formatter 后，缩进是 Tab。为了统一，替换成4个空格。

## 标题

1. 除了章 (Chapter) 的题目外，节 (Section) 的标题分为3级。\section{}, \subsection{}, \subsubsection{}
1. 层级之间不要出现跳跃，即 \subsubsection{} 前需要有  \subsection{}。下面这个是不被允许的

    ```latex
    \section{}
    \subsubsection{}
    ```

1. section 后面一定要同时写上 label，方便其他章节引用

    ```latex
    \section{数据 (Data Loader 和 Dataset)}\label{code_structure:data}
    ```

1. 为方便编辑器中区分，section 和 subsection 加上注释线

    ```latex
    % ------------------------------------------------------------------------------
    \section{配置(Options)}\label{code_structure:config}

    % ----------------------------------
    \subsection{实验命名}\label{code_structure:name_convention}
    ```

1. 章节标题 (\section{}, \subsection{}, \subsubsection{}) 后空一行，方便编辑时区分

    ```latex

    % ------------------------------------------------------------------------------
    \section{配置(Options)}\label{code_structure:config}

    在这个章节，我们先简单介绍一下...
    ```

## 标点与空格

1. 我们的主体是中文写作，因此使用中文标点 (全角符号)。有几个特殊的：
    1. 为保持统一，括号使用英文标点。括号中的内容是中文，括号也用英文括号。因为括号在有的编辑器里面会“吃字”。英文括号前后需要空格，但如果括号后面接标点，则不需要

        ```latex
        常见数据 (dataset) 的定义在...
        有整体框架 (参见第4小节)，网络结构 (参见第5小节) 等。
        ```

    1. 如果整句为英文，使用英文标点。几个英语单词之间也可用英文标点 (这个是灵活的，主要看英语占比)。如果仅是英语单词结尾，使用中文标点

        ```latex
        小节标题使用 \section{}, \subsection{}, \subsubsection{}。
        ```

1. 英文单词前后空一格。但如果单词前后是标点符号，则不需要空格

    ```latex
    这个部分主要定义了 Dataset 和 Data Loader 文件
    包括图像读取、归一化 (normalization)、数据增强 (augmentation) 以及封装为 PyTorch Tensor。
    ```

1. 数字前后不用空格。数字后有英文单位，根据需要决定是否需要空格 (一般不需要)

    ```latex
    训练了1000K iterations。
    占用显存16GB。
    ```

1. 省略号：...或中文省略号均可
1. 其他标点符号例子 (修改自[阮一峰的写作规范](https://github.com/ruanyf/document-style-guide))

    ```latex
    句号和括号关系：关于文件的输出，请参照第1.3节 (见第26页)。
    并列词用顿号 (即使是英语单词)：科技公司有 Google、Facebook、腾讯、阿里和百度等。
    ```

1. LaTex 中的连接号和下划线

    ```latex
    {-}opt
    {-}{-}net
    \_arch.py
    ```

1. LaTex 中的波浪线

    ```latex
    $\sim$
    ```

## 列表

1. 列表末尾不用句号。LaTex 主要是 enumerate 和 itemize

    ```latex
    \begin{enumerate}
        \item 训练和 validation 的 data loader 的创建
        \item model 的创建
    \end{enumerate}
    ```

## 引用

1. section 后面一定要同时写上 label，方便其他章节引用。section label 按照 {chapter_name:section_name} 的方式写。
    a. 不要出现空格
    b. 下划线 _ 或者短划线 - 均可。推荐使用短划线，section name 和文件名保持一致，可使用下划线

    ```latex
    \section{数据 (Data Loader 和 Dataset)}\label{code_structure:data}
    ```

1. 。每一个 section 都给一个 label，方便其他章节引用。
比如：\section{目录解读}\label{getting_start:content-overview}
 a. 不要出现空格
 b.

1. 章节引用。编译后格式为：章节4.10：日志系统(Logger)

    ```latex
    章节\ref{code_structure:logger}：\nameref{code_structure:logger}
    ```

1. 小节引用。编译后格式为：第4.1小节

    ```latex
    第\ref{code_structure:overview}小节
    ```

1. 文章中提到其他小节或内容，一定要使用引用。方便读者进行点击跳转

## 图表
