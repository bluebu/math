---
description: 往「易错字本」(docs/易错字本.html) 增加或修改一个生字（田字格 + 拼音 + 组词 + 易错提醒 + 描红）。用户说「加个字 / 这个字也记上 / 改 X 字的提醒」时用。
user-invocable: true
---

# 增加 / 修改 易错字本里的生字

所有生字都在同一个文件：`docs/易错字本.html`。**一个字 = 一个 `<section class="zi">`**。

## 新增一个字

在最后一个 `<section class="zi">…</section>` 之后、`<footer>` 之前，复制下面整段，改这 **5 处**：
① 田字格正字　② 拼音 `py`　③ 组词 `word`　④ 易错提醒 `warn`　⑤ 描红格 `faint` 里的字（要和正字同步改成同一个字）

```html
  <section class="zi">
    <div class="top">
      <div class="tian show"><span>字</span></div>
      <div class="info">
        <div class="py">pīnyīn</div>
        <div class="word">组词：<b>词一</b> · <b>词二</b>（用法 / 答题场景）</div>
      </div>
    </div>
    <div class="warn">⚠️ 易错点：哪一笔 / 哪个部件容易写错，正确该怎么写。</div>
    <div class="plabel">练一练：</div>
    <div class="gridrow">
      <div class="tian show faint"><span>字</span></div>
      <div class="tian"></div><div class="tian"></div><div class="tian"></div>
      <div class="tian"></div><div class="tian"></div>
    </div>
  </section>
```

要点：

- 第 1 格 `tian show` = 黑色正字；描红格 `tian show faint` = 浅色字照着描；后面 5 个空 `tian` 留给孩子自己写。**正字格和描红格里的字必须一致**。
- 拼音标准声调（如 `zǒng`、`bèi`）。
- 组词贴近数学答题场景（例：总 → 总共 / 一共；被 → 被除数 / 被减数）。
- `warn` 写「**容易错在哪 + 正确写法**」，用三年级能懂的话（可点出偏旁、笔画，如「衤 衣字旁 5 笔，不是 礻 示字旁 4 笔」）。

## 修改一个字

定位该字的 `<section class="zi">`，改对应字段。**若改的是字本身**，记得正字格 `tian show` 和描红格 `tian show faint` 两处都要改。

## 完成后

`open docs/易错字本.html` 预览；用户说 **push** 才提交（本 repo 直接推 `master`）。
