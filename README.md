# latex
LaTeX从零开始完整指南：
## 入门
1.[overleaf快速入门](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes)
2.[PKU LaTeX网站](https://latex.pku.edu.cn)
3.[VsCode配置LaTeX教程](https://zhuanlan.zhihu.com/p/166523064)    
(这是我读了n多教程觉得最好的一篇，讲解了settings.json配置的原理)。
4. 注意：
  - 不要尝试清除aux/bib/bbl等编译产生的文件，在引用插图、图表、文献时这些文件有用处，所以clean设置为onFailed就好。
  - 对于配置，多阅读latex workshop插件的详细内容，都有解释。
  - 关于vscode插图：
      - A.首先下载Paste Image插件，该插件可以保证crtl+alt+v快捷键直接粘贴图片；
      - B.[创建一个文件夹存放图片。设置Paste Image快捷键粘贴图片默认存放位置](https://blog.csdn.net/javahighness/article/details/90454136?spm=1001.2014.3001.5506)
## 语法
关于LaTeX语法，学习了B站以下视频：

①[video1](https://www.bilibili.com/video/BV15x411j7k6/?spm_id_from=333.999.0.0&vd_source=db6edf094802fef6bc67dbf99244ba0c)

②[video2](https://www.bilibili.com/video/BV11h41127FD/?spm_id_from=333.999.0.0&vd_source=db6edf094802fef6bc67dbf99244ba0c)

③[video3](https://www.bilibili.com/video/BV1qa4y1v7my/?spm_id_from=333.999.0.0&vd_source=db6edf094802fef6bc67dbf99244ba0c)

[自己做的语法详细总结-包括插图、表格、参考文献、自定义命令等](https://github.com/cryingnow/latex.git)
## 文件保存
关于中文乱码，要将文件保存为utf8的格式。而vscode配置c++环境文件为GBK格式。所以在settings.json中应分别设置不同类型文件保存方式，参考 "[tex]": {
        "files.encoding": "utf8"
    },  的设置格式设置不同文件（比如.cpp）保存格式。

