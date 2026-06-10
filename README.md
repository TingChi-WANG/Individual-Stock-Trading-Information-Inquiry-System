# Individual Stock Trading Information Inquiry System

> 🇹🇼 [繁體中文版說明請點此](./README.zh-TW.md)

A Python-based tool that queries daily stock trading data from the Taiwan Stock Exchange (TWSE) and presents it with charts and styled tables.

---

## Features

- Enter a Taiwan stock ticker to automatically open TWSE in Firefox
- Fetch current-month daily trading data via the TWSE Open API
- Parse and clean the response into a structured Pandas DataFrame
- Plot a **closing price trend chart**
- Render a styled table with:
  - Blue gradient background on closing price column
  - Red for positive price changes, green for negative

---

## Tech Stack

| Category | Libraries |
|----------|-----------|
| Browser Automation | `selenium`, Firefox WebDriver |
| HTTP Request | `requests` |
| Data Processing | `pandas`, `numpy`, `json` |
| Visualization | `matplotlib` |
| Utilities | `time` |

---

## Requirements

- Python 3.x
- Firefox browser
- [GeckoDriver](https://github.com/mozilla/geckodriver/releases) (must be in system PATH)
- Chinese font: `Taipei Sans TC Beta` (for Matplotlib CJK rendering)

### Install dependencies

```bash
pip install selenium requests pandas numpy matplotlib
```

---

## Usage

### Option 1 — Python script

```bash
python "[Code] Individual-Stock-Trading-Information-Inquiry-System.py"
```

### Option 2 — Jupyter Notebook

Open `[Code] Individual-Stock-Trading-Information-Inquiry-System.ipynb` and run cells interactively.

### Steps

1. Run the program and enter a Taiwan stock code (e.g. `2330` for TSMC)
2. Firefox opens and navigates to the TWSE query page
3. The TWSE API is called simultaneously to fetch this month's daily data
4. A closing price chart and a formatted data table are displayed

---

## Data Source

Taiwan Stock Exchange (TWSE) Open API:

```
https://www.twse.com.tw/exchangeReport/STOCK_DAY?response=json&date={YYYYMMDD}&stockNo={ticker}
```

---

## Data Fields

| Field (Chinese) | Description |
|-----------------|-------------|
| 日期 | Trading date |
| 成交股數 | Total shares traded |
| 成交金額 | Total trading value (NTD) |
| 開盤價 | Opening price |
| 最高價 | Daily high |
| 最低價 | Daily low |
| 收盤價 | Closing price |
| 漲跌價差 | Price change vs. previous close |
| 成交筆數 | Number of transactions |

---

## File Structure

```
Individual-Stock-Trading-Information-Inquiry-System/
├── README.md                                                          # English (this file)
├── README.zh-TW.md                                                    # Traditional Chinese
├── [Code] Individual-Stock-Trading-Information-Inquiry-System.py      # Python script
└── [Code] Individual-Stock-Trading-Information-Inquiry-System.ipynb   # Jupyter Notebook
```

---

## Notes

- Data coverage is limited to the **current month** as returned by the TWSE API
- Ensure GeckoDriver version is compatible with your installed Firefox version
- If Chinese characters do not render correctly in Matplotlib, replace the font setting in the code:
  ```python
  # Change this line:
  plt.rcParams['font.sans-serif'] = ['Taipei Sans TC Beta']
  # To an available CJK font, e.g.:
  plt.rcParams['font.sans-serif'] = ['Microsoft JhengHei']   # Windows
  plt.rcParams['font.sans-serif'] = ['PingFang TC']           # macOS
  ```

---

## License

This project is for educational and personal use only. Stock data is provided by the Taiwan Stock Exchange and remains their property.
