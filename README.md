# Stock Price Prediction Using LSTM

End‑to‑end project predicting daily closing prices for 10 major stocks with an LSTM neural network, including an **interactive widget** to forecast a user‑selected future date. Notebook + dissertation + slides included.

## 🔎 Overview
- **Model**: 2× LSTM(50) → Dense(1), optimizer **Adam**, loss **MSE**.
- **Sequence length**: 60 look‑back steps (time windows).
- **Data**: Yahoo Finance via `yfinance` for 10 tickers: `AAPL, META, GOOGL, MSFT, TSLA, AMZN, NFLX, NVDA, INTC, IBM`.
- **Preprocessing**: MinMax scaling; sliding windows; train/test split.
- **Metrics**: MSE, MAE.
- **Extras**: Plotly interactive charts; **ipywidgets** tool to predict price on a chosen date.

## 📂 Repository structure
```
stock-price-prediction-lstm/
├─ README.md
├─ requirements.txt
├─ .gitignore
├─ notebooks/
│  └─ StockPricePredictionUsingLSTM_001272625.ipynb
├─ src/                 # (optional for modular code later)
├─ data/
│  └─ README.md
├─ assets/              # add screenshots used in README
└─ reports/
   ├─ Final_report_001272625.pdf
   └─ Stock Price Prediction PPT (1).pptx
```

## 🚀 How to run (local)
1. Create a virtual environment (recommended).
2. Install deps:
   ```bash
   pip install -r requirements.txt
   ```
3. Enable Jupyter widgets (first time only):
   ```bash
   jupyter nbextension enable --py widgetsnbextension
   ```
4. Launch Jupyter:
   ```bash
   jupyter lab
   ```
5. Open `notebooks/StockPricePredictionUsingLSTM_001272625.ipynb` and run all cells.

> **Tip:** If you hit Yahoo rate limits, cache data to CSV once and reuse locally.

## ▶️ Run in Google Colab
- Upload the notebook to Colab.
- `pip install -q yfinance plotly ipywidgets tensorflow scikit-learn`
- In Colab: *Runtime → Change runtime type → GPU (optional)*.
- Ensure widgets are enabled: `from google.colab import output; output.enable_custom_widget_manager()`

## 📊 Sample performance (from report)
| Ticker | MSE    | MAE    |
|-------:|:------:|:------:|
| AAPL   | 1.4788 | 0.5178 |
| META   | 79.2327| 5.7424 |
| GOOGL  | 3.4856 | 1.1046 |
| MSFT   | 8.7600 | 1.2860 |
| TSLA   | 69.7353| 4.1160 |
| AMZN   | 4.4626 | 1.0934 |
| NFLX   |119.8323| 6.6549 |
| NVDA   | 1.6544 | 0.8179 |
| INTC   | 0.6460 | 0.5019 |
| IBM    | 2.2357 | 0.8381 |

> These figures vary by train/test split and seed but illustrate relative difficulty across tickers.



## 🧩 Key implementation notes
- Sliding window creation for sequences (`n_steps=60`).
- Two stacked LSTM layers with `return_sequences=True` on the first.
- 10 epochs, batch size 32 (tune as needed).
- Interactive **ipywidgets** lets a user pick a ticker + date; the model iteratively forecasts to that date.

## ⚖️ Disclaimer
Educational project demonstrating time‑series modeling with deep learning. **Not financial advice.** Check Yahoo Finance terms before redistribution of data.

## 📚 References & docs
See `reports/Final_report_001272625.pdf` for full methodology, literature review, risks, limitations, and future work. Slides: `reports/Stock Price Prediction PPT (1).pptx`.
