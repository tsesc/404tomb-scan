# 404Tomb Scan

[English](README.md) | [繁體中文](README.zh-TW.md)

404Tomb Scan 是一個 coding agent 技能，在你投入時間開發新想法之前，自動掃描 [404tomb.com](https://404tomb.com) 上 1000+ 個已死亡的網路產品資料庫。

## 運作方式

當你描述一個新的創業想法時，你的 coding agent 不會直接開始寫程式。它會先檢查 [404tomb.com](https://404tomb.com) — 一個記錄失敗網路產品的數位墓園 — 尋找已經死亡的類似想法。

技能會從你的想法生成多組搜尋關鍵字，同時查詢 404tomb API，然後用語意判斷過濾掉誤報。對每個相關的匹配結果，它會報告該產品做了什麼、存活了多久、以及你能從它的失敗中學到什麼。

列出匹配結果後，它會綜合分析類似失敗的模式，並提供差異化機會 — 你的想法可以如何避免相同命運的具體建議。每次掃描都以判定結束：**safe（安全）**、**proceed with caution（謹慎前進）** 或 **graveyard is full of these（墓園裡滿是這類產品）**。

因為這個技能在你腦力激盪時會自動觸發，你不需要做任何特別的事。你的 coding agent 就是知道要先查墓園。

## 安裝

**注意：** 安裝方式因平台而異。Claude Code 和 Cursor 有內建的 plugin marketplace。Codex、OpenCode 和 Gemini CLI 需要手動設定。

### Claude Code（透過 Plugin Marketplace）

在 Claude Code 中，先註冊 marketplace：

```bash
/plugin marketplace add tsesc/404tomb-marketplace
```

然後從 marketplace 安裝 plugin：

```bash
/plugin install 404tomb-scan@404tomb-marketplace
```

### Cursor（透過 Plugin Marketplace）

在 Cursor Agent 聊天中安裝：

```text
/add-plugin 404tomb-scan
```

或在 plugin marketplace 中搜尋 "404tomb-scan"。

### Codex

告訴 Codex：

```
Clone https://github.com/tsesc/404tomb-scan.git to ~/.codex/404tomb-scan, then symlink the skills directory: mkdir -p ~/.agents/skills && ln -s ~/.codex/404tomb-scan/skills ~/.agents/skills/404tomb-scan
```

**詳細文件：** [.codex/INSTALL.md](.codex/INSTALL.md)

### OpenCode

告訴 OpenCode：

```
Clone https://github.com/tsesc/404tomb-scan.git to ~/.config/opencode/404tomb-scan, then symlink skills: mkdir -p ~/.config/opencode/skills && ln -s ~/.config/opencode/404tomb-scan/skills ~/.config/opencode/skills/404tomb-scan
```

**詳細文件：** [.opencode/INSTALL.md](.opencode/INSTALL.md)

### Gemini CLI

```bash
gemini extensions install https://github.com/tsesc/404tomb-scan
```

更新：

```bash
gemini extensions update 404tomb-scan
```

### 驗證安裝

啟動一個新的 session，描述一個創業想法（例如「我想做一個 AI 旅遊規劃器」或「來做一個冥想 app」）。Agent 應該會自動觸發 404tomb-scan 技能並報告類似的失敗產品。

## 內容

### 技能

- **404tomb-scan** — 對 404tomb.com 進行多關鍵字 API 搜尋，搭配語意過濾、模式分析和風險判定

### API 參考

技能使用以下 404tomb.com 端點：

| 端點 | 用途 |
|------|------|
| `GET /api/search/dead?category=all&q={keyword}&limit=500` | 依關鍵字搜尋已死亡產品 |
| `GET /api/tags` | 列出全部 181 個產品分類及數量 |
| `GET /api/products/filter?category={tagId}&limit=500` | 依分類標籤過濾 |
| `GET /api/stats` | 取得已死亡產品總數 |

## 更新

Plugin 更新時技能會自動更新：

```bash
/plugin update 404tomb-scan
```

## 授權

MIT License - 詳見 LICENSE 檔案。

## 支援

- **Issues**: https://github.com/tsesc/404tomb-scan/issues
- **Marketplace**: https://github.com/tsesc/404tomb-marketplace
