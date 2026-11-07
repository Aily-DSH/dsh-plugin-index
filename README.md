# dsh-plugin-index

[![dsh-plugin](https://img.shields.io/badge/GitHub%20topic-dsh--plugin-3b82f6)](https://github.com/topics/dsh-plugin)

A tiny **DeepSeek Harness plugin-market index** (format 1) for the plugins maintained by [Aily-DSH](https://github.com/Aily-DSH).

DSH's in-client plugin market does not search npm: it only reads the index URLs you configure. Point `dsh.profile.indexes` at the jsDelivr URL below and the market page will list these plugins with their install targets.

## Use it

```yaml
# ~/.dsh/profiles/desktop/cordis.patch.yml (or your profile's patch file)
- id: plugin-market
  name: "@deepseek-ai/dsh-plugin-market"
  config:
    indexes:
      - https://cdn.jsdelivr.net/gh/Aily-DSH/dsh-plugin-index@main/index.json
```

Then restart DSH (or reload the profile) and open **设置 → 插件市场**.

## Plugins in this index

| Plugin | What it does |
| --- | --- |
| [dsh-peak-guard](https://github.com/Aily-DSH/dsh-peak-guard) | Warns before DeepSeek peak-priced hours, stops selected sessions, resumes them when off-peak pricing starts. |
| [dsh-sidebar-tab-close](https://github.com/Aily-DSH/dsh-sidebar-tab-close) | Double-click a right-sidebar tab to close it; Ctrl+W prefers the active sidebar tab over the window. |
| [dsh-quick-chat](https://github.com/Aily-DSH/dsh-quick-chat) | A row of quick-send chips in the composer: one click sends a saved phrase, up to ten editable presets stored locally. |
| [dsh-test-window](https://github.com/Aily-DSH/dsh-test-window) | Test windows always open on the display you pick in settings. |
| [dsh-session-usage](https://github.com/Aily-DSH/dsh-session-usage) | Per-conversation token usage (input / cache read / cache write / output) and estimated cost. |
| [dsh-superagent-manager](https://github.com/Aily-DSH/dsh-superagent-manager) | Manage several super-agent projects from one DSH client. |
| [dsh-approval-inbox](https://github.com/Aily-DSH/dsh-approval-inbox) | Turns blocking approvals into a background queue: requests wait in a sidebar inbox while the agent keeps working, approvals made in peak-priced hours run off-peak. |

## Format

`index.json` follows the format-1 contract of `@deepseek-ai/dsh-plugin-market-index`: top-level `format: 1`, localized `title` / `description`, declared `metadata.categories`, and a `plugins[]` array where every version pins an exact git commit.

Validate locally:

```bash
node -e "import('@deepseek-ai/dsh-plugin-market-index').then(m=>m.parseMarketIndex(require('./index.json'),'https://example.com/index.json'))"
```

## License

MIT
