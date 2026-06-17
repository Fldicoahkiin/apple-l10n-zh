# Terminology: English → Simplified Chinese (zh-Hans)

Apple's official zh-Hans terms for common macOS/iOS UI concepts. When unsure, check the live macOS system UI or the Apple zh-CN guides in [sources.md](sources.md). Apple wins over literal or Microsoft translations.

## Contents
- Common actions
- App & menus
- Settings & appearance
- Processes & memory (Activity Monitor domain)
- Charts & data export (Numbers domain)
- Logs (Console domain)
- Signals
- Keep in English (code tokens)

## Common actions

| English | zh-Hans | Note |
|---|---|---|
| Save | 存储 | not 保存 |
| Copy | 拷贝 | not 复制 |
| Cut | 剪切 | |
| Paste | 粘贴 | |
| Delete | 删除 | |
| Cancel | 取消 | |
| Apply | 应用 | |
| Reset | 重置 | |
| Clear | 清除 | |
| Add… | 添加… | use the … ellipsis, not ... |
| Quit | 退出 | |
| Force Quit | 强制退出 | |
| Show in Finder | 在“访达”中显示 | Finder = 访达 |
| Check for Updates… | 检查更新… | |
| Export / Import | 导出 / 导入 | |

## App & menus

| English | zh-Hans | Note |
|---|---|---|
| About X | 关于 X | |
| Documentation | 文档 | not 文稿 |
| Settings / Preferences | 设置 / 偏好设置 | macOS 13+ uses 设置 |
| Inspector | 检查器 | |
| Release Notes | 发行说明 | |
| Shortcuts (app) | 快捷指令 | the Shortcuts app |

## Settings & appearance

| English | zh-Hans | Note |
|---|---|---|
| General | 通用 | |
| Appearance | 外观 | |
| Behavior | 行为 | |
| Theme | 主题 | |
| Widgets | 小组件 | |
| Cell | 单元格 | |
| Filter (search field) | 筛选 | the search action |
| Filter (saved rule object) | 过滤器 | the noun object |
| Highlight | 高亮 | |

## Processes & memory (Activity Monitor)

| English | zh-Hans | Note |
|---|---|---|
| Process | 进程 | |
| Thread | 线程 | |
| Memory | 内存 | |
| Resident Memory | 常驻内存 | RSS |
| Virtual Memory | 虚拟内存 | |
| Footprint | 内存占用 | |
| Page-ins | 页面调入 | |
| Wired Memory | 联动内存 | Apple official |
| Compressed | 被压缩 | Apple official |
| Swap Used | 已使用的交换 | Apple official |
| Sockets | 套接字 | |
| Signature | 签名 | code signature |
| Entitlements | 授权 | or keep "Entitlements" for dev audiences |
| Priority / Nice | 优先级 / Nice | keep Nice (Unix term) |

## Charts & data export (Numbers)

| English | zh-Hans | Note |
|---|---|---|
| Series | 序列 | Apple Numbers 数据序列 — not Excel 系列 |
| Value | 值 | |
| Time | 时间 | |
| Timeline | 时间线 | |
| Sample (data point) | 样本 | Instruments 样本列表; not 采样 (the act) |

## Logs (Console)

| English | zh-Hans |
|---|---|
| Category | 类别 |
| Subsystem | 子系统 |
| Sender | 发送者 |
| Message | 消息 |

## Signals

| English | zh-Hans |
|---|---|
| Send Signal | 发送信号 |
| Terminate (SIGTERM) | 终止 (SIGTERM) |
| Kill (SIGKILL) | 强制终止 (SIGKILL) |
| Interrupt (SIGINT) | 中断 (SIGINT) |
| Pause (SIGSTOP) | 暂停 (SIGSTOP) |
| Resume (SIGCONT) | 继续 (SIGCONT) |

Keep the `(SIG…)` token half-width with a leading space.

## Keep in English (do not translate)

CPU, GPU, QoS, PID, JSON, CSV, SSD, RAM, URL, vmmap, dylib, plist, Info.plist, Nice (Unix), and all `SIG*` signal names.
