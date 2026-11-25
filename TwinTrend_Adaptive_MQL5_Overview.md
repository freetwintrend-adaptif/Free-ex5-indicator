# Ritz TwinTrend Adaptive - MQL5 Market overview


---

## 1. Name and short description

**Name:** Ritz TwinTrend Adaptive

**Short description (one line):**
Two volatility-adaptive trend lines (Fast and Slow) with sideway warning zones, HeatBar breakout detection, Fibonacci channel, SL/TP lines and a multi-timeframe Canvas dashboard.

---

## 2. Full description

### Overview

Ritz TwinTrend Adaptive puts a FAST and a SLOW adaptive trend line on one chart, so you can read the short-term and the larger trend at the same time. Instead of a fixed multiplier, each line adapts to the current market volatility: ATR values are grouped by K-Means clustering into three regimes (high, medium, low volatility), and the line follows the regime the market is in now.

Around the two lines the indicator adds the tools you normally have to combine by hand: a sideway (consolidation) warning, breakout detection with a tick spam filter, structure reasons for every signal (BoS / CHoCH), a Fibonacci channel, SL / TP lines and a dashboard that shows the active trend on every timeframe.

Every threshold is relative to ATR, so the same settings work on forex, metals, indices, crypto and stocks, and on every timeframe from M1 to MN.

### Main features

**1. FAST and SLOW trend, each with its own fill**
- Fast line (default ATR 7, factor 1.3) and Slow line (default ATR 10, factor 3.0), both fully adjustable.
- Each line has a gradient fill between the line and the candle body, drawn on the chart canvas.
- COMBINE state: both lines agree (strong trend) or disagree (mixed, be careful).

**2. Signal arrows with small text**
- BUY / SELL arrows for Fast, Slow and Combine. Choose which sources are shown.
- Fast and Slow arrows are placed on the trend line at the moment the line is born, so the chart stays tidy.
- A small text sits next to each arrow: "BUY Fast", "SELL Slow" and so on, with the reason (BoS, CHoCH, volume) and a score.
- Arrow distance is measured in pixels, so the layout looks the same on every symbol.

**3. Sideway / consolidation zones**
- Ranging markets are detected from ATR-relative range, efficiency ratio and breakout confirmation.
- Shown as a canvas zone (outline by default, fill optional) and used as a warning and a point to consider, not a hard block. Signals created inside a zone are tagged "SW". You can also choose to hide them.

**4. HeatBar breakout detection**
- Candles are colored when price presses the edge of a sideway zone and when it breaks out of it.
- A tick spam filter (spike, spread and burst protection) with a minimum hold time keeps a single bad tick from painting a false breakout.

**5. Fibonacci channel**
- A diagonal channel built from the latest swings, with configurable levels, so you can see the trend direction and its limits at a glance.

**6. SL / TP lines**
- On every BUY / SELL signal: one SL and three TP levels (risk-reward based), with SL from the trend line or from ATR.
- Lines are short and expire, so they do not stretch across the whole chart.

**7. Professional Canvas dashboard**
- Tabs: Overview, Trend, Levels, Log and View.
- Trend tab: the active trend on all timeframes, with a FAST / SLOW / COMBINE selector.
- Draggable with the mouse without moving the chart, minimize / maximize, and automatic font size so the text stays readable on any screen.
- Your layout (position, tab, font) is remembered per chart.

**8. Alerts**
- Popup, push notification and sound for new signals, new sideway zones and confirmed live breakouts.

**9. Works on short history**
- Needs at least 50 bars, so monthly and weekly charts still work on symbols with little history. The K-Means training length is shortened automatically in that case.

### How to read it

1. Check the dashboard Trend tab: do the higher timeframes agree with the chart you trade?
2. Look at the COMBINE state. Both lines in the same direction means a cleaner trend.
3. If a sideway zone is active, treat new signals with caution and wait for a HeatBar breakout.
4. Use the arrow text (BoS / CHoCH) and the score to judge the quality of a signal.
5. Use the SL / TP lines and the Fibonacci channel to plan the trade.

### Data for EAs and other indicators

All values are available through `iCustom` / `CopyBuffer`:

| Buffer | Content |
|---|---|
| 0 / 1 | Fast line, up / down part |
| 2 / 3 | Slow line, up / down part |
| 4 / 5 | Fast BUY / SELL arrow (price of the line) |
| 6 / 7 | Slow BUY / SELL arrow |
| 8 / 9 | Combine BUY / SELL arrow |
| 10 - 14 | HeatBar candle open, high, low, close and color index |
| 15 / 16 | Fast / Slow line value |
| 17 / 18 | Fast / Slow trend (+1 up, -1 down) |
| 19 | Combine trend (+1 up, -1 down, 0 mixed) |
| 20 | Sideway flag (1 = inside a zone) |
| 21 / 22 | Fast / Slow volatility cluster (0 high, 1 medium, 2 low) |

Signals are calculated on closed bars and do not repaint. The live bar is shown as a preview; the optional early arrow on the live bar is off by default and can disappear if price moves back.

### Main inputs

- Fast and Slow: ATR length, factor, colors, line width, fill on / off.
- K-Means: training length and the three percentile guesses.
- Sideway: minimum bars, range, efficiency limit, breakout buffer, fill and outline on / off.
- Tick filter: spike, spread, burst, hold time and minimum clean ticks.
- Signals: sources shown, minimum score, sideway mode (mark / hide / show), arrow gaps and codes.
- SL / TP: method, ATR multiples, risk-reward levels, line length and expiry.
- Dashboard: position, size, auto font, transparency, start minimized.
- Alerts: popup, push, sound.

### Notes

- The indicator draws on a chart canvas and needs no DLLs, no web requests and no extra files.
- It is an analysis tool. It does not open or close trades.
- Open-source component: the adaptive trend engine and the trend fill are based on "Machine Learning Adaptive SuperTrend" by AlgoAlpha and its MQL5 port by Trung, both under the Mozilla Public License 2.0. The source of these two files (Ritz_TTA_KMeansST.mqh and Ritz_TTA_StFill.mqh, with my modifications) is available at: [PUT THE LINK TO THE PUBLISHED SOURCE HERE].
- Everything else (Fast / Slow combination, sideway zones, HeatBar, structure reasons, Fibonacci channel, SL / TP, dashboard) is original work.

### Risk warning

Trading leveraged products carries a high level of risk and you can lose more than your deposit. The signals, zones and levels shown by this indicator are information for your own analysis and not investment advice. Past behavior of the indicator does not guarantee future results. Test on a demo account first and use proper risk management.

---

## 3. Deskripsi singkat (Bahasa Indonesia, opsional)

**Ritz TwinTrend Adaptive** menampilkan dua garis trend adaptif volatilitas (Fast dan Slow) dalam satu indikator. Volatilitas dikelompokkan dengan K-Means ke tiga kondisi (tinggi, sedang, rendah), sehingga garis menyesuaikan pasar saat ini.

Fitur utama:
- Fill gradient untuk Fast dan Slow, serta status COMBINE (kedua trend searah atau tidak).
- Panah BUY / SELL di garis trend, dengan teks kecil dan alasan (BoS, CHoCH, volume) serta skor.
- Peringatan sideway sebagai zona canvas, dengan filter spam tick.
- HeatBar untuk tekanan dan breakout dari zona sideway.
- Fibonacci Channel untuk melihat diagonal trend dan batasnya.
- Garis SL dan TP1 sampai TP3 yang singkat dan kedaluwarsa.
- Dashboard Canvas dengan tab trend semua timeframe (FAST / SLOW / COMBINE), bisa digeser, diminimize, dan ukuran teks otomatis.
- Bekerja di semua simbol dan timeframe, termasuk MN dengan history pendek (minimal 50 bar).

Mesin trend dan fill berbasis AlgoAlpha dan port MQL5 oleh Trung (MPL-2.0); sumbernya dipublikasikan terpisah.

Indikator ini alat analisis dan tidak membuka atau menutup posisi. Trading berisiko tinggi dan bukan nasihat investasi.
