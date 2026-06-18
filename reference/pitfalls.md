# Pitfalls: where the obvious translation is wrong

Cases where a literal, habitual, or Microsoft-Office translation produces the wrong term. Each is a real correction.

## Series → 序列, not 系列

A chart's data series. Apple Numbers' zh-CN term is **数据序列** ("更改图表数据序列的外观"); the bare label is **序列**. Microsoft Excel uses 系列 — do not follow it. In Swift Charts this is the `.value("Series", …)` legend dimension, alongside `Value` (值) and `Time` (时间).

## Documentation → 文档, not 文稿

**文稿** is the Pages / iCloud "Documents" (我的文稿). Technical **Documentation** is **文档**.

## Filter → 筛选 or 过滤器, by context

- A search/filter **field** (an action) → **筛选**
- A saved **filter rule object** (a noun) → **过滤器**

Same English word, two different UI things; translating both the same way loses the distinction.

## Sample → 取样 / 样本 / 采样, by referent

Three different things, three terms — and in a process / Activity-Monitor-style app, a bare "Sample" is usually the **action**, not a data point:

- **Sample Process** (the command that captures a few seconds of a running process) → **取样** (Apple Activity Monitor: 取样进程 — "取样进程：创建所选进程在 3 秒内的报告。"). A standalone "Sample" button in a process tool is almost always this.
- A recorded **sample** (a data point / row) → **样本** (Apple Instruments 样本列表). "N samples recorded" → "已记录 N 个样本".
- **采样** is the act/process of sampling (a gerund) — e.g. "sampling rate" → 采样率.

A bare "Sample" with no `<note>` is ambiguous between 取样 and 样本 — flag it to the user, don't guess.

## Developer-facing terms with no shipped Apple UI string

Apple Developer documentation (developer.apple.com) is **English-only**, so capability / code-signing / API terms (Hardened Runtime, entitlements, QoS class names, dylib) have no *shipped-UI* zh-Hans to copy. That splits into two outcomes — don't lump them together:

- **No settled zh term at all → flag.** **Hardened Runtime** (the code-signing capability in a Process Details / signing inspector): community uses both 强化运行时 and 加固运行时, neither official and neither dominant. Verify the absence, then flag: present "keep English / 强化运行时 / 加固运行时" and let the user pick. Don't confuse it with the Apple *Platform Security* guide's 运行时保护 — that is the kernel's KIP/APRR protection, a different concept.
- **A settled WWDC rendering exists → use it, just cite provenance.** **QoS class names** (`QOS_CLASS_*`) → 用户交互 / 用户发起 / 实用工具 / 后台 / 默认, from Apple's WWDC subtitle localization. These are cached in terminology.md — **fill them directly, do not flag**; only note that the source is WWDC, not a shipped UI string, if asked.

The test is whether a single settled Chinese rendering exists, not whether it came from a shipped UI. Flag only when the term is genuinely unsettled (Hardened) — a confidently-filled *unsettled* term is the "looks decisive, reads as guessed" failure; reflexively flagging a *settled* one (QoS) just nags the user.

## Resident Memory → 常驻内存

RSS = Resident Set Size = 常驻内存大小. Both 常驻内存 and 驻留内存 are understood; **常驻内存** is more common in zh tech writing.

## Save → 存储, Copy → 拷贝

Apple macOS uses **存储** (not 保存) and **拷贝** (not 复制). Finder → **访达**.

## "..." → "…"

Normalize three ASCII dots to a single ellipsis character `…`, matching Apple's UI.
