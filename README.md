# 🤖 Android RCA Analyzer

> **AI-powered Android Defect Root Cause Analysis Tool**  
> Built for Senior QA Architects, Framework Engineers & Android Debug Specialists

[![Made with Claude](https://img.shields.io/badge/Powered%20by-Claude%20AI-7c3aed?style=flat-square)](https://anthropic.com)
[![HTML](https://img.shields.io/badge/Tech-HTML%20%7C%20JS%20%7C%20CSS-00d4aa?style=flat-square)]()
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](LICENSE)

---

## 🎯 What It Does

A single-file, browser-based tool that accepts Android bug reports and diagnostic artifacts, then uses Claude AI to produce a **complete 8-step Root Cause Analysis** in seconds.

### 8-Step Investigation Flow

| Step | Description |
|------|-------------|
| 1️⃣ Categorize Defect | Crash · ANR · Camera Failure · Performance · Battery · Memory Leak · Thermal · UI · Connectivity · Sensor |
| 2️⃣ Log Analysis | Exception type · Stack trace · Error codes · Thread info · Process name |
| 3️⃣ Framework Mapping | Application → Framework → HAL → Kernel → Vendor → Driver layers |
| 4️⃣ Root Cause | Immediate cause · Underlying cause · Trigger condition · Dependency failure |
| 5️⃣ Confidence Score | High (>90%) · Medium (70–90%) · Low (<70%) with reasoning |
| 6️⃣ Fix Recommendation | Developer fix · Config fix · Workaround · Validation plan |
| 7️⃣ Risk Assessment | Severity · Customer impact · Production risk |
| 8️⃣ Automation | Suggested regression, smoke, stress, monkey test cases |

---

## 🚀 How to Use

### Option 1 — Open Directly in Browser
```bash
# Clone the repo
git clone https://github.com/vanichalla24/android-rca-analyzer.git
cd android-rca-analyzer

# Open in browser
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

### Option 2 — GitHub Pages
Enable GitHub Pages on this repo (`Settings → Pages → Deploy from branch: main`) and access it at:
```
https://vanichalla24.github.io/android-rca-analyzer/
```

---

## 📋 Inputs Supported

| Input | Field |
|-------|-------|
| Device Model | Samsung Galaxy S25 Ultra, Pixel 9, etc. |
| Android Version | Android 14, 15, etc. |
| Build Version | S928BXXS3AYA1, etc. |
| Affected Module | Samsung Camera, Settings, etc. |
| Bug Description | Free text |
| Reproduction Steps | Free text |
| Logcat Logs | Raw logcat paste |
| ANR Traces / Tombstone | Raw paste |
| Camera / Framework Logs | HAL, CameraService logs |
| Perfetto / Battery / Memory | Trace summaries |

All log fields are **optional** — the AI works with whatever you provide.

---

## 📊 Output Format

```
═══════════════════════════════
BUG SUMMARY
═══════════════════════════════
Issue Type       | ANR
Affected Module  | com.samsung.android.camera
Severity         | Critical (P1)
Exception Type   | android.app.RemoteServiceException
Process          | com.samsung.android.camera
Thread           | main

FRAMEWORK LAYER MAP
Application Layer  → AFFECTED
Framework Layer    → SECONDARY
HAL Layer          → CLEAN
...

ROOT CAUSE ANALYSIS
Primary Cause    | Binder thread pool exhaustion in CameraService
Secondary Cause  | Upstream HAL callback timeout not handled
Confidence       | High · 91%

FIX RECOMMENDATION
Developer Fix    | Increase binder thread pool size, add timeout handler
Workaround       | Force-stop camera app, clear cache

AUTOMATION TESTS
1. [Regression] Camera Launch Stress Test
2. [Monkey]     Random camera gesture stress under low memory
3. [Regression] ANR detection on camera open/close cycle
═══════════════════════════════
```

---

## 🏗️ Architecture

```
index.html
├── Tab 1: Bug Input       — Device, version, description, category tags
├── Tab 2: Logs & Traces   — Logcat, ANR, HAL logs, Perfetto
└── Tab 3: RCA Report      — AI-generated full 8-step analysis
         ├── Bug Summary
         ├── Framework Layer Map (visual grid)
         ├── Root Cause Chain
         ├── Fix Recommendations
         ├── Risk Assessment
         ├── Automation Test Suggestions
         └── Prevention Strategy
```

**Tech Stack:** Pure HTML + Vanilla JS + CSS · No dependencies · Single file · Claude Sonnet 4.6 API

---

## 👩‍💻 Built By

**Vaani Challa** — QA Architect & Technical Manager  
Samsung R&D Institute India (SRIB), Bangalore  
17+ years · Galaxy S-series Camera QA Lead (S22–S26)  
🏆 Best Award — Galaxy S25 & S26 Camera Quality  

GitHub: [@vanichalla24](https://github.com/vanichalla24)

---

## 📄 License

MIT License — free to use, modify, and distribute.
