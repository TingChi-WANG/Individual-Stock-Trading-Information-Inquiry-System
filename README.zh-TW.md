# 台灣個股交易資訊查詢系統

> 🇬🇧 [English version available here](./README.md)

透過 Python 自動查詢台灣證券交易所（TWSE）個股交易資料，並進行視覺化呈現的工具。

---

## 功能介紹

- 輸入台灣股票代碼，自動開啟 Firefox 並導向 TWSE 查詢頁面
- 透過 TWSE Open API 取得當月每日交易資料
- 將資料整理為結構化的 Pandas DataFrame
- 繪製**收盤價趨勢圖**
- 以樣式化表格呈現資料：
  - 收盤價套用藍色漸層背景
  - 漲跌價差正值標紅、負值標綠

---

## 使用技術

| 類別 | 套件 |
|------|------|
| 網頁自動化 | `selenium`, Firefox WebDriver |
| HTTP 請求 | `requests` |
| 資料處理 | `pandas`, `numpy`, `json` |
| 資料視覺化 | `matplotlib` |
| 其他 | `time` |

---

## 環境需求

- Python 3.x
- Firefox 瀏覽器
- [GeckoDriver](https://github.com/mozilla/geckodriver/releases)（需加入系統 PATH）
- 中文字型：`Taipei Sans TC Beta`（用於 Matplotlib 中文顯示）

### 安裝相依套件

```bash
pip install selenium requests pandas numpy matplotlib
```

---

## 使用方式

### 方式一：執行 Python 腳本

```bash
python "[Code] Individual-Stock-Trading-Information-Inquiry-System.py"
```

### 方式二：使用 Jupyter Notebook

開啟 `[Code] Individual-Stock-Trading-Information-Inquiry-System.ipynb`，逐格執行。

### 操作流程

1. 執行程式後，輸入台灣股票代碼（例如：`2330` 代表台積電）
2. 程式自動開啟 Firefox 並前往 TWSE 查詢頁面
3. 同時透過 TWSE API 取得當月每日交易資料
4. 輸出收盤價趨勢圖與格式化資料表

---

## 資料來源

台灣證券交易所（TWSE）Open API：

```
https://www.twse.com.tw/exchangeReport/STOCK_DAY?response=json&date={YYYYMMDD}&stockNo={股票代碼}
```

---

## 資料欄位說明

| 欄位 | 說明 |
|------|------|
| 日期 | 交易日期 |
| 成交股數 | 當日成交總股數 |
| 成交金額 | 當日成交總金額（新台幣） |
| 開盤價 | 當日開盤價格 |
| 最高價 | 當日最高價格 |
| 最低價 | 當日最低價格 |
| 收盤價 | 當日收盤價格 |
| 漲跌價差 | 與前日收盤價之差值 |
| 成交筆數 | 當日成交筆數 |

---

## 檔案結構

```
Individual-Stock-Trading-Information-Inquiry-System/
├── README.md                                                          # 英文版（主要）
├── README.zh-TW.md                                                    # 繁體中文版（此檔案）
├── [Code] Individual-Stock-Trading-Information-Inquiry-System.py      # Python 腳本版本
└── [Code] Individual-Stock-Trading-Information-Inquiry-System.ipynb   # Jupyter Notebook 版本
```

---

## 注意事項

- 本系統查詢的是**當月**交易資料，資料範圍依 TWSE API 回傳為準
- 需確保 GeckoDriver 版本與已安裝的 Firefox 版本相容
- 若 Matplotlib 無法正確顯示中文，請修改程式碼中的字型設定：
  ```python
  # 將此行：
  plt.rcParams['font.sans-serif'] = ['Taipei Sans TC Beta']
  # 替換為已安裝的中文字型，例如：
  plt.rcParams['font.sans-serif'] = ['Microsoft JhengHei']   # Windows
  plt.rcParams['font.sans-serif'] = ['PingFang TC']           # macOS
  ```

---

## 授權

本專案僅供學習與個人使用。資料來源版權歸台灣證券交易所所有。
