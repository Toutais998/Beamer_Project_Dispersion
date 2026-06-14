# Beamer Object Slides

这是一个关于光学像差诊断、显微物镜结构演化、Zemax 设计闭环和 Cousa 物镜仿真的 Beamer 项目。

## 主文件

- 编译入口：`slides.tex`
- 内容摘要：`slides_content.md`
- 章节源文件：
  - `Chapter/01.Chapter1.tex`：像差理论与诊断基础
  - `Chapter/02.Chapter2.tex`：物镜设计方法与 Zemax 闭环
  - `Chapter/03.ZemaxSimulation.tex`：物镜设计仿真案例分析

`Chapter/02.Zhang.tex` 保留为历史材料备份，但当前不再由 `slides.tex` 输入；其内容已经合并进第 2 章。

## 当前逻辑

```text
理想成像 -> OPD/波前 -> Ray Fan/Zernike -> 材料与色差
          -> 物镜结构约束 -> Zemax 优化与公差 -> Cousa 案例分析
```

这次整理把原先分散的像差页合并为几个连续模块：

- 球差、彗差、离焦统一按 Ray Fan 曲线阶次判断。
- 场曲和像散合并讲，重点区分最佳像面弯曲和子午/弧矢焦点分离。
- 阿贝图、色差、玻璃材料选择和 Zemax 玻璃替换放在同一段。
- 物镜设计历史并入 Zemax 前的结构选择逻辑，不再单独成章。
- Cousa 实际仿真章节暂不改主线，只补标签和引用框。

## 编译

建议使用 XeLaTeX：

```bash
latexmk -xelatex slides.tex
```

如果没有 `latexmk`，可使用：

```bash
xelatex slides.tex
xelatex slides.tex
```

项目使用 `xeCJK`，需要本机有 `SimHei`、`Microsoft YaHei` 和 `Times New Roman` 等字体。

## 标签规则

每个 section/subsection/frame 都已经补充 `\label`：

- 章/section：`\label{chap:1}`、`\label{chap:2}`、`\label{chap:3}`
- subsection：`\label{sec:1.1}`、`\label{sec:2.2}`
- frame：`\label{1.1}`、`\label{2.6}`、`\label{3.5}`

自动目录页由 `slides.tex` 的 `\AtBeginSection` 生成，并带有 `\label{toc:\thesection}`。

## 引用框

使用方式：

```tex
\framerefbox{Yu, C.-H. et al. Nature Methods 21, 132--141 (2024). DOI: 10.1038/s41592-023-02098-1}
```

原来的引用框放在 `background canvas` 中，可能被正文图片覆盖或受 Beamer 渲染时序影响。现在改为在 `footline` 阶段绘制，仍由当前 frame 内的 `\framerefbox{...}` 控制，显示更稳定。
