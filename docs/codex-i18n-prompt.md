# [ARCHIVED] Codex Task: Add i18n to maple-benefits

> **Status: Completed in v1.3**
> This file was the original task specification used to implement bilingual (EN / 中文) support.
> It is kept for historical reference only. The translation keys and architecture described here
> may be outdated — the source of truth is the `T` object in `index.html`.

## What was implemented

- `LANG.current` + `t(key, vars)` — unified translation function with `{placeholder}` support
- EN default, 中文 toggle, persists in `localStorage` under key `'lang'`
- Language switch calls `navigate(currentPage)` for full re-render (no DOM patching)
- Status values stored as internal keys (`'unaware'`, `'aware'`, `'applied'`, `'receiving'`, `'ineligible'`) — never translated strings
- `statusLabel(key)` helper converts internal key → current-language display string
- `desc_en` and `conditions_en` fields added to all BENEFITS entries

## Key divergences from original spec

| Original spec | Actual implementation |
|---|---|
| `status_heard` key | Renamed to `status_unaware` |
| `checklist_*` keys | Checklist feature removed (replaced by Next Actions panel) |
| `renderPage()` after `setLang()` | `navigate(currentPage)` used instead |
| STATUS stored as translated strings | STATUS stored as internal keys (lang-safe) |
| `nav_diagnosis` key | Renamed to `nav_advisor` |
