# Log XLC 🚀

 > **One-Sentence Pitch:** "ImpactNet fuses decades of market data (1990–2025) with learned information signals to decide when news and price action truly matter.”

## 📊 Results & Performance (Placeholder)
Below is a sample equity curve comparing the **Swing AI** strategy against the S&P 500 (SPY) benchmark over the test period (Jan 2024 – Present).

![Equity Curve](./equity-curve.jpeg)

| Metric | Log XLC |
| :--- | :--- |
| **Total Return** | 50.37% |
| **Max Drawdown** | -23.20% |
| **Win Rate** | 58% |

*Note: Results depend on the specific random seed used for slippage simulation.*

## 💡 Inspiration
Modern quantitative trading is dominated by opaque systems trained on decades of market data, with little emphasis on reproducibility or understanding. As strong believers in open-source research, we built this project to show that long-horizon market models and information-driven signals can be developed transparently and shared for learning, experimentation, and verification.


## 🚀 Key Features
1. **Stacked Esemble Logic:**
- Level 1: LightGBM, CatBoost, and Ridge Classifier.
- Level 2: Logistic Regression Router to weigh models based on market volatility regimes.
2. **News LLM Integration:** Uses Qwen/Qwen2.5-3B-Instruct (via HuggingFace Transformers) to read raw news headlines and output a sentiment score (-1.0 to 1.0) specific to US Tickers.
3. **Robust Risk Management:**
- Volatility-based position sizing
- ATR (Average True Range) Trailing Stops
- Max Drawdown circuit breakers. 

## 🧠 Challenges we ran into
1. Turning messy information into something usable
2. Avoiding hidden data leakage
3. Balancing model power with practicality

## 🏅 Accomplishments that we're proud of
1. Proved advanced ideas can be open-source: Rather than treating sophisticated models as black boxes, we built everything with reproducibility and openness as first-class goals.

## 📦 Installation & Requirements
- **Hardware:** 16GB+ VRAM Nvidia GPU
- **Python Dependencies:** `pip install -U bitsandbytes accelerate transformers lightgbm catboost scikit-learn numpy pandas matplotlib yfinance`

## 🖥️ Usage
1. **Prepare the Script:** Ensure all python dependencies and notebook is ready.
2. **News Data:** The script currently contains a hardcoded NEWS_DATA list for demonstration. In production, you would load this from an external API or scraper.

## 📚 Open in Kaggle for Testing
[![Notebook!](https://kaggle.com/static/images/open-in-kaggle.svg)](https://www.kaggle.com/code/jeminm/log-xlc-hackathon-project)

## 🧠 Model Logic Details (The 'Fusion' Algorithm)
The final trade probability is calculated as:

$$
P_{final} =
P_{technical}
\times
\text{clamp}\left(
1.0 + (\text{strength} \times Score_{news}),
0.7,
1.3
\right)
$$

- If news is **Bullish**, the probability is boosted (up to 30%).
- If news is **Bearish**, the probability is penalized (down to 30%).
- If news is **Neutral**, the technical signal remains unchanged.

## ⚠️ Disclaimer
- **This software is for educational and research purposes only.**

- **Not Financial Advice:** The strategies and code provided here do not constitute financial advice.

- **Risk** Algorithmic trading involves significant risk. Backtest results (simulations) do not guarantee future performance.

- **Data:** This system relies on `yfinance` (unofficial API) and generative AI, both of which may produce inaccurate or incomplete data.
