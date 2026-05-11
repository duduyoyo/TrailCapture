# TrailCapture

A fully native automated trading and OAuth authentication engine designed for capturing intraday price movements without manual intervention.

TrailCapture introduces a flexible trailing strategy engine capable of dynamically tracking both downtrends and uptrends while providing a seamless automated OAuth login experience for Schwab accounts — eliminating the manual authorization interruptions required by existing solutions.

---

# Features

## 📉 Intelligent Downtrend Tracking

TrailCapture allows you to dynamically monitor downward price movement and capture reversal opportunities with customizable controls.

### Supported Features

* Configure a trigger price to start tracking a downtrend
* Ignore a configurable number of consecutive downward ticks before monitoring reversal behavior
* Specify an absolute price movement threshold between the first and last downward ticks
* Once the configured downtrend conditions are satisfied, TrailCapture automatically begins tracking the next upward tick for potential capture

### Example

```text id="r1"
Start tracking after price drops below trigger
Ignore first N down ticks
Require absolute drop >= configured threshold
Capture first qualifying upward reversal tick
```

---

## 📈 Intelligent Uptrend Tracking

TrailCapture also supports symmetrical upward trend tracking.

### Supported Features

* Configure a trigger price to begin monitoring upward movement
* Ignore a configurable number of consecutive upward ticks
* Require an absolute upward price movement threshold between the first and last upward ticks
* After the configured uptrend conditions are satisfied, TrailCapture automatically tracks the first downward reversal tick

### Example

```text id="r2"
Start tracking after price rises above trigger
Ignore first N up ticks
Require absolute rise >= configured threshold
Capture first qualifying downward reversal tick
```

---

# 🔐 Fully Automated OAuth Authentication for Schwab

One of the biggest pain points in automated trading systems is OAuth authentication maintenance.

Most current solutions rely on:

* manual browser interaction
* Playwright
* Selenium
* Puppeteer
* authorization-code copy/paste workflows
* periodic manual re-login

TrailCapture takes a fundamentally different approach.

## What Makes TrailCapture Different

### ✅ No manual authorization pause

Existing solutions typically require users to:

1. pause automation
2. manually retrieve authorization code
3. resume token refresh process

TrailCapture eliminates this workflow entirely.

### ✅ Pure native engine

* No browser automation frameworks
* No Selenium
* No Playwright
* No Puppeteer
* No third-party browser control dependency

### ✅ Seamless token lifecycle

* automatic login
* automatic token refresh
* automatic token renewal
* no periodic manual intervention required

This architecture enables a significantly smoother long-running automated trading workflow.

---

# Prerequisites

## 1. Microsoft Visual C++ Runtime (x64)

TrailCapture requires the Microsoft Visual C++ Redistributable Runtime for x64 Windows systems.

Download from Microsoft:

[Microsoft Visual C++ Redistributable (x64)](https://aka.ms/vs/17/release/vc_redist.x64.exe)

Supported platforms:

* Windows 10 x64
* Windows 11 x64

---

## 2. Approved Schwab Developer Application

You must have an approved developer application from [Charles Schwab Developer Portal](https://developer.schwab.com) in order to obtain:

* App Key (Client ID)
* App Secret
* Callback URL

These values must be configured within TrailCapture before authentication can function properly.

---

## 3. Regular Schwab Brokerage Account

A standard Schwab brokerage account is required for automated login.

You will need:

* Schwab username
* Schwab password

⚠️ Note:

* This is NOT the Schwab developer portal account
* The developer account alone cannot be used for trading authentication
* OAuth authentication must be performed against a regular brokerage account

---

## 4. Usage

If you have multiple trading accounts and need to select a specific one, you can configure this using `config.xml`.

Place the file in:

```text id="u1"
C:\ProgramData\TrailingPro
```

Otherwise, the first account will be used by default.

⚠️ Currently, only one account is supported.

Example configuration:

```xml id="u2"
<Config>
	<AccountIndex>
		<Value>0</Value>
	</AccountIndex>
</Config>
```

Account indexing is zero-based:

* `0` = first account
* `1` = second account
* `2` = third account
* etc.

If an invalid account index is specified, authentication or token generation may fail.

---
# Technical Highlights

* Native C/C++ implementation
* Lightweight architecture
* No browser automation frameworks
* Designed for long-running unattended execution
* Flexible trend tracking engine
* Event-driven trailing logic
* OAuth automation workflow integrated directly into native runtime

---

# Use Cases

* Automated trading systems
* Intraday range capture strategies
* Schwab API integrations
* Native low-latency trading tools
* Long-running unattended trading workflows

---

# Philosophy

TrailCapture was built from a first-principles perspective:

Instead of automating a browser externally, the project focuses on understanding and integrating the underlying authentication and price-tracking mechanisms directly within a native engine.

The result is a lightweight, automated, and developer-oriented solution focused on stability, flexibility, and uninterrupted execution.

---

# Disclaimer

This project is intended for educational and research purposes only.

Users are responsible for complying with:

* Schwab API Terms of Service
* OAuth provider policies
* trading regulations and brokerage agreements

Use at your own risk.

---

# Screenshots

<img width="1149" height="632" alt="image" src="https://github.com/user-attachments/assets/a0f5eef3-643d-4426-a28a-b87cc518e3f9" />

<img width="1150" height="626" alt="image" src="https://github.com/user-attachments/assets/7c14f5bf-eb00-4e19-9526-abb531f13e42" />

