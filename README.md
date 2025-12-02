# FinDash Buddy - Your AI-Powered Trading Laboratory

> **"Form ni gani? Twende kazi!

" (What's the plan? Let's work!)**  
> **This is the story of how I turned four years of chaos, 47 Jupyter notebooks, and countless blown accounts into the trading partner I always wished existed.**

> [!CAUTION]
> **UNDER DEVELOPMENT: Still polishing, still fixing, still building!** 🚧

---

## 👋 Hey! I'm Daniel — And This Is the Tool I Built for Myself (and Now for You)

For years, I was that guy drowning in notebooks, CSVs, and half-baked models. One notebook for Gold, another for BTC, another for NAS100… same code, just copy-paste. I created and trained accurate models that I lost track of. Every model demanded its own environment and my laptop looked like a data crime scene.

I believe in **data for evidence** with repeatable experiments/measurements. I needed to keep my models in one environment and build a city around them.

**"And here we are!"**

So I stopped jumping between scattered pipelines and built one unified system — a real lab where my technical analysis, astro cycles, volatility studies, ML models, and RL agents could live together.

That lab became **FinDash Buddy**.

![Main Dashboard - Live Trading View](./Images/Screenshot%20from%202025-11-30%2017-25-11.png)
*My command center. Live charts, smart metrics, my watchlist — everything I used to jump between in 10 tabs now lives in one place.*

---

## 🎯 Why I Built FinDash Buddy

Very many reasons, but the main ones:

* Training an LSTM on Gold, then starting from zero for EURUSD
* Paying expensive subscriptions when I could build 10x better tools myself
* Seeing brilliant open-source models (that I had built) nobody uses because there's no way to plug them into real trading
* Switching between 15 apps to understand one market move

So I asked myself:

**"What if I gave every trader — coder or not — the same firepower I designed for myself?"**

That became the soul of FinDash Buddy.

---

## 🏭 The 9-Step "Money Factory" - Deep Dive

This is the pipeline that finally replaced my messy notebooks. Each step transforms raw market data into actionable intelligence.

### **Step 1: Data Source - The Foundation**

**What it does:** Connects to your data sources and loads market data  
**Inputs:** MT5 connection, CSV files, or mixed datasets  
**Outputs:** Clean OHLCV (Open, High, Low, Close, Volume) time series data

![Data Source Selection](./Images/Screenshot%20from%202025-11-30%2017-29-08.png)


**Why this matters:** Garbage in = garbage out. This step ensures your data is clean, properly formatted, and ready for analysis.

**What you can do:**
- Connect to MetaTrader 5 (MT5) for live/historical data
- Upload CSV files with custom market data
- Merge multiple data sources (e.g., combine MT5 with external sentiment data)
- Select symbols, timeframes (M1, M5, H1, H4, D1, etc.)
- Set date ranges for historical analysis

**Expected output:** A validated dataset with timestamps, OHLCV data, and metadata

---

### **Step 2: Technical Analysis - The Math Layer**

**What it does:** Calculates 50+ technical indicators and their differentials  
**Inputs:** Raw OHLCV data from Step 1  
**Outputs:** Enriched dataset with indicators (SMA, EMA, RSI, MACD, Bollinger Bands, etc.)

![Technical Analysis Configuration](./Images/Screenshot%20from%202025-11-30%2017-27-41.png)

**Available Indicators:**
- **Trend:** SMA (multiple periods), EMA, DEMA, TEMA, WMA
- **Momentum:** RSI, Stochastic, CCI, Williams %R, ROC
- **Volatility:** Bollinger Bands, ATR, Standard Deviation, Keltner Channels
- **Volume:** OBV, VWAP, Volume MA, Money Flow Index
- **Oscillators:** MACD, Stochastic RSI, Ultimate Oscillator
- **Custom:** Parabolic SAR, Ichimoku, Supertrend, Pivot Points

**Chart Visualizations:**
1. **Main Price Chart** - Candlestick/Line/Area/Bar/Heikin-Ashi
2. **RSI Panel** - Separate panel showing RSI oscillator with overbought/oversold zones
3. **MACD Panel** - MACD line, signal line, and histogram

**What you can configure:**
- Select which indicators to calculate
- Customize periods (e.g., SMA 20, 50, 200)
- Set MACD parameters (fast: 12, slow: 26, signal: 9)
- Configure Bollinger Bands (length: 20, std: 2)
- Enable/disable indicator differentials (rate of change)

**Expected output:** Dataset with 50-150 new columns depending on configuration

---

### **Step 3: Support & Resistance (SNR) - The Zones**

**What it does:** Automatically detects support and resistance zones using clustering algorithms  
**Inputs:** OHLCV + Technical indicators  
**Outputs:** SNR zones, breakout signals, bounce signals

![SNR Signal Analysis](./Images/Screenshot%20from%202025-11-30%2017-28-16.png)

**How it works:**
1. **Zone Detection:** Uses K-Means clustering to find price levels where price repeatedly bounces
2. **Strength Calculation:** Measures how many times price respected each zone
3. **Signal Generation:** Identifies breakouts, bounces, and rejections

**Configuration Options:**
- **Lookback Period:** How far back to search for zones (default: 500 candles)
- **Confirmation Period:** Candles needed to confirm a zone (default: 3)
- **Lookforward Period:** Future candles to validate signals (default: 10)
- **Number of Clusters:** How many SNR zones to identify (default: 8)
- **Zone Width:** Thickness of each zone in percentage (default: 0.5%)
- **Minimum Distance:** Minimum separation between zones (default: 1%)

**Signals Generated:**
- `SNR_Signal`: -1 (resistance rejection), 0 (neutral), +1 (support bounce)
- `SNR_Strength`: Confidence score (0-1)
- `SNR_Zone_Type`: Support or Resistance
- `SNR_Distance`: Distance to nearest zone

**Chart Display:**
- Horizontal zones overlaid on price chart
- Color-coded by strength (green = strong support, red = strong resistance)
- Signal markers at breakout/bounce points

---

### **Step 4: Astronomical Features - The Cosmic Edge**

**What it does:** Calculates planetary positions, lunar phases, and astronomical aspects  
**Inputs:** Time series data with timestamps  
**Outputs:** Astronomical features correlated with market cycles

**Why astronomy?** Not superstition — statistical correlation. Markets are driven by human psychology, and human behavior shows measurable patterns with lunar cycles, planetary aspects, and seasonal timing.

**Features Calculated:**
- **Lunar Phase:** New Moon, Waxing Crescent, First Quarter, Waxing Gibbous, Full Moon, Waning Gibbous, Last Quarter, Waning Crescent
- **Planetary Positions:** Sun, Moon, Mercury, Venus, Mars, Jupiter, Saturn positions in zodiac
- **Major Aspects:** Conjunction (0°), Opposition (180°), Trine (120°), Square (90°), Sextile (60°)
- **Retrograde Periods:** Mercury, Venus, Mars retrograde indicators
- **Seasonal Timing:** Equinoxes, solstices, quarter markers

**Configuration:**
- Select which celestial bodies to track
- Choose aspect types (major vs minor)
- Set orb tolerance for aspects (±5°)
- Enable/disable retrograde tracking

**Visualization:**
- **Orbital Chart:** Shows planetary positions over time
- **Aspect Timeline:** Marks when major aspects occur
- **Phase Correlation:** Overlays lunar phases on price chart

**Expected Output:** 20-40 astronomical columns added to dataset

---

### **Step 5: News Sentiment - The Mood Detector**

**What it does:** Analyzes news headlines and social media sentiment  
**Inputs:** Time-aligned news data, social media feeds  
**Outputs:** Sentiment scores, fear/greed index, event markers

**Data Sources:**
- Financial news APIs (Bloomberg, Reuters, etc.)
- Social media (Twitter/X, Reddit, StockTwits)
- Economic calendars (Fed announcements, earnings, etc.)

**Sentiment Metrics:**
- **Overall Sentiment:** -1 (bearish) to +1 (bullish)
- **Fear/Greed Index:** 0 (extreme fear) to 100 (extreme greed)
- **Event Impact Score:** Predicted market impact (0-10)
- **Keyword Frequency:** Mentions of key terms (recession, rally, crash, etc.)

**Expected Output:** Sentiment columns aligned with price data timestamps

---

### **Step 6: Feature Review - The Quality Control**

**What it does:** Statistical analysis and quality checks on all features  
**Inputs:** Complete dataset with all features from Steps 1-5  
**Outputs:** Feature importance scores, correlation matrices, quality reports

**Analysis Modules:**

#### 6.1 **Descriptive Statistics**
- Mean, median, standard deviation
- Min, max, quartiles (Q1, Q3)
- Skewness, kurtosis
- Missing value percentage
- Coefficient of variation

**Chart:** Histogram distribution for each feature

#### 6.2 **Feature Importance**
- Random Forest feature importance scores
- F-statistic and p-values (ANOVA)
- Identifies which features have predictive power

**Chart:** Bar chart ranking features by importance

#### 6.3 **Correlation Analysis**
- Pearson correlation matrix
- Identifies highly correlated features (multicollinearity)
- Highlights significant correlations with target

**Chart:** Heatmap showing feature correlations

#### 6.4 **Multicollinearity Detection**
- VIF (Variance Inflation Factor) scores
- Condition number analysis
- Recommends features to remove

**Chart:** VIF scores bar chart

#### 6.5 **Outlier Detection**
- IQR method (Interquartile Range)
- Z-score method
- Isolation Forest algorithm
- Reports outlier percentage per feature

**Chart:** Box plots showing outliers

#### 6.6 **Time Series Tests**
- **ADF Test:** Tests for stationarity
- **KPSS Test:** Confirms stationarity
- Identifies if differencing is needed

**Chart:** Time series plot with stationarity indicators

#### 6.7 **Distribution Analysis**
- Normality tests (Shapiro-Wilk)
- Skewness interpretation
- Kurtosis interpretation
- Identifies multimodal distributions

**Chart:** Q-Q plots, distribution curves

#### 6.8 **PCA (Principal Component Analysis)**
- Dimensionality reduction
- Variance explained by components
- Scree plot showing optimal component count
- Component loadings (which features contribute to each PC)

**Charts:**
- Scree plot (variance explained)
- Component correlation heatmap
- Cumulative variance curve

**What you can do:**
- Select which analysis modules to run
- Choose columns to analyze
- Set thresholds for outlier detection
- Review and remove problematic features
- Export quality reports

**Expected Output:** Clean, validated dataset ready for ML + detailed quality report

---

### **Step 7: ML Preparation - The Dataset Builder**

**What it does:** Transforms tabular data into ML-ready sequences  
**Inputs:** Clean feature dataset from Step 6  
**Outputs:** Train/validation/test splits, scaled sequences, target labels

![ML Preparation](./Images/Screenshot%20from%202025-11-30%2017-28-39.png)

**Configuration Options:**

#### **Sequence Parameters:**
- **Sequence Length:** How many past candles to use as input (default: 60)
  - Example: 60 means "use last 60 candles to predict next N candles"
- **Prediction Length:** How many future candles to predict (default: 4)
  - Example: 4 means "predict next 4 candles' close prices"

#### **Target Columns:**
- Select what to predict:
  - `close` (price prediction)
  - `direction` (up/down classification)
  - `volatility` (volatility regime)
  - `snr_signal` (support/resistance signals)
  - Custom targets

#### **Feature Selection:**
- **Exclude Columns:** Remove non-predictive columns (timestamps, symbols, etc.)
- **Include All:** Use all available features
- **Custom Selection:** Manually pick features

#### **Scaling:**
- **MinMax Scaler:** Scales to [0, 1] range (best for neural networks)
- **Standard Scaler:** Z-score normalization (mean=0, std=1)
- **Robust Scaler:** Uses median and IQR (resistant to outliers)
- **Save Scaler:** Save scaler parameters for production use
- **Load Scaler:** Use pre-trained scaler for consistency

#### **Data Splitting:**
- **Train Ratio:** Percentage for training (default: 70%)
- **Validation Ratio:** Percentage for validation (default: 15%)
- **Test Ratio:** Percentage for testing (default: 15%)
- **Split Strategy:**
  - **Sequential:** Time-ordered split (recommended for time series)
  - **Random:** Shuffled split (not recommended for time series)
  - **Stratified:** Balanced class distribution (for classification)

#### **Advanced Options:**
- **Random Seed:** For reproducibility (default: 42)
- **Shuffle Data:** Whether to shuffle sequences (usually False for time series)
- **Handle Class Imbalance:** Apply SMOTE or class weights

**Output Metrics:**
- **Total Sequences:** Number of sequences created
- **Train Sequences:** Count in training set
- **Validation Sequences:** Count in validation set
- **Test Sequences:** Count in test set
- **Input Shape:** `[sequence_length, num_features]` (e.g., `[60, 45]`)
- **Output Shape:** `[prediction_length, num_targets]` (e.g., `[4, 1]`)
- **Signal Distribution:** Class balance for classification targets
- **Scaled Features:** Number of features after scaling

**Charts:**
- **Sequence Distribution:** Bar chart showing train/val/test split
- **Signal Distribution:** Pie chart showing class balance
- **Feature Scaling:** Before/after scaling comparison

**Expected Output:** 
```python
{
  "X_train": np.array([...]),  # Shape: (num_train_sequences, sequence_length, num_features)
  "y_train": np.array([...]),  # Shape: (num_train_sequences, prediction_length, num_targets)
  "X_val": np.array([...]),
  "y_val": np.array([...]),
  "X_test": np.array([...]),
  "y_test": np.array([...]),
  "scaler": MinMaxScaler(...),
  "config": {...}
}
```

---

### **Step 8: Model Selection & Training - The Brain**

**What it does:** Build, configure, and train deep learning models  
**Inputs:** ML-ready sequences from Step 7  
**Outputs:** Trained model with performance metrics

![Model Builder](./Images/Screenshot%20from%202025-11-30%2017-28-39.png)

**Model Architectures Available:**

#### **1. LSTM (Long Short-Term Memory)** 🔄
- **Best for:** Sequential patterns, trend following
- **Complexity:** Medium
- **Parameters:**
  - `lstm_units`: [64, 128, 256] - Number of LSTM cells per layer
  - `num_layers`: [1, 2, 3, 4] - Depth of network
  - `dropout`: [0.0 - 0.5] - Regularization to prevent overfitting
  - `bidirectional`: [True/False] - Process sequences forward and backward
  - `return_sequences`: [True/False] - For stacked LSTMs

**Example Architecture:**
```
Input (60, 45) → LSTM(128) → Dropout(0.2) → LSTM(64) → Dense(4)
```

#### **2. TCN (Temporal Convolutional Network)** ⏱️
- **Best for:** Fast training, long-range dependencies
- **Complexity:** Medium-High
- **Parameters:**
  - `num_filters`: [32, 64, 128] - Convolutional filters per layer
  - `kernel_size`: [2, 3, 5, 7] - Size of convolutional kernel
  - `num_layers`: [4, 6, 8] - Number of residual blocks
  - `dilation_rates`: [[1,2,4,8], [1,2,4,8,16]] - Exponential dilation
  - `dropout`: [0.0 - 0.3]

**Example Architecture:**
```
Input (60, 45) → TCN Block(64, dilation=1) → TCN Block(64, dilation=2) → 
TCN Block(64, dilation=4) → TCN Block(64, dilation=8) → Dense(4)
```

#### **3. Transformer** 🤖
- **Best for:** Complex patterns, attention mechanisms
- **Complexity:** High
- **Parameters:**
  - `d_model`: [64, 128, 256] - Model dimension
  - `num_heads`: [4, 8, 16] - Multi-head attention heads
  - `num_layers`: [2, 4, 6] - Transformer blocks
  - `d_ff`: [256, 512, 1024] - Feed-forward dimension
  - `dropout`: [0.0 - 0.3]
  - `use_positional_encoding`: [True/False]

**Example Architecture:**
```
Input (60, 45) → Positional Encoding → 
Transformer Block (d_model=128, heads=8) × 4 → Dense(4)
```

#### **4. CNN (Convolutional Neural Network)** 🔍
- **Best for:** Pattern recognition, feature extraction
- **Complexity:** Low-Medium
- **Parameters:**
  - `filters`: [[32, 64, 128]] - Filters per conv layer
  - `kernel_sizes`: [[3, 5, 7]] - Kernel sizes
  - `pool_sizes`: [[2, 2, 2]] - Max pooling sizes
  - `dense_units`: [128, 256] - Fully connected layer size

#### **5. Hybrid Models** 🔗
- **CNN-LSTM:** CNN for feature extraction + LSTM for sequences
- **CNN-TCN:** CNN + TCN for multi-scale patterns
- **Transformer-LSTM:** Attention + recurrence

#### **6. 3D-CNN** 📦
- **Best for:** Multi-timeframe analysis
- **Complexity:** High
- **Use case:** Analyzing multiple timeframes simultaneously

#### **7. DNN (Deep Neural Network)** 🧠
- **Best for:** Simple tabular data, baseline models
- **Complexity:** Low
- **Parameters:**
  - `layers`: [[256, 128, 64]] - Layer sizes
  - `activation`: ['relu', 'tanh', 'elu']
  - `dropout`: [0.0 - 0.5]

**Training Configuration:**

- **Optimizer:** Adam, SGD, RMSprop, AdamW
- **Learning Rate:** 0.0001 - 0.01 (with scheduler options)
- **Batch Size:** 16, 32, 64, 128
- **Epochs:** 50, 100, 200, 500
- **Loss Function:**
  - Regression: MSE, MAE, Huber
  - Classification: Binary Crossentropy, Categorical Crossentropy
- **Early Stopping:** Stop if validation loss doesn't improve for N epochs
- **Model Checkpointing:** Save best model during training

**What you can do:**
1. **Browse Model Catalog:** View all available architectures
2. **Filter by Category:** LSTM, CNN, TCN, Transformer, Hybrid
3. **Filter by Complexity:** Low, Medium, High
4. **Search Models:** Find specific architectures
5. **Select Model:** Choose architecture that fits your use case
6. **Configure Parameters:** Adjust hyperparameters using sliders/inputs
7. **Build Model:** Generate model summary and architecture diagram
8. **Train Model:** Start training with real-time progress
9. **Monitor Training:** View loss curves, accuracy metrics
10. **Save Model:** Save trained model to library or marketplace

**Expected Output:**
- **Model Summary:** Layer-by-layer architecture description
- **Training Metrics:**
  - Training Loss/Accuracy per epoch
  - Validation Loss/Accuracy per epoch
  - Test Accuracy (final evaluation)
- **Performance Metrics:**
  - Sharpe Ratio (risk-adjusted returns)
  - Win Rate (percentage of profitable predictions)
  - Profit Factor (gross profit / gross loss)
  - Max Drawdown
- **Model File:** Saved weights (.h5 or .pth format)
- **Configuration File:** JSON with all hyperparameters

---

### **Step 9: Results - The Proof**

**What it does:** Displays model predictions and performance analysis  
**Inputs:** Trained model + test data  
**Outputs:** Predictions, confidence scores, performance charts

![Results Dashboard](./Images/Screenshot%20from%202025-11-30%2017-29-45.png)

**Results Display:**

#### **Prediction Output:**
- **Direction:** Bullish/Bearish/Neutral
- **Confidence:** 0-100% confidence score
- **Predicted Prices:** Next N candle close prices
- **Volatility Regime:** Low/Medium/High/Extreme
- **Probability Distribution:** Confidence intervals

#### **Performance Metrics:**
- **Training Accuracy:** How well model learned training data
- **Validation Accuracy:** Performance on unseen validation data
- **Test Accuracy:** Final performance on test set
- **Sharpe Ratio:** Risk-adjusted returns (higher is better)
- **Win Rate:** Percentage of correct predictions
- **Profit Factor:** Total profit / total loss ratio
- **Max Drawdown:** Largest peak-to-trough decline

#### **Visualization Charts:**
1. **Prediction vs Actual:** Line chart comparing predictions to reality
2. **Confusion Matrix:** For classification tasks
3. **Equity Curve:** Cumulative returns over time
4. **Loss Curves:** Training and validation loss over epochs
5. **Feature Importance:** Which features the model relied on most

**What you can do:**
- **Review Results:** Analyze model performance
- **Export Predictions:** Save predictions to CSV
- **Save Model:** Add to your model library
- **Publish to Marketplace:** Share/sell your model
- **Generate Report:** Create PDF summary
- **Backtest Strategy:** Test trading strategy with predictions
- **Deploy Model:** Use for live trading signals

---

## 📊 Chart Types & Visualizations

FinDashBuddy supports **5 chart types** with extensive customization:

### **1. Candlestick Charts** 🕯️
- **Use case:** Standard price action analysis
- **Features:**
  - Green candles (bullish): Close > Open
  - Red candles (bearish): Close < Open
  - Wicks show high/low range
  - Customizable colors and styles

### **2. Line Charts** 📈
- **Use case:** Clean trend visualization
- **Features:**
  - Connects close prices
  - Smooth trend lines
  - Multiple line overlays (SMA, EMA, etc.)

### **3. Area Charts** 🏔️
- **Use case:** Filled trend visualization
- **Features:**
  - Shaded area under line
  - Gradient fills
  - Emphasizes magnitude of movement

### **4. Bar Charts** 📊
- **Use case:** OHLC visualization
- **Features:**
  - Vertical bar shows high-low range
  - Horizontal ticks show open/close
  - Alternative to candlesticks

### **5. Heikin-Ashi Charts** 🎴
- **Use case:** Smoothed trend identification
- **Features:**
  - Modified candlestick calculation
  - Filters out noise
  - Clearer trend signals
  - Reduces false signals

**Chart Customization:**
- **Timeframes:** M1, M5, M15, M30, H1, H4, D1, W1, MN1
- **Indicators:** Overlay 50+ technical indicators
- **Drawing Tools:** Trend lines, horizontal lines, Fibonacci retracements
- **Templates:** Save/load chart configurations
- **Themes:** Dark mode, light mode, custom color schemes
- **Export:** Save charts as PNG/PDF

---

## 🔍 Multi-Timeframe Analysis - The Alignment Strategy

**What it is:** Analyze the same asset across multiple timeframes simultaneously

![Multi-Timeframe Analysis Window](./Images/Screenshot%20from%202025-11-30%2017-30-59.png)

**How it works:**
1. Select symbol (e.g., EURUSD)
2. Choose timeframes (e.g., M5, M15, H1, H4, D1)
3. Run analysis across all timeframes
4. View consensus signals

**For each timeframe, you see:**
- **Volatility:** Current volatility level
- **Speed:** Rate of price change
- **Direction:** Bullish/Bearish/Neutral
- **Regime:** Trending/Ranging/Volatile
- **Model Predictions:** AI predictions for this timeframe
- **Sparkline:** Mini price chart

**Consensus Dashboard:**
- **Overall Direction:** Weighted average across timeframes
- **Alignment Score:** How many timeframes agree (0-100%)
- **Strongest Timeframe:** Which timeframe has clearest signal
- **Conflicting Signals:** Timeframes that disagree
- **Recommended Action:** Buy/Sell/Wait based on alignment

**Use case:** Trade only when multiple timeframes align (e.g., H1, H4, and D1 all bullish)

---

## 🤖 AI Chat Assistant - Your Trading Buddy

![AI Chat Assistant](./Images/Screenshot%20from%202025-11-30%2017-30-15.png)

**What it does:** Natural language interface to your analysis

**Supported LLM Providers:**
- **Local:** Phi-3-Mini, Llama, Mistral (runs on your machine)
- **OpenAI:** GPT-4, GPT-4-Turbo, GPT-3.5
- **Anthropic:** Claude 3 Opus, Claude 3 Sonnet
- **Google:** Gemini Pro, Gemini Flash

**What you can ask:**
- "Explain this divergence on EURUSD H4"
- "Form ni gani leo?" (What's the setup today?)
- "Is this bullish or am I dreaming?"
- "What do the models predict for Gold?"
- "Show me the strongest support zone"
- "Which timeframe has the clearest signal?"

**Context-Aware Responses:**
The AI has access to:
- Current chart data (OHLCV)
- Technical indicators
- Model predictions
- Volatility metrics
- Momentum indicators
- Market regime
- Astronomical conditions
- Sentiment scores
- Multi-timeframe analysis

**Example Conversation:**
```
You: "What's the setup on BTCUSD right now?"

AI: "Based on the current analysis:
- Price: $42,350 (+2.3% today)
- Direction: Bullish on H1, H4, D1 (strong alignment)
- Volatility: Medium (ATR: 850)
- Key Level: Strong support at $41,800
- Model Prediction: 73% probability of move to $43,200
- Regime: Trending (ADX: 28)
- Recommendation: Look for pullback to $42,000 for long entry"
```

---

## 🛠️ Building Your Own Models - The Creator's Guide

**Can I code my own model?** YES! Here's how:

### **Option 1: Use the Model Builder (No Code)**
1. Go to Step 8 (Model Selection)
2. Browse the model catalog
3. Select an architecture (LSTM, TCN, Transformer, etc.)
4. Configure parameters using sliders
5. Click "Build Model"
6. Train and save

### **Option 2: Custom Architecture (Advanced)**

**Backend Integration:**
Create a new model architecture in `Backend/app/models/architectures/`:

```python
# Backend/app/models/architectures/my_custom_model.py

from tensorflow.keras.models import Model
from tensorflow.keras.layers import Input, LSTM, Dense, Dropout

def build_my_custom_model(
    input_shape: tuple,
    n_predictions: int,
    lstm_units: int = 128,
    dropout: float = 0.2
) -> Model:
    """
    My custom LSTM architecture with special sauce
    
    Args:
        input_shape: (sequence_length, num_features)
        n_predictions: Number of future steps to predict
        lstm_units: LSTM layer size
        dropout: Dropout rate
    
    Returns:
        Compiled Keras model
    """
    inputs = Input(shape=input_shape)
    
    # Your custom architecture here
    x = LSTM(lstm_units, return_sequences=True)(inputs)
    x = Dropout(dropout)(x)
    x = LSTM(lstm_units // 2)(x)
    x = Dropout(dropout)(x)
    outputs = Dense(n_predictions)(x)
    
    model = Model(inputs=inputs, outputs=outputs)
    model.compile(optimizer='adam', loss='mse', metrics=['mae'])
    
    return model
```

**Register in Model Catalog:**
```python
# Backend/app/models/model_catalog.py

MODEL_CATALOG = [
    {
        "id": "my_custom_lstm",
        "name": "My Custom LSTM",
        "category": "lstm",
        "description": "Custom LSTM with special sauce",
        "parameters": [
            {"name": "lstm_units", "type": "int", "default": 128, "min": 32, "max": 512},
            {"name": "dropout", "type": "float", "default": 0.2, "min": 0.0, "max": 0.5}
        ],
        "builder_function": "build_my_custom_model",
        "input_requirements": {
            "min_sequence_length": 30,
            "min_features": 5
        },
        "tags": ["lstm", "custom", "experimental"],
        "complexity": "medium",
        "recommended_for": ["trend_following", "price_prediction"]
    }
]
```

**Now it appears in the frontend model catalog!**

### **Option 3: External Model Integration**

Already have a trained model? Import it:

```python
# Save your model in the standard format
import joblib

# For scikit-learn models
joblib.dump(my_model, 'my_model.pkl')

# For Keras/TensorFlow
my_model.save('my_model.h5')

# For PyTorch
torch.save(my_model.state_dict(), 'my_model.pth')
```

Then load it in FinDashBuddy:
1. Go to Model Selection
2. Click "Import Model"
3. Upload your model file
4. Configure input/output shapes
5. Test predictions
6. Save to library

---

## 🏪 Model Marketplace - Share & Earn

**Publish Your Models:**
1. Train a model with good performance
2. Click "Save Model" in Results step
3. Fill in details (name, description, symbol, timeframe)
4. Set as "Public" and "Rentable"
5. Set rental price (in BESHA tokens or $)
6. Publish to marketplace

**Model Listing Shows:**
- Model name and description
- Architecture type (LSTM, TCN, etc.)
- Symbol and timeframe trained on
- Performance metrics (accuracy, Sharpe ratio, win rate)
- Number of downloads
- User ratings and reviews
- Price (free or paid)

**Earn from Your Models:**
- Users rent your model for predictions
- You earn BESHA tokens or $ per rental
- Revenue split: 70% creator, 20% platform, 10% treasury
- Track earnings in Treasury dashboard

**Download Models:**
- Browse marketplace
- Filter by symbol, timeframe, architecture
- Sort by performance, rating, downloads
- Preview model details
- Download/rent model
- Use in your analysis pipeline

---

## 🌍 The Economy (Web3 Layer)

### 🏦 Wallet & Treasury
- Manage BESHA tokens (platform currency)
- Track earnings from model rentals
- View revenue splits
- Withdraw to external wallet

### ⚡ Compute Network
- **Rent Your GPU:** Earn tokens by providing compute power for model training
- **Hire Compute:** Pay tokens to use others' GPUs for faster training
- **Decentralized:** P2P network, no central server

### 🛒 Marketplace
- **Models:** Buy/sell trained AI models
- **Indicators:** Custom technical indicators
- **Scripts:** Trading strategies and automation
- **Datasets:** Clean, preprocessed market data

### 🤝 Social Layer
- **Follow Traders:** See what successful traders are analyzing
- **Share Analysis:** Publish your analysis for others
- **Collaborate:** Work on models together
- **Learn:** Tutorials, guides, and community support

---

## 🎓 Learning Path - From Beginner to Expert

### **Level 1: Beginner (Week 1-2)**
1. **Install FinDashBuddy**
2. **Connect MT5** or load CSV data
3. **Run your first analysis** (all 9 steps with defaults)
4. **Understand the results** (what each metric means)
5. **Try different symbols** (EURUSD, BTCUSD, Gold, etc.)

### **Level 2: Intermediate (Week 3-4)**
1. **Customize technical indicators** (add your favorite indicators)
2. **Configure SNR zones** (adjust parameters for your trading style)
3. **Experiment with ML preparation** (different sequence lengths, targets)
4. **Try different model architectures** (LSTM vs TCN vs Transformer)
5. **Analyze multi-timeframe** (find alignment across timeframes)

### **Level 3: Advanced (Month 2-3)**
1. **Build custom models** (create your own architectures)
2. **Optimize hyperparameters** (find best settings for your symbol)
3. **Backtest strategies** (test model predictions historically)
4. **Feature engineering** (create custom features)
5. **Publish to marketplace** (share your best models)

### **Level 4: Expert (Month 4+)**
1. **Develop custom indicators** (code your own technical indicators)
2. **Create hybrid models** (combine multiple architectures)
3. **Automate trading** (connect models to live trading)
4. **Contribute to codebase** (add features, fix bugs)
5. **Mentor others** (help community members)

---

## 💡 Use Cases - What Can You Actually Do?

### **1. Day Trader**
- Run analysis on M5, M15, H1 timeframes
- Use SNR zones for entry/exit points
- Check multi-timeframe alignment before entering
- Set alerts for breakout signals
- Use AI chat to confirm setups

### **2. Swing Trader**
- Analyze H4, D1, W1 timeframes
- Train models on daily data
- Use astronomical features for timing
- Monitor sentiment for major moves
- Backtest strategies over months

### **3. Algorithm Developer**
- Build custom model architectures
- Optimize hyperparameters systematically
- Backtest with historical data
- Export predictions via API
- Automate trading decisions

### **4. Researcher**
- Test hypothesis (e.g., "Do lunar phases affect Bitcoin?")
- Run statistical analysis on features
- Compare model architectures
- Publish findings
- Share datasets

### **5. Educator**
- Create tutorials using real analysis
- Share model configurations
- Demonstrate strategies
- Build course content
- Mentor students

---

## 🚀 Why FinDashBuddy is Different

### **Traditional Trading Platforms:**
- ❌ Closed-source black boxes
- ❌ Limited customization
- ❌ Expensive subscriptions
- ❌ No model training
- ❌ Siloed tools

### **FinDashBuddy:**
- ✅ **Open & Transparent:** See exactly how everything works
- ✅ **Fully Customizable:** Build your own models, indicators, strategies
- ✅ **Free Core Features:** 9-step pipeline, model training, analysis tools
- ✅ **AI-Powered:** State-of-the-art deep learning models
- ✅ **Unified Platform:** Everything in one place
- ✅ **Community-Driven:** Share, learn, earn together
- ✅ **Evidence-Based:** Data-driven decisions, not gut feelings

---

## 🛠️ Tech Stack

* **Frontend:** React + TypeScript + Vite + Tailwind CSS
* **Backend:** FastAPI (Python) + Node.js
* **AI/ML:** PyTorch, TensorFlow, scikit-learn, RLlib, Pyro (Bayesian)
* **Charts:** Recharts + Lightweight Charts (TradingView)
* **Database:** PostgreSQL + Redis
* **Web3:** Ethers.js + Solidity (smart contracts)
* **Compute:** Celery (task queue) + Docker

---


## 📖 Documentation

- **User Guide:** [docs/USER_GUIDE.md](docs/USER_GUIDE.md)
- **API Reference:** [docs/API.md](docs/API.md)
- **Model Catalog:** [docs/MODELS.md](docs/MODELS.md)
- **Contributing:** [CONTRIBUTING.md](CONTRIBUTING.md)

---

## 🤝 Contributors & Special Thanks

A massive thank you to my digital junior devs:

* **Claude** — My clean-code perfectionist
* **ChatGPT** — My chaotic genius
* **Grok** — My comedian-engineer
* **DeepSeek** — My math killer
* **Gemini** — My structured thinker
* **:D** — For vibes

You all helped shape this!
You are welcome for contributorsip , relax as I set up the pipeline

---

## 📜 License

MIT License - See [LICENSE](LICENSE) for details

---

## 🌟 Star This Repo!

If FinDashBuddy helps you trade smarter, give it a ⭐ on GitHub!

---

*Built with ❤️ in a small room full of notebooks, charts, and dreams.*  
**Ni tucarie mugate hamwe!** 🍞

---

## 🔮 Roadmap

### **Q1 2025**
- [ ] Mobile app (iOS/Android)
- [ ] Real-time alerts system
- [ ] Advanced backtesting engine
- [ ] More model architectures (GAN, VAE)

### **Q2 2025**
- [ ] Live trading integration
- [ ] Portfolio management
- [ ] Risk management tools
- [ ] Social trading features

### **Q3 2025**
- [ ] Decentralized compute network
- [ ] DAO governance
- [ ] Cross-chain support
- [ ] Advanced analytics dashboard

### **Q4 2025**
- [ ] Institutional features
- [ ] White-label solutions
- [ ] API marketplace
- [ ] Educational platform

---
