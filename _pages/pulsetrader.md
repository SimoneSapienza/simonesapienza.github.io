---
layout: single
title: "PulseTrader – Real-Time Trading Engine with ML Integration"
permalink: /pulsetrader/
excerpt: "Android application based on Raven-style matrices."
author_profile: true
toc: true
toc_label: "Contents"
toc_sticky: true
---

PulseTrader is a modular real-time trading engine focused on:

- ingesting and normalizing live market data  
- computing technical indicators over sliding windows  
- generating feature sets for ML models  
- executing validated orders with exchange-level constraints  
- maintaining consistency under continuous data streams  

The project emphasizes **architecture**, **data flow reliability**, and **model integration**, without disclosing trading strategies or proprietary logic.

---

## 1. System Structure

PulseTrader is composed of the following main components:

### **Market Data Layer**
- WebSocket clients for continuous tick or order-book streams.
- Periodic REST synchronization for historical candles.
- Per-symbol data buffers with:
  - timestamp alignment  
  - missing-data handling  
  - out-of-order event correction  
- Recovery logic for disconnects or API throttling.

### **Indicator & Feature Engine**
- Rolling computation on sliding windows (configurable time horizon).
- Indicators include:
  - moving averages (SMA, EMA)
  - volatility measures (ATR, Bollinger Bands, Keltner)
  - oscillators (RSI, Stochastic, Williams %R, CCI)
  - price-derived transforms (ROC, PPO, Momentum)
  - volume/flow metrics (OBV, CMF)
  - custom rolling statistics
- Optimized recalculation to avoid recomputing entire history at each update.

### **Machine Learning Layer**
- Offline training pipelines based on:
  - XGBoost (tree-based models)
  - LSTM architectures (sequence modeling)
- Feature preparation:
  - per-symbol normalization  
  - window extraction  
  - multi-horizon target generation (no targets disclosed)
- Training utilities:
  - time-series cross-validation  
  - Optuna hyperparameter tuning  
  - SHAP analysis for feature contribution  
- Runtime inference:
  - models pre-loaded in memory  
  - scoring performed on closed-candle intervals  
  - prediction outputs passed to the decision layer

### **Decision Logic (Non-Strategic)**
This module does *not* contain trading strategies in the public version.  
Its public description is limited to:

- rule-based validation of exchange constraints  
- integration of model outputs with system checks  
- state machine for order lifecycle management  
- configurable timeouts and safety guards  
- structured logging for traceability

No thresholds, proprietary rules, or profitability logic are described.

### **Execution Layer**
- Order generation with:
  - precision computation (tick size, step size, asset precision)
  - rounding rules compliant with exchange metadata
- Separation between:
  - tick-level events  
  - execution attempts  
  - post-order state updates  
- Idempotent execution to avoid duplicate placements.
- Error-handling pipeline for rejected or expired orders.

### **Storage & Logging**
- MySQL for trade metadata, order lifecycle, and decisions.
- Optional time-series storage (InfluxDB) for:
  - indicator snapshots  
  - aggregated metrics  
- Structured logging (JSON) for analysis and debugging.

---

## 2. Data Processing Pipeline

### **Data acquisition**
- Historical data retrieval
- Real-time incremental updates
- Synchronization strategy to maintain consistent rolling windows

### **Feature generation**
- Multi-resolution OHLCV extraction
- Rolling window computation
- Memory-optimized indicator updates
- Grouping by symbol, interval, and time index

### **Model interface**
- Predictive features generated at fixed intervals
- Batched scoring for multiple symbols
- Low-latency path for loading and evaluating models

---

## 3. Execution & Validation

### **Precision handling**
- Conversion and rounding rules derived from exchange metadata:
  - baseAssetPrecision  
  - quoteAssetPrecision  
  - stepSize  
  - tickSize  

### **Consistency checks**
- Order admissibility validation  
- Prevention of invalid quantities/prices  
- Mandatory alignment with symbol-specific constraints

### **State transitions**
- Pending → Placed → Partially filled → Filled / Cancelled / Timeout  
- All transitions recorded for reproducibility  
- Automatic cleanup of expired states

---

## 4. Reliability & Fault Tolerance

Mechanisms implemented to maintain continuity:

- automatic reconnect and backoff on WebSocket drops  
- periodic resync of historical data  
- timeout watchers for model inference  
- fallback logic when a module is temporarily unavailable  
- deterministic logging for post-mortem analysis  
- safe shutdown with state preservation  

---

## 5. Technology Stack

### **Languages**
- Python (runtime engine, indicators, ML)
- Java (legacy engine used as reference implementation)

### **APIs**
- Binance REST & WebSocket  
- Custom wrappers for candle/history retrieval

### **Storage**
- MySQL (trades, orders, state machine)
- Optional: InfluxDB for time-series metrics

### **Machine Learning**
- XGBoost  
- scikit-learn  
- TensorFlow/Keras (LSTM)  
- Optuna (hyperparameter search)  
- SHAP (feature contribution analysis)

### **Infrastructure & Tools**
- Docker containers for modular components  
- Git for version control  
- CI/CD integration for reproducibility  
- Telegram bot for optional notifications (non-sensitive)

---

## 6. Engineering Considerations

Some of the main technical topics addressed in the project:

- synchronization of asynchronous data sources  
- consolidation of high-frequency ticks into candle structures  
- incremental feature computation  
- time-series ML workflow design  
- cross-language indicator consistency  
- precision-critical order construction  
- structured, reproducible state transitions  
- latency and load management with multiple symbols  
- clear separation between:
  - data pipelines  
  - model inference  
  - execution module  
  - system monitoring  

---

This page intentionally avoids publishing any strategy logic, thresholds, profitability rules, or sensitive decision criteria.  
Its purpose is solely to outline the **architecture**, **technical components**, and **engineering characteristics** of the system.
