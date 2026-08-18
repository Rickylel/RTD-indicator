# RTD-indicator
IFVG indicator

# DISCLAIMER
This indicator is for educational and informational purposes only. It does 
NOT constitute financial advice. Trading financial markets involves high risk, 
including the possible loss of principal. Past performance is not indicative 
of future results. You are solely responsible for your own trading decisions.

# Comments
after that, so this is an iFVG indicator that is going to be open source, everyone can use it, modify it or use it as a base for ur own indicator, it's very similar to an very famous iFVGS Content Creator indicator, so im going to explain very briefly what it does.

# Features

# 1. IFVG Detection Engine
  - Detects Fair Value Gaps and tracks their inversion (IFVG) once price closes through them.
  - Two detection modes: Single (merges consecutive gaps into one block) and Series (keeps each FVG separate).
  - Adjustable sensitivity (Strict / Normal / Sensitive) and configurable formation window (6 or up to 15 candles).

# 2. Entry Signal Engine (RTD+/RTD−)
  - Generates bullish (RTD+) and bearish (RTD−) setups when an IFVG forms in the context of:
    - A liquidity sweep (buy-side/sell-side),
    - An HTF Fair Value Gap reaction ("PDA delivery"),
    - Or SMT divergence.
  - Each setup is scored with a letter grade (A+ to C) based on premium/discount positioning and candle momentum, filtered by      a minimum grade threshold.
  - Includes an anti-front-run filter to invalidate setups where the signal candle already swept its own first target.

#  3. Liquidity & Market Structure
  - Structural Buy-Side/Sell-Side Liquidity (BSL/SSL) from swing pivots, with automatic or manual alignment timeframe.
  - Relative Equal Highs/Lows (REQH/REQL) detection with tick-based tolerance.
  - Session liquidity: highs/lows for NY AM, Lunch, NY PM, London, and Asia sessions.
  - PDH/PDL (Previous Day High/Low) and PWH/PWL (Previous Week High/Low).
  - Liquidity sweep tracking with a timeout/confirmation mechanism to distinguish genuine sweeps from structural breaks.

# 4. Higher-Timeframe (HTF) Fair Value Gaps
  - Auto-plots FVGs from 5M, 15M, and 1H timeframes with a merging engine that fuses overlapping/stacked gaps into a single        "liquidity void."
  - Optional midline (Consequent Encroachment / CE) for each HTF FVG.
  - Displacement filter (ATR-based) to ignore insignificant gaps.
  - Nested/lower-timeframe FVG cleanup to reduce chart clutter.

# 5. SMT Divergence (SMT Pro+)
  - Compares the current symbol against a correlated asset (auto-paired for NQ/ES/YM/GC, or manually selected).
  - Detects synchronized pivots and flags divergence when one asset sweeps liquidity while the correlated asset fails to.
  - Includes deduplication and anti-nesting logic to avoid redundant divergence signals.

# 6. Macro Data High/Low (currently working on this cuz I don't have the idea of how to make it wok)
  - Automatically flags the high or low of the 8:30 AM (NY time) news candle across any timeframe, with a minimum wick-size        filter.
  - Tracks mitigation and can auto-clean after a configurable number of bars.

# 7. Risk Management & Visual Execution Plan
  - Configurable stop-loss placement: Wick/Swing, iFVG Border, or Fixed Points.
  - Automatic position sizing (contracts) based on account balance and risk % per trade.
  - Draws SL, Break-Even, TP1, and TP2 levels, dynamically selected from the nearest available liquidity/FVG/structure targets     ("Draw On Liquidity" — DOL scan), with minimum separation logic to avoid stacked targets.
  - Setups are tracked live: stopped out, break-even, partial (TP1), or full win (TP2), with the option to keep or hide            winning/losing setups on the chart.

# 8. Killzone Filters & Session Backgrounds
  - Configurable killzone sessions (NY AM, NY Lunch, NY PM, London, Asia) with optional background boxes.
  - A strict killzone filter can downgrade/block setups formed outside your selected trading sessions.

# 9. Dashboard & Statistics Panels
  - Checklist dashboard: shows live confluence status (HTF Bias, Liquidity Sweep, iFVG, Momentum, HTF PDA Delivery,                Premium/Discount, DOL, SMT, Grade, Position Size).
  - Statistics panel: tracks win/loss/break-even counts per grade tier (A+, A, B), resettable by session and/or by day.
  - Both panels are fully configurable (position, text size, colors).

# 10. Optional HTF Auto-Bias
  - An internal bias engine (1H + 4H structure) can automatically determine market bias instead of a manual                        bullish/bearish/neutral input.

# Notes
  - All drawing objects use xloc.bar_time for precise time-based anchoring.
  - Built with performance in mind: object pooling, garbage collection loops, and configurable display limits                      (max_lines_count,    max_boxes_count, max_labels_count) keep the chart responsive.

# Author
r1ckylel/RTD
