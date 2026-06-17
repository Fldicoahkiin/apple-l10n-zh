---
name: apple-l10n-zh
description: Use this skill before translating any macOS or iOS app's interface into Simplified Chinese (zh-Hans / 简体中文) — even a single button or menu label. Don't translate Apple UI strings from general knowledge — Apple ships its own Chinese (Save = 存储 not 保存, Copy = 拷贝 not 复制, chart Series = 序列 not 系列, plus Finder, Force Quit, Sockets, Resident Memory…), and guessing reads as machine translation. Triggers on a .xcstrings, .xliff, or .xcloc file, filling in target translations, a zh-Hans translation PR for a Mac/iPhone app, Chinese for SwiftUI/Xcode buttons, menus, or labels, or keeping placeholders like %@, %lld, %1$@ intact. Provides Apple's official glossary, CJK punctuation and spacing rules, and a script for bulk target injection with placeholder-parity checks. Not for web/i18next/JSON localization, English copywriting or release notes, App Store screenshot uploads, or Simplified-to-Traditional script conversion.
---

# Apple App Localization → Simplified Chinese

Translate Apple-platform (macOS / iOS) UI strings into Simplified Chinese (zh-Hans) so the result reads like a native Apple app: Apple's official terminology, intact format placeholders, and the Xcode String Catalog file workflow. Output language is **zh-Hans**; the source is usually English but may be any language.

## When to use

- Editing a `<lang>.xliff` exported from an `.xcloc` localization catalog
- Adding zh-Hans values to a `.xcstrings` String Catalog
- Choosing the Apple-official Chinese term for a macOS/iOS UI concept

## File workflow (.xcloc / .xliff / .xcstrings)

An `.xcloc` localization catalog has two sides:

| Path | Role |
|---|---|
| `Source Contents/.../*.xcstrings` | English source snapshot — **read-only, never edit** |
| `Localized Contents/<lang>.xliff` | where translations go |

Translate by adding a `<target>` after each `<source>`:

```xml
<trans-unit id="Save" xml:space="preserve">
  <source>Save</source>
  <target>存储</target>
  <note from="auto-generated">A button that saves the current color setting.</note>
</trans-unit>
```

- A unit with no `<target>` falls back to the source at runtime — nothing breaks, so leaving a string untranslated is safe.
- Leave brand names and empty-source units alone (e.g. `CFBundleName`, copyright).
- The maintainer merges `<target>`s back into the real String Catalog with `xcodebuild -importLocalizations`. You only ever edit the xliff; never touch `Source Contents`.
- **Always read each unit's `<note>`** — it gives the real UI context and frequently decides the correct term.

## Hard rules

1. **Placeholders**: the target must keep the same set of format specifiers as the source — `%@`, `%lld`, `%d`, `%.1f`, `%u`, and positional `%1$@` / `%2$@`. Reorder with positional specifiers; never drop, add, or alter one. `进程 %A` is wrong; `进程 %@` is right.
2. **Don't translate code tokens**: CPU, GPU, QoS, PID, JSON, CSV, SSD, RAM, vmmap, dylib, plist, and signal names (SIGTERM / SIGKILL / SIGINT / SIGSTOP / SIGCONT).
3. **Markdown links**: translate the label, keep the URL unchanged — `[Documentation](https://…)` → `[文档](https://…)`.
4. **Punctuation**: full-width Chinese marks in Chinese text (：，。（）「」？！), but half-width for code tokens and their parentheses — `中断 (SIGINT)`, not `中断（SIGINT）`.
5. **CJK / Latin spacing**: one space between a Chinese run and an adjacent Latin word or number — `显示 CPU 使用率`, `vmmap 路径`. A standalone unit like `30s` stays `30s`.
6. **Apple terminology wins** over literal or Microsoft-Office translations. Verify against the live macOS UI or Apple's zh-CN docs. See [reference/terminology.md](reference/terminology.md).

## Terminology

Pick the term Apple itself ships in Simplified Chinese, not a dictionary literal. A few high-frequency ones:

| English | zh-Hans | Watch out |
|---|---|---|
| Save | 存储 | not 保存 |
| Copy | 拷贝 | not 复制 |
| Finder | 访达 | |
| Force Quit | 强制退出 | |
| Inspector | 检查器 | |
| Sockets | 套接字 | |
| Resident Memory | 常驻内存 | RSS |
| Series (chart) | 序列 | Apple Numbers 数据序列 — not Excel 系列 |
| Documentation | 文档 | not 文稿 (that is the Documents folder) |

Full glossary with sources: [reference/terminology.md](reference/terminology.md).
The cases where the obvious translation is wrong: [reference/pitfalls.md](reference/pitfalls.md).

## Validation

After editing the xliff, run this loop until clean:

```
- [ ] XML is well-formed:      xmllint --noout <file>.xliff
- [ ] Placeholder parity:      each <target> has the same specifiers as its <source>
- [ ] Spot-check terminology:  against reference/terminology.md
```

For bulk work, `scripts/inject_targets.py` inserts `<target>`s from an id→translation JSON map and reports any placeholder mismatch. Run it, then run `xmllint`:

```bash
python3 scripts/inject_targets.py path/to/zh-Hans.xliff path/to/translations.json
xmllint --noout path/to/zh-Hans.xliff
```

See the script header for the JSON format.

## Sources

Authoritative references (Apple Style Guide, String Catalog docs, Activity Monitor / Numbers zh-CN guides) are in [reference/sources.md](reference/sources.md). Prefer the live macOS system UI and Apple's own zh-CN material over third-party blogs.
