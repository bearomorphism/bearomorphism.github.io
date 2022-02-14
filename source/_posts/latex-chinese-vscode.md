---
title: 如何使用 Vscode LaTeX Workshop 上用 xelatex 編譯出帶中文的文件
tags:
  - latex
  - vscode
date: 2022-02-14 15:12:15
---


> 早上好 Vscode, 現在我有 LaTeX, 我很喜歡 LaTeX.

這篇文章的目標是記錄如何用 Vscode LaTeX Workshop 成功用 xelatex 編譯有中文的文件。

每次我要用 LaTeX 編譯出帶有中文的文件，我都要偷看以前寫的作業，不然就是重新上網查一遍。但是網路資訊又很亂很雜要看好久，乾脆今天把懶人包整理下來，一勞永逸。

## 環境設置

首先先安裝好 [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)

這個插件有好幾個優點，其中我最中意的優點是：在儲存時會自動編譯出 PDF 檔案 (build LaTeX (including BibTeX) to PDF automatically on save)

![Cool gif](https://github.com/James-Yu/LaTeX-Workshop/raw/master/demo_media/preview.gif)

不過這裡預設的編譯器是 pdflatex, 然而有些我需要用的 package 要用 xelatex 才可以編譯成功，例如 xeCJK

要解決這個問題很簡單，在 `settings.json` 中加入以下這一行，原因請見 references 中的 Stack Overflow 問答

```json
{
    ...
    "latex-workshop.latex.build.forceRecipeUsage": false,
    ...
}
```

接著在 tex 檔的第一行加入 [magic command](https://github.com/James-Yu/LaTeX-Workshop/wiki/Compile#tex-program-and-options)

```latex
% !TeX program = xelatex
```

最後 Ctrl + S 即會編譯出 PDF

![Image of editor](/images/2022-02-14-14-39-18.png)

這裡附上我使用的完整 tex 檔案

```latex
% !TeX program = xelatex

\documentclass{article}
\usepackage{xeCJK}
\setCJKmainfont{NotoSansCJK-regular.ttc} % 設定字體
\begin{document}

Et reprehenderit sunt consequat labore anim sunt qui eu cupidatat irure deserunt reprehenderit exercitation enim. Reprehenderit laboris Lorem amet ad minim dolor aute occaecat sit. Qui excepteur nostrud in sit.

早上好中国 \\
现在我有 bing chilling \\
我很喜欢 bing chilling \\
但是 \\
速度与激情9 \\
比 bing chilling \\
速度与激情 \\
速度与激情9 \\
我最喜欢 \\
所以…现在是音乐时间 \\
准备 1 2 3 \\
两个礼拜以后 \\
速度与激情9 \\
两个礼拜以后 \\
速度与激情9 \\
两个礼拜以后 \\
速度与激情9 \\
不要忘记 \\
不要错过 \\
记得去电影院看速度与激情9 \\
因为非常好电影 \\
动作非常好 \\
差不多一样 bing chilling \\
再见
\end{document}
```

## References

* [Enable xelatex in Latex Workshops for Visual Studio Code](https://stackoverflow.com/questions/56109128/enable-xelatex-in-latex-workshops-for-visual-studio-code)
