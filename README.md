# Beamer Object Slides

这是一个围绕光学像差分析、显微物镜设计方法与 Zemax 仿真闭环整理的 Beamer 汇报项目。

## 主文件与目录

- 编译入口：`slides.tex`
- 内容说明：`slides_content.md`
- 章节源文件：
  - `Chapter/01.Chapter1.tex`：像差理论与诊断基础
  - `Chapter/02.Chapter2.tex`：物镜设计方法与 Zemax 闭环
  - `Chapter/03.Chapter3.tex`：物镜设计仿真案例分析

## 当前汇报主线

```text
理想成像
-> OPD / 波前误差
-> Ray Fan / Zernike 诊断
-> 色散与玻璃材料选择
-> 物镜结构与 Zemax 优化闭环
-> Cousa 物镜仿真案例
```

其中：

- 第 1 章负责建立像差分析语言，并把 OPD、PSF、Ray Fan、Zernike、阿贝图与材料选择连成一条线。
- 第 2 章负责把物镜历史、结构约束、规格定义、Zemax 评价函数与优化流程组织成设计闭环。
- 第 3 章保留 Cousa 物镜的实际仿真与结果对比，作为完整案例收束。

## 编译方式

建议使用 XeLaTeX：

```bash
latexmk -xelatex slides.tex
```

如果没有 `latexmk`，可以执行：

```bash
xelatex slides.tex
xelatex slides.tex
```

项目使用 `xeCJK`，需要本机安装 `SimHei`、`Microsoft YaHei`、`Times New Roman` 等字体。

## 标签规则

项目已为 section、subsection、frame 补充统一标签，便于交叉引用与后续维护：

- section：`\label{chap:1}`、`\label{chap:2}`、`\label{chap:3}`
- subsection：`\label{sec:1.1}`、`\label{sec:2.2}`、`\label{sec:3.1}`
- frame：`\label{1.1}`、`\label{2.6}`、`\label{3.5}`

自动目录页由 `slides.tex` 中的 `\AtBeginSection` 生成，并带有 `\label{toc:\thesection}`。

## 引用框说明

页面底部引用框的使用方式如下：

```tex
\framerefbox{Yu, C.-H. et al. Nature Methods 21, 132--141 (2024). DOI: 10.1038/s41592-023-02098-1}
```

当前引用框在 `footline` 阶段绘制，因此显示更稳定；位置也已向左微调，与页面左边界更贴齐。

## 维护建议

- 修改章节结构时，优先同步更新 `slides_content.md`。
- 新增页面时，保持 `section / subsection / frame` 标签编号连续。
- 若重新整理图片版式，建议每次调整后立即执行一次 XeLaTeX 编译检查溢出和分页变化。
