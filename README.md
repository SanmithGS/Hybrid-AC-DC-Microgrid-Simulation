# 🔌 Hybrid AC/DC Microgrid Simulation (Grid-Connected Mode)

## Overview

A MATLAB/Simulink simulation of a **Hybrid AC/DC Microgrid** based on the **IEEE 14-Bus test system**, operating in **grid-connected mode**. The model performs comprehensive power quality analysis including voltage profiling, active/reactive power balancing, power factor assessment, line loss estimation, and Total Harmonic Distortion (THD) evaluation — all validated against IEEE standards.

---

## 🛠️ Tools & Environment

| Tool | Version | Purpose |
|------|---------|---------|
| MATLAB | R2025a | Scripting, post-processing & analysis |
| Simulink | R2025a | System modeling & simulation |
| Simscape Electrical | R2025a | Power electronic component modeling |

---

## 🏗️ System Architecture

| Subsystem | Description |
|-----------|-------------|
| **AC Grid** | IEEE 14-bus network (Bus2AC–Bus16AC) as utility reference |
| **DC Bus** | Central DC link interconnecting distributed energy resources |
| **Generation Sources** | Diesel generator (Bus8AC), Grid & converter sources (Bus12AC, Bus14AC) |
| **Load Centers** | High-consumption buses at Bus4AC, Bus6AC, Bus10AC |
| **Converters** | AC/DC and DC/DC converters for bus coupling |
| **Controller** | PLL-based grid synchronization with proportional control (Kp, Kq) |

---

## 📁 Project Structure

```
Hybrid-AC-DC-Microgrid-Simulation/
│
├── Model/                  # Simulink models (.slx)
├── Matlab codes/           # MATLAB analysis scripts
├── Data/                   # Input parameters and load profiles
├── Results/                # Simulation waveforms and plots
└── Documentation/          # Project report and system diagrams
```

---

## ▶️ How to Run

1. Open **MATLAB R2025a** (or compatible version)
2. Navigate to the `Model/` folder
3. Open the `.slx` Simulink model file
4. Click **Run** (`Ctrl+T`)
5. View results in Scope blocks or export to `Results/`

> ⚠️ Requires **Simscape Electrical** toolbox. Ensure it is installed via MATLAB Add-Ons Manager.

---

## 📊 Simulation Results

### Voltage Profile
| Metric | Value |
|--------|-------|
| Acceptable voltage range (IEEE standard) | 0.95 – 1.05 pu |
| Buses within acceptable range | Most buses ✅ |
| Bus2AC status | Undervoltage risk ⚠️ |
| Bus14AC status | Significant voltage drop (reactive absorption) ⚠️ |
| ADVS — Phase a | 0.0568 pu |
| ADVS — Phase b | 0.0412 pu |
| ADVS — Phase c | 0.0499 pu |

> ADVS (Average Deviation from Voltage Set-point) computed as `mean(abs(V_pu - 1))` across all buses.

---

### Active & Reactive Power Balance
| Bus | Role | Observation |
|-----|------|-------------|
| Bus8AC | Diesel Generator | Major active power source |
| Bus12AC, Bus14AC | Grid + Converter | Supporting generation nodes |
| Bus4AC, Bus6AC, Bus10AC | Load Centers | Highest active power consumption |

- ✅ Active and reactive power well distributed across all 3 phases
- ✅ Effective operation under high demand with distributed generation support
- ⚠️ Bus6AC — peak reactive power injection ~1,500 VAR
- ⚠️ Bus14AC — reactive power absorption ~−2,100 VAR, indicating voltage stress

---

### Power Factor Analysis
| Bus | Power Factor | Status |
|-----|-------------|--------|
| Bus10AC, Bus12AC | ~1.0 (near unity) | ✅ Best — efficient & balanced |
| Bus4AC, Bus8AC | ~0.75 – 0.80 | ⚠️ Moderate |
| Bus2AC, Bus6AC | ~0.40 – 0.45 | ❌ Lowest — high reactive flow |
| Bus14AC | ~0.50 – 0.60 | ❌ Load-heavy bus |

> System would benefit from reactive power compensation (capacitor banks or STATCOM) at Bus2AC and Bus6AC.

---

### Power Losses per Line
| Line | Losses | Cause |
|------|--------|-------|
| Line4AC, Line8AC | ~9–10 kW ❌ Highest | Long distance + high current + low PF |
| Line2AC, Line10AC | ~2–5 kW ⚠️ Moderate | Moderate loading |
| Line6AC, Line12AC, Line14AC | < 1 kW ✅ Minimal | Low loading, good PF |

- ✅ Phase losses (a, b, c) balanced in most lines
- ⚠️ Slight phase imbalance in heavily loaded lines (Line4AC, Line8AC)

---

### Total Harmonic Distortion (THD)
| Metric | Value |
|--------|-------|
| THD range (all buses, all phases) | 2.3% – 3.5% |
| IEEE 519 compliance limit | < 5% |
| Compliance status | ✅ All buses compliant |
| Highest THD | Phase C — up to **3.4%** at Bus2AC & Bus12AC |
| Lowest THD | **2.3%** at Bus6AC & Bus10AC |

> Minor inter-phase THD variation observed — indicates slight harmonic imbalance but acceptable power quality per IEEE 519 standard.

---

## 🔑 Key Concepts Demonstrated

- Hybrid AC/DC microgrid architecture and IEEE 14-bus power system modeling
- Three-phase power flow analysis — active (P), reactive (Q), apparent (S)
- Voltage profile monitoring with ADVS deviation quantification
- Power factor computation (PF = P/S) and I²R line loss assessment
- THD analysis via FFT — benchmarked against IEEE 519 Standard (< 5%)
- PLL-based grid synchronization control
- Proportional control law for power balance correction (ΔP, ΔQ)

---

## 👤 Author

**Sanmith G S**

- 🎓 M.Tech – Smart Electric Grid, **NIT Warangal**
- 🎓 B.E – Electrical & Electronics Engineering, **BMS College of Engineering, Bengaluru**
- 🔗 [LinkedIn](https://www.linkedin.com/in/sanmith-g-s)
- 📧 sannysanmith@gmail.com
