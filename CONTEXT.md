# 理財自動化專案 — CONTEXT.md
# Gary Huang（garyhuang868@gmail.com）｜台南
# 上次更新：2026-04-06
# ⚠️ 此檔案為 Public，金額數字請見 Claude Project 附件

---

## 👤 基本資訊
| 項目 | 內容 |
|------|------|
| 姓名 | Gary Huang |
| Email | garyhuang868@gmail.com |
| 地區 | 台灣台南 |
| 語言 | 繁體中文（台灣用語）|
| 電腦 | Windows，Python 3.14 |
| Claude 方案 | Max Plan |
| API Key | 環境變數 ANTHROPIC_API_KEY |
| Telegram Bot | @Gary_invest_bot，Chat ID：7393752765 |
| 環境變數 | TELEGRAM_TOKEN / TELEGRAM_CHAT_ID |

---

## 📁 Claude Project 附件（私密，含完整數字）
| 附件 | 內容 |
|------|------|
| 專案說明.md | 台股/美股持倉、保險、損益總覽 |
| 房產.xlsx | 台南公司房產 + 台北個人房產明細 |
| 基金.png | 旭源聯邦基金 + Gary個人基金 |
| 進度日誌.md | 開發進度記錄 |

---

## 🖥️ 系統架構（C:\投資報告\）

| 檔案 | 功能 | 狀態 |
|------|------|------|
| daily_report.py | 每日損益報告（yfinance 抓價）| ✅ |
| daily_report_v2.py | 整合版（呼叫所有模組）| ✅ |
| stock_analysis.py | 個股分析引擎 v2 | ✅ |
| market_summary.py | 市場動態摘要 | ✅ |
| dashboard.py | HTML 儀表板（黑色主題）| ✅ |
| notify.py | Telegram Bot 推播 | ✅ |
| insurance.py | 保險管理模組 | ✅（解約金待填）|
| setup_real_estate_fund.py | 房產/基金DB建立 | ✅ 2026-04-06 |
| query.py | 歷史查詢選單（含房產/基金）| ✅ 2026-04-06 |
| setup_db.py | 資料庫建立 | ✅ |
| investment.db | SQLite 資料庫 | ✅ |

### Google Sheets
- 檔案：portfolio_master
- API URL：https://script.google.com/macros/s/AKfycbwuymO33qI8m1dlRm9n93c6F80jqtWi_yi4WUpnz0lc56jMtngyejqtmQao-k7cnW83Xw/exec

### Windows 排程
- 任務：每日投資損益報告，每天 08:00
- 指令：python C:\投資報告\daily_report_v2.py

### SQLite 資料表
| 資料表 | 說明 | 狀態 |
|------|------|------|
| holdings | 台股/美股持倉 | ✅ |
| realized_pnl | 已實現損益 | ✅ |
| pledge_records | 質借紀錄 | ✅ |
| insurance | 保險記錄 | ✅ |
| daily_snapshots | 每日損益快照 | ✅ |
| transactions | 交易記錄 | ✅ |
| fx_rates | 匯率記錄 | ✅ |
| real_estate | 房產記錄（19筆）| ✅ 2026-04-06 |
| funds | 基金記錄（7筆）| ✅ 2026-04-06 |

---

## 📊 資產架構總覽（金額詳見 Project 附件）

### 台股持倉
- 質押帳戶：鴻海(227K股)、欣興、京元電、神達 → 聯邦銀行質借
- 一般帳戶：台積電、南亞科、聯發科（聯邦+玉山）、神達現股

### 美股持倉（IB 帳戶）
- PLTR / APLD / CRM / SOFI / ADBE

### 質借風險
- 銀行：聯邦銀行，利率 2.5%
- 目前維持率：190%（安全），警戒線 130%

### 保險（8張）
- 新光人壽、台新人壽×2、南山人壽、中國人壽、國泰人壽、香港匯豐×2
- ⚠️ 中國人壽三得利：2026-06-05 可贖回（~60天）

### 房產（詳見房產.xlsx）
**公司名下（台南+台中）**
- 懷石1、懷石2、多摩市、宇成NY、桂田磐古、404土地、420土地、404建物、420建物、元翰門

**個人名下（台北）**
- 民安街101/201/202/301、中山路、土城、法國經典、日月光、牡丹園

**重點數字：**
- 公司房產預估總值：NT$185,872,250，現欠 NT$54,335,964
- 個人房產預估總值：NT$123,240,000，現欠 NT$66,393,147
- 月租金合計：NT$284,520，年租金：NT$3,414,240

### 基金（詳見基金.png）
**旭源聯邦資產**（以旭源房貸質借）
- 洛克希德馬丁、JPM多重收益美對沖、富蘭克林新興國家
- 鋒匯新市債U美月配、富蘭克林公用事業A×2
- 損益合計：+NT$615,428

**Gary個人**
- 土銀美國消費基金IPO，損益 +NT$6,000

---

## 📈 開發待辦（優先順序）

| 優先 | 項目 | 說明 |
|------|------|------|
| 🔴 緊急 | 中國人壽評估贖回 | 2026-06-05 到期 |
| 🔴 緊急 | 填入各保單解約金 | 向各保險公司查詢 |
| 🟡 近期 | 更新 Windows 排程 | 改跑 daily_report_v2.py |
| 🟡 近期 | Dashboard 加入房產/基金區塊 | dashboard.py 擴充 |
| 🟢 之後 | 歷史損益趨勢圖 | DB 快照累積後 |
| 🟢 之後 | 美股 IB API 整合 | 自動讀取 IB 記錄 |

---

## 🔧 重要指令速查

```cmd
REM 每日報告
python C:\投資報告\daily_report_v2.py

REM 查詢（含房產/基金）
python C:\投資報告\query.py

REM 個股分析
python C:\投資報告\stock_analysis.py

REM HTML 儀表板
python C:\投資報告\dashboard.py

REM 更新 GitHub（每次對話後）
cd C:\Users\user\finance-context
copy /Y C:\投資報告\CONTEXT.md C:\Users\user\finance-context\CONTEXT.md
git add .
git commit -m "更新：YYYY-MM-DD"
git push
```

---

## 📝 Claude 操作規則
1. 所有回覆使用繁體中文（台灣用語）
2. 金額以台幣（NT$）為主，美金（USD）為輔
3. 程式有錯誤時，直接修好輸出新檔案，不要只給說明
4. 持倉/房產/基金更新時，同步給出 DB SQL 指令
5. 股票代碼：鴻海=2317、欣興=3037、京元電=2449、神達=3706、台積電=2330、南亞科=2408、聯發科=2454

---
*CONTEXT.md 為 Public，敏感金額請見 Claude Project 私密附件*
*上次更新：2026-04-06*
