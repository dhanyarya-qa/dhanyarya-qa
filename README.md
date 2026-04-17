<div align="center">

# 📱 Mepo Travel — Appium E2E Automation

### Android Mobile App Testing Framework

[![Appium](https://img.shields.io/badge/Appium_2.x-662D8C?style=flat-square&logo=appium&logoColor=white)](https://appium.io/)
[![Python](https://img.shields.io/badge/Python_3.10+-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org/)
[![Pytest](https://img.shields.io/badge/Pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)](https://pytest.org/)
[![Android](https://img.shields.io/badge/Android_API_33+-3DDC84?style=flat-square&logo=android&logoColor=white)](https://developer.android.com/)

*End-to-end mobile automation for the Mepo Travel Android app — powered by Page Object Model, API-driven preconditions, and rich failure diagnostics.*

</div>

---

## ✨ Key Features

<table>
<tr>
<td width="50%">

### 🎯 Test Scenarios
- 🔐 **Login Flow** — Splash → Welcome → Login → Home
- 🔍 **Open Trip Discovery** — Search, filter, book
- 💰 **Budget Tracking** — Expense management
- 🛡️ **Permission Handling** — Auto-grant & dismiss

</td>
<td width="50%">

### 🔬 Framework Features
- 🏗️ **Page Object Model (POM)** — Clean separation
- 🔌 **API-Driven Preconditions** — Seed test data
- 📸 **Auto Screenshots** — Capture on failure
- 📝 **Rich Logging** — Timestamped test logs

</td>
</tr>
</table>

---

## 🏗️ Architecture

```
mepo-appium/
├── config/
│   ├── __init__.py
│   └── settings.py              # Appium caps, API endpoints, test data
├── pages/
│   ├── __init__.py
│   ├── base_page.py             # Common interactions (wait, tap, scroll)
│   ├── splash_page.py           # Splash & welcome screens
│   ├── login_page.py            # Authentication flow
│   ├── home_page.py             # Home/Dashboard navigation
│   ├── open_trip_page.py        # Open Trip Discovery page object
│   └── budget_page.py           # Budget Tracking page object
├── tests/
│   ├── __init__.py
│   ├── conftest.py              # Fixtures, driver lifecycle, reporting
│   ├── test_login.py            # Login E2E scenarios
│   └── test_advanced_features.py # Open Trip & Budget scenarios
├── utils/
│   ├── __init__.py
│   └── api_helper.py            # API client for pre/post-conditions
├── reports/
│   ├── logs/                    # Test run logs (auto-generated)
│   └── screenshots/             # Failure screenshots (auto-captured)
├── apps/                        # Place APK file here
├── .env.example                 # Environment variable template
├── pytest.ini                   # Pytest configuration
├── requirements.txt             # Python dependencies
└── README.md
```

---

## 📋 Prerequisites

| Component | Version | Purpose |
|-----------|---------|---------|
| Python | ≥ 3.10 | Test runtime |
| Appium Server | ≥ 2.x | Mobile automation server |
| Android SDK | API 33+ | Android platform tools |
| Java JDK | ≥ 11 | Required by UiAutomator2 |
| Node.js | ≥ 18 | Appium server runtime |

---

## 🚀 Quick Start

```bash
# 1. Clone repository
git clone https://github.com/dhanyarya-qa/mepo-appium.git
cd mepo-appium

# 2. Install Python dependencies
pip install -r requirements.txt

# 3. Configure environment
cp .env.example .env
# Edit .env with your actual values

# 4. Start Appium Server (separate terminal)
appium --relaxed-security

# 5. Start Android Emulator or connect device
emulator -avd Pixel_6_API_33

# 6. Place Mepo APK in ./apps/ directory
```

---

## ▶️ Running Tests

```bash
# All tests
pytest tests/ -v -s

# Login flow only
pytest tests/test_login.py -v -s

# Advanced features (Open Trip + Budget)
pytest tests/test_advanced_features.py -v -s

# Open Trip scenarios only
pytest tests/test_advanced_features.py -v -s -k "open_trip"

# Budget Tracking only
pytest tests/test_advanced_features.py -v -s -k "budget"

# Generate HTML report
pytest tests/ -v -s --html=reports/report.html
```

---

## 🧪 Test Scenarios

### Scenario 1: Login Flow 🔐

| Step | Action | Validation |
|------|--------|------------|
| 1 | App launch from fresh state | Splash screen appears |
| 2 | Handle welcome/onboarding | Navigate past splash |
| 3 | Navigate to login page | Login form visible |
| 4 | Enter credentials | Fields populated |
| 5 | Submit login | Home screen reached ✅ |

### Scenario 2: Open Trip Discovery 🔍

| Step | Action | Validation |
|------|--------|------------|
| 1 | Navigate to Open Trip menu | Search bar displayed |
| 2 | Search "Bandung" | Results count > 0 |
| 3 | Apply Wisata Alam + Kuliner filters | Filtered results > 0 |
| 4 | Select first trip | Detail page with title |
| 5 | Check departure schedule | Available dates > 0 |
| 6 | Validate Booking button | Button enabled & clickable |

### Scenario 3: Budget Tracking 💰

| Step | Action | Validation |
|------|--------|------------|
| 1 | Open active itinerary | Itinerary tab accessible |
| 2 | Navigate to Budget tab | Budget page loads |
| 3 | Add expense: Rp 500.000 (Makanan) | Form submits successfully |
| 4 | Validate total expense update | Display contains "500.000" |

---

## ⚙️ Permission Dialog Handling

```python
# Auto-handled via Appium capabilities
"appium:autoGrantPermissions": True,
"appium:autoAcceptAlerts": True,
```

Fallback: `BasePage.dismiss_permission_dialog()` catches any remaining dialogs.

---

## 📊 Reporting

| Report Type | Location |
|-------------|----------|
| 🖥️ Terminal | PASS (✅) / FAIL (❌) per flow |
| 📝 Logs | `reports/logs/test_run_YYYYMMDD_HHMMSS.log` |
| 📸 Screenshots | `reports/screenshots/` (auto on failure) |
| 📄 HTML Report | `pytest --html=reports/report.html` |

---

<div align="center">

**Built with ❤️ by [Dhany Arya Pratama](https://github.com/dhanyarya-qa)**

</div>
