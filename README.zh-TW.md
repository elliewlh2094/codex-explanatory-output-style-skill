# Codex 解釋型輸出風格 Skill

**[English](README.md)** | 中文

## 簡介

`explanatory-output-style` 是一個 OpenAI Codex skill，用來在程式開發對話中加入簡短且實用的教學說明。當這個 skill 啟用時，它會引導代理（agent）在完成任務的同時，說明具體實作方案的選擇、本地設計模式、權衡因素，以及與目前程式碼庫直接相關的細節。

這個 skill 適合希望一邊完成開發工作、一邊理解實作理由的使用者。它會在程式撰寫前後插入簡短的 `★ Insight` 區塊，讓整個過程維持執行導向，同時保留足夠的設計說明。

## 功能

- 在開始撰寫程式碼前加入一個簡短的 `★ Insight` 教學區塊。
- 在完成程式碼後再加入一個 `★ Insight` 教學區塊。
- 將說明重點放在具體實作方案，而非泛用的程式設計理論。
- 在需要時說明設計模式（design pattern）與程式碼庫中的本地慣例。
- 說明權衡、設計決策，以及某個方案為何比其他方案更適合目前儲存庫。
- 優先指出與程式碼庫直接相關的細節，例如既有抽象、命名規則、模組邊界、狀態流與測試風格。
- 透過 `agents/openai.yaml` 啟用隱式呼叫，讓 skill 可以在 session 起始階段自動參與上下文建立。

## 格式範例

這個 skill 使用以下 `★ Insight` 格式：

```markdown
`★ Insight ──────────────────────────────────────`
- [說明實作方案的教學重點]
- [說明設計模式、權衡或程式碼庫細節的教學重點]
`─────────────────────────────────────────────────`
```

## 安裝方式

請將這個儲存庫建立成名稱是 `explanatory-output-style` 的 Codex skill 目錄。

### Project-scope 安裝方式

將此儲存庫複製到：

```text
.codex/skills/explanatory-output-style/
```

安裝後的目錄結構應包含：

```text
.codex/skills/explanatory-output-style/
  SKILL.md
  agents/openai.yaml
```

### User-scope 安裝方式

將此儲存庫複製到：

```text
${CODEX_HOME}/skills/explanatory-output-style/
```

如果 `CODEX_HOME` 尚未設定，請使用：

```text
~/.codex/skills/explanatory-output-style/
```

### 最後一步

完成複製後，重新啟動 Codex，讓 skill 能在新的 session 中被正確載入。
