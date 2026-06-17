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

## Sample → 样本, not 采样

A recorded **sample** (a data point) is **样本** (Apple Instruments 样本列表). **采样** is the act of sampling. "N samples recorded" → "已记录 N 个样本".

## Resident Memory → 常驻内存

RSS = Resident Set Size = 常驻内存大小. Both 常驻内存 and 驻留内存 are understood; **常驻内存** is more common in zh tech writing.

## Save → 存储, Copy → 拷贝

Apple macOS uses **存储** (not 保存) and **拷贝** (not 复制). Finder → **访达**.

## "..." → "…"

Normalize three ASCII dots to a single ellipsis character `…`, matching Apple's UI.
