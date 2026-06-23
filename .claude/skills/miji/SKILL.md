---
description: 新增或修改一份「计算秘籍」讲义（docs/ 下的 A4 打印 HTML），并登记到首页 index.html。用户说「加个秘籍 / 出一份 XX 秘籍 / 改 XX 讲义」时用。
user-invocable: true
---

# 增加 / 修改 计算秘籍讲义

调用本 skill = 要**新建**一份秘籍讲义，或**修改**已有的某一份。先判断哪种：

- 给的是新题型 / 新秘籍 → 走「新增」。
- 说「改 XX 讲义的 …」「这里写错了」→ 走「修改」（定位 `docs/<名字>-计算秘籍.html` 直接改）。

## 教学硬约束（务必遵守）

- 对象是三年级小学生，人教版 **2024 新版**下册；用算术方法、**不用代数方程**、不超纲。
- 核心打法：先提炼一句好记的「**秘籍**」（公式 / 口诀），再用它解真题、点易错点。
- 题目优先来自 `原始题集/`、`错题集/` 的真题（PDF 用 Read 的 `pages` 读，错题照片直接 Read）；没有再编贴近教材的。
- 判断题目所属单元，按 `CLAUDE.md` 里的 2024 新版单元表选标准解法。

## 新增步骤

1. 确定：题型 + 一句话秘籍 + 至少一道真题例题 + 所属单元。
2. 复制一份最接近的现有讲义作骨架，命名 `docs/<秘籍名>-计算秘籍.html`：
   - 通用版式 → `docs/求经过天数-计算秘籍.html`
   - 含竖式 / 数位的 → `docs/商中间末尾有0-计算秘籍.html`
3. **必守的页面约定**（从骨架继承，别删）：
   - `<head>`：favicon / apple-touch-icon / manifest 那组标签，**外加** `<meta name="robots" content="noindex, nofollow, noarchive">`（全站永不被搜索引擎录入）。
   - 顶部一行 `<div class="topbar screen-only">`：左 `‹ 返回秘籍本`（`.back`，href=`index.html`），右 `🖨️ 打印 A4`（`.printbtn`，`onclick="window.print()"`）。
   - **打印锁 A4**：`@page { size:A4; margin:0 }`，并在 `@media print` 里 `html,body{ width:210mm }`、`.sheet{ width:210mm; max-width:none; padding:..mm }`（边距写在 `.sheet` 上，用 mm）。否则移动端 / Epson 等会按手机窄宽度排版再缩放成「移动布局」。
   - `print-color-adjust:exact`、系统中文字体。
   - 结构顺序：秘籍公式框 → 生活化「为什么」 → 易错点 → 真题例题 → 小工具（如月份表 / 数位盒）→ 练一练（带答案，可倒排 + 裁切线）。`section{break-inside:avoid}`，长内容用 `.pagebreak` 分页。
4. 把正文替换成本次题型内容。
5. 在 `docs/index.html` 复制一张卡片模板，填 href、emoji、名称、公式、单元标签、记录日期 `data-date`（用今天的日期）。
6. `open docs/<文件>` 浏览器预览，并用 ⌘P 看一眼打印是否撑满 A4；请用户确认。

## 修改步骤

1. 定位 `docs/` 下对应讲义直接编辑。
2. 若改了名称 / 公式 / 记录日期，同步更新 `index.html` 里那张卡片。
3. `open` 预览。

## 完成后

用户说 **push** 才提交（本 repo 直接推 `master`，不走 PR / 分支）。
