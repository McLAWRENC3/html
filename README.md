# html
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

---

## Day 1 Deliverables Summary

✅ Complete requirements document  
✅ Feature categorization (12 major modules)  
✅ GUI layout specification (main window + popups)  
✅ Priority matrix for development planning  
✅ Technical specifications for Day 2-3 implementation  

**Ready to proceed to Day 2: Building (Implementation)**

---

*End of Requirements Document*
