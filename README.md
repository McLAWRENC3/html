# Ultimate Trade Assistant for MT5 – Complete Requirements Document

**Version:** 1.0  
**Date:** 2026-04-22  
**Project:** Ultimate Trade Assistant for MetaTrader 5  
**Based on:** Analysis of 10 top MQL5 products + reference code `phone_telegram_sender_proj2.mq5`

---

## 1. Core Architecture & GUI Framework

### 1.1 Main Dashboard (Home Page)

| Requirement | Description |
|-------------|-------------|
| **Modular Button Navigation** | Main GUI window displays category buttons that open dedicated sub-windows (similar to reference code's group toggles). |
| **Minimize/Maximize** | Collapse main panel to compact status bar. |
| **Draggable Interface** | User can reposition all windows on chart. |
| **Theme Support** | Minimum 5 color themes (Dark, Light, Blue, Green, Professional Black). |
| **Multi-Language** | English, Chinese, Spanish, Arabic, Russian (expandable). |
| **Settings Persistence** | Save/load all configurations to/from files. |

### 1.2 Main Menu Buttons (Core Categories)

| Button | Opens Window |
|--------|--------------|
| Trade Execution | Order entry with risk tools |
| Telegram Signals | Multi-provider signal copier |
| Trade Copier | Local account trade synchronization |
| Grid/Martingale | Grid trading system |
| Risk Manager | Account protection settings |
| Analytics | Performance statistics |
| Settings | Global configuration |

---

## 2. Trade Execution & Order Management

### 2.1 Order Entry Panel

| Feature | Description |
|---------|-------------|
| **Market Orders** | One-click Buy/Sell with pre-configured SL/TP. |
| **Pending Orders** | Buy Limit, Sell Limit, Buy Stop, Sell Stop. |
| **Order Modification** | Drag lines on chart to adjust entry/SL/TP (like Trade Dashboard). |
| **Order Expiry** | Set time expiration for pending orders. |
| **OCO Orders** | One-Cancels-Other – pair of pending orders where one execution cancels the other. |
| **Virtual Pending Orders** | Hidden pending orders not visible to broker. |

### 2.2 Position Sizing Calculator

| Feature | Description |
|---------|-------------|
| **Risk-Based Sizing** | Calculate lot size based on stop loss distance and risk %. |
| **Fixed Lot** | Manual lot size override. |
| **Risk Amount ($)** | Fixed dollar risk per trade. |
| **Risk % of Balance** | Percentage of current balance. |
| **Risk % of Equity** | Percentage of current equity. |
| **Risk % of Free Margin** | Based on available margin. |
| **Auto-Adjust on SL Move** | Recalculate lot when stop loss is moved (DashPlus feature). |

### 2.3 Risk-to-Reward Tools

| Feature | Description |
|---------|-------------|
| **R:R Ratio Presets** | 1:1, 1:2, 1:3, 1:4, 1:5, custom. |
| **R/TP Button** | Set TP automatically based on SL × ratio. |
| **R/SL Button** | Set SL automatically based on TP ÷ ratio. |
| **Visual R:R Tool** | Draggable lines showing entry, SL, TP with real-time ratio display. |
| **Multiple TP Levels** | Up to 5 TP levels with partial closes. |

### 2.4 Chart Visualization

| Feature | Description |
|---------|-------------|
| **Entry Line** | Horizontal line showing planned entry. |
| **Stop Loss Line** | Red line, draggable. |
| **Take Profit Line(s)** | Green line(s), draggable. |
| **Risk Display** | Shows $ risk, lot size, R:R ratio. |
| **Magnet to Price** | One-click snap lines to current market price. |
| **Hotkey Toggle** | Show/hide all trading lines. |

---

## 3. Trade Management Features

### 3.1 Trailing Stop (8 Types)

| Type | Description |
|------|-------------|
| **Standard Pip Trail** | Move SL by X pips behind price. |
| **ATR-Based** | Trail by multiplier of ATR value. |
| **Moving Average** | Trail using MA cross. |
| **Parabolic SAR** | Trail using PSAR indicator. |
| **Fractal** | Trail using fractal highs/lows. |
| **High/Low Bar** | Trail using last N bars' extreme. |
| **Partial Close Trail** | Close portion at each trail step. |
| **Multi-Level Trail** | Different trail distances at different profit levels. |

**Activation Trigger:** Trail only starts after profit reaches X pips/$.

### 3.2 Breakeven Management

| Feature | Description |
|---------|-------------|
| **Basic BE** | Move SL to entry after X profit. |
| **BE + Offset** | Move SL to entry + X pips (lock small profit). |
| **Multi-Level BE** | Up to 4 BE levels (e.g., BE at +10, BE+5 at +20, BE+10 at +30). |
| **Commission Compensation** | BE offset covers spread/commission costs. |
| **Virtual BE** | Hidden from broker. |

### 3.3 Partial Close System

| Feature | Description |
|---------|-------------|
| **TP-Based Partial** | Close X% at each TP level. |
| **Pip-Based Partial** | Close X% at specified pip distance. |
| **R:R Based Partial** | Close at 1R, 2R, 3R, etc. |
| **Volume Options** | Close by fixed lot, % of current lot, or % of initial lot. |
| **Up to 8 Partial Levels** | Configurable per position. |

### 3.4 Advanced Position Management

| Feature | Description |
|---------|-------------|
| **Close by Groups** | Close all Buys / all Sells / all positions. |
| **Close by Profit/Loss** | Close only profitable or only losing trades. |
| **Reverse Position** | Close and open opposite. |
| **Hedge/Lock** | Open opposite position with matching volume. |
| **Bulk SL/TP** | Set same SL/TP for all positions on symbol. |
| **Mobile Trade Management** | Manage trades opened from phone (reference code feature). |

---

## 4. Grid & Martingale Systems

### 4.1 Recovery Grid (Averaging)

| Feature | Description |
|---------|-------------|
| **Grid Distance** | Pip spacing between orders. |
| **Lot Multiplier** | 1x, 1.5x, 2x, Fibonacci. |
| **Max Levels** | Limit number of grid steps. |
| **TP for Grid** | Single TP for entire grid or per order. |
| **SL for Grid** | Single SL for entire basket. |
| **Reverse Grid** | Open opposite direction grid after X losses. |

### 4.2 Stack Grid (Pyramiding)

| Feature | Description |
|---------|-------------|
| **Trend Following** | Add positions in profit direction. |
| **Distance Based** | Add every X pips. |
| **Indicator Based** | Add on MA cross, MACD, RSI. |
| **Max Positions** | Limit total pyramid levels. |

### 4.3 Basket Management

| Feature | Description |
|---------|-------------|
| **Basket BE Price** | Show average price on chart. |
| **Basket SL/TP** | Set unified SL/TP for all positions on symbol. |
| **Basket Close** | Close entire basket at target equity. |
| **Hedge Basket View** | Separate Buy/Sell basket statistics. |

---

## 5. Telegram Signal Integration

*Based on reference code `phone_telegram_sender_proj2.mq5` and Telegram To MT5 Signal Trader*

### 5.1 Multi-Provider Support

| Feature | Description |
|---------|-------------|
| **Multiple Channels** | Support up to 10 Telegram groups/channels simultaneously. |
| **Public Channels** | Join and copy from public Telegram channels. |
| **Private Channels** | Support for private channels with invitation. |
| **Per-Provider Enable/Off** | Toggle each provider independently. |
| **Provider Naming** | Custom names for each signal source. |

### 5.2 Signal Recognition

| Feature | Description |
|---------|-------------|
| **Keyword Matching** | Detect signals by keywords (BUY, SELL, LONG, SHORT). |
| **Pattern Recognition** | Parse formats like "EURUSD BUY 1.2345 SL 1.2300 TP 1.2400". |
| **Placeholder System** | Configurable templates for signal parsing. |
| **Comment Filter** | Filter signals by comment/text content. |
| **Magic Number Filter** | Only process signals with specific magic numbers (reference code). |

### 5.3 Signal Execution Logic

| Feature | Description |
|---------|-------------|
| **Entry Offset** | Add/subtract pips from signal entry (prop firm protection). |
| **SL/TP Override** | Use custom SL/TP instead of signal values. |
| **Fixed Lots** | Ignore signal lot size, use fixed volume. |
| **Risk-Based Execution** | Calculate lot based on signal's SL distance. |
| **Multi-TP Support** | Execute up to 5 TP levels from signal. |
| **Partial Close Following** | Copy partial close commands. |

### 5.4 Telegram Connection

| Feature | Description |
|---------|-------------|
| **Bot Token Authentication** | Per-group bot tokens (reference code). |
| **Chat ID Configuration** | Target channel/group IDs. |
| **Test Message Button** | Send test notification. |
| **Connection Status** | Visual indicator for each provider. |
| **WebRequest Support** | HTTPS API calls to Telegram. |

### 5.5 Notification System

| Feature | Description |
|---------|-------------|
| **Trade Copied Alert** | MT5 alert when signal executed. |
| **Mobile Notification** | Push to MetaTrader mobile app. |
| **Email Report** | Daily signal execution summary. |
| **Screenshot Capture** | Auto-screenshot of executed trade. |

---

## 6. Local Trade Copier

### 6.1 Master/Slave Architecture

| Feature | Description |
|---------|-------------|
| **Master Mode** | Send trades from this terminal. |
| **Slave Mode** | Receive trades to this terminal. |
| **Multiple Slaves** | One master to many slaves. |
| **Multiple Masters** | One slave from many masters. |
| **Same Computer/VPS** | Copy between terminals on same machine. |

### 6.2 Copy Filters

| Feature | Description |
|---------|-------------|
| **Symbol Mapping** | Copy EURUSD → EURUSD or EURUSD → FXEURUSD. |
| **Lot Size Calculation** | Fixed lot, multiplier, percentage of original. |
| **SL/TP Sync** | Copy with offset or exact. |
| **Order Type Filter** | Copy only market orders, pending orders, or both. |
| **Magic Number Filter** | Only copy trades with specific magic. |
| **Comment Filter** | Copy based on order comment. |

### 6.3 Advanced Copy Features

| Feature | Description |
|---------|-------------|
| **Reverse Copying** | Copy Buy as Sell and vice versa. |
| **Slippage Control** | Max price difference tolerance. |
| **Time Delay Sync** | Max time lag before ignoring. |
| **Partial Close Sync** | Copy partial close operations. |
| **Back Copying** | Copy open positions on connection. |

### 6.4 Protection Features

| Feature | Description |
|---------|-------------|
| **Min Equity Stop** | Stop copying below equity threshold. |
| **Max Drawdown Stop** | Stop copying at drawdown limit. |
| **Daily Trade Limit** | Max copies per day. |
| **Daily Loss Limit** | Stop at daily loss amount. |
| **Time Filters** | Only copy during specified hours. |

---

## 7. Risk Management & Protection

### 7.1 Account Protection

| Feature | Description |
|---------|-------------|
| **Daily Loss Limit** | Close all at X% or X$ loss, block new trades. |
| **Weekly Loss Limit** | Reset weekly. |
| **Monthly Loss Limit** | Reset monthly. |
| **Daily Profit Target** | Close all at target, lock profits. |
| **Max Open Trades** | Limit concurrent positions. |
| **Max Lot per Trade** | Per-trade volume cap. |
| **Max Daily Trades** | Trade count limit. |

### 7.2 Overtrading Prevention

| Feature | Description |
|---------|-------------|
| **Time Between Trades** | Minimum seconds between entries. |
| **Trade per Hour Limit** | Max trades in rolling 60 minutes. |
| **Consecutive Loss Stop** | Stop after X losses in a row. |
| **Equity Curve Guard** | Stop if equity drops X% in Y minutes. |

### 7.3 News Filter

| Feature | Description |
|---------|-------------|
| **Economic Calendar** | Built-in news calendar. |
| **Impact Filter** | Block trades before high/medium impact news. |
| **Currency Matching** | Only block news affecting traded symbols. |
| **Pre-News Actions** | Close positions X minutes before news. |
| **Post-News Delay** | Wait X minutes after news before trading. |

### 7.4 Time Filters

| Feature | Description |
|---------|-------------|
| **Trading Hours** | Specify allowed trading times. |
| **Weekend Protection** | Auto-close or block on weekends. |
| **Session-Based** | Trade only during London, NY, Tokyo, Sydney sessions. |

---

## 8. Advanced Tools & Utilities

### 8.1 Task Scheduler

| Feature | Description |
|---------|-------------|
| **Time-Based Tasks** | Execute at specific time daily/weekly/monthly. |
| **Price-Based Tasks** | Execute when price hits level. |
| **Task Types** | Close all, take screenshot, send notification, open trade, change settings. |
| **Recurring Tasks** | Repeat every X minutes/hours. |

### 8.2 Alert System

| Feature | Description |
|---------|-------------|
| **Price Alerts** | Notify when price crosses level. |
| **Indicator Alerts** | Alert on MA cross, RSI level, etc. |
| **Support/Resistance Alerts** | Line break notifications. |
| **Alert Actions** | Chart popup, sound, push notification, email. |

### 8.3 Hotkeys

| Feature | Description |
|---------|-------------|
| **Trade Actions** | Buy, Sell, Close All, Breakeven. |
| **Chart Controls** | Zoom, scroll, timeframe change. |
| **Panel Controls** | Show/hide, minimize. |
| **Customizable** | User-assignable key combinations. |
| **Shift Modifier** | Alternative actions with Shift key. |

### 8.4 Auto SL/TP Setting

| Feature | Description |
|---------|-------------|
| **ATR-Based SL** | SL = ATR × multiplier. |
| **Candle-Based SL** | SL at recent swing high/low. |
| **Auto TP** | TP = SL × R:R ratio. |
| **For External Orders** | Add SL/TP to trades from mobile/other EAs (reference code feature). |

### 8.5 Virtual Levels (Stealth Mode)

| Feature | Description |
|---------|-------------|
| **Virtual SL** | Hide stop loss from broker. |
| **Virtual TP** | Hide take profit from broker. |
| **Virtual Pending Orders** | Hidden pending orders. |
| **Broker Protection** | Prevents stop hunting. |

---

## 9. Analytics & Reporting

### 9.1 Performance Dashboard

| Feature | Description |
|---------|-------------|
| **Win Rate** | % of profitable trades. |
| **Profit Factor** | Gross profit / gross loss. |
| **Average R:R** | Average risk-to-reward ratio. |
| **Max Drawdown** | Historical peak-to-trough. |
| **Sharpe Ratio** | Risk-adjusted return. |
| **Expectancy** | Average profit per trade. |

### 9.2 Trade History Visualization

| Feature | Description |
|---------|-------------|
| **Chart Overlay** | Show trades on price chart. |
| **Profit Labels** | Display $ profit per trade on chart. |
| **Filter Options** | Show only Buys/Sells/Profitable/Losing. |
| **Date Range Filter** | Analyze specific periods. |
| **Symbol Filter** | Per-symbol statistics. |

### 9.3 Export Functionality

| Feature | Description |
|---------|-------------|
| **CSV Export** | Export trade history to spreadsheet. |
| **Screenshot Export** | Save chart screenshots automatically. |
| **Report Generation** | Daily/weekly/monthly PDF reports. |

---

## 10. User Interface Specifications

### 10.1 Main Window (Home Page)


### 10.2 Popup Windows

Each button opens a dedicated window with:
- **Title bar** with minimize/close
- **Tabbed interface** for sub-features (reference code style)
- **Save/Load template** buttons
- **Apply/Close** action buttons

### 10.3 Input Controls (Reference Code Pattern)

- `CEdit` for numeric/text input with validation
- `CButton` with color-coded states (Green=ON, Red=OFF)
- `CLabel` for descriptive text
- `CComboBox` for dropdown selections

---

## 11. Technical Specifications

### 11.1 Compatibility

| Requirement | Specification |
|-------------|---------------|
| **Platform** | MetaTrader 5 only |
| **Account Types** | Netting and Hedging |
| **Asset Classes** | Forex, Indices, Commodities, Crypto, Stocks |
| **Broker Types** | Market Execution, Instant Execution |
| **Quote Formats** | 4-digit, 5-digit, and variable |

### 11.2 Performance

| Requirement | Specification |
|-------------|---------------|
| **Execution Speed** | <50ms from signal to order |
| **Tick Processing** | Non-blocking, OnTick() optimization |
| **Memory Usage** | <50MB RAM |
| **CPU Usage** | <5% on standard VPS |

### 11.3 Dependencies

| Requirement | Specification |
|-------------|---------------|
| **External DLLs** | None (pure MQL5) except WebRequest |
| **WebRequest** | Required for Telegram API |
| **Internet** | Required for Telegram signals |
| **Windows Version** | Windows 10+ / Server 2016+ |

---

## 12. Feature Priority Matrix

| Priority | Features |
|----------|----------|
| **P0 (Must Have)** | Trade Execution, Position Sizing, Basic SL/TP, Breakeven, Trailing Stop, Basic Telegram Copy |
| **P1 (High)** | Partial Close, Grid System, Local Copier, Risk Limits, OCO Orders, Virtual Levels |
| **P2 (Medium)** | News Filter, Task Scheduler, Analytics Dashboard, Hotkeys, Multiple TP Levels |
| **P3 (Nice to Have)** | AI Signal Suggestions, Social Trading Feed, Cloud Backup of Settings |

---

## 13. User Stories

1. **As a prop firm trader**, I want to set daily loss limits so I don't breach my drawdown rules.
2. **As a signal follower**, I want to copy signals from multiple Telegram channels with different risk per provider.
3. **As a scalper**, I want one-click order execution with pre-calculated risk based on ATR stop loss.
4. **As a grid trader**, I want to set up recovery grids with lot multipliers and basket TP.
5. **As a manual trader**, I want to drag lines on the chart to set my entry, SL, and TP visually.
6. **As a remote trader**, I want my phone trades to automatically get SL/TP from the EA (reference code feature).
7. **As a risk-averse trader**, I want virtual stops so my broker can't see my levels.
8. **As a multi-account manager**, I want to copy my trades from one master account to 10 slave accounts.

---

## 14. Success Criteria

| Criterion | Target |
|-----------|--------|
| No critical bugs in 7-day continuous operation | 100% |
| Order execution latency | <100ms |
| Telegram signal parse accuracy | >99% |
| GUI responsiveness | <50ms refresh |
| Memory leak | 0 bytes over 24 hours |



*End of Requirements Document*
