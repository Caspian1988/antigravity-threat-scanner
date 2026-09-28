# 🛡️ Comrade Sentinel v2 — Batch Threat & Scam Inspector

> A high-speed client-side cybersecurity triage console that extracts URLs from unformatted text, runs multi-vector heuristic risk scoring, and validates domains against the Google Safe Browsing API.

[![Live Demo](https://img.shields.io/badge/Demo-Live%20Threat%20Scanner-00e5ff?style=for-the-badge&logo=shield)](https://caspian1988.github.io/antigravity-threat-scanner/)

---

## 📌 The Problem It Solves

Modern phishing and social engineering campaigns (smishing, spear-phishing, delivery alert scams) often flood users with deceptive links disguised as reputable brands or hidden under disposable top-level domains (TLDs). 

Manually inspecting suspicious emails, text messages, or server logs link-by-link is slow and hazardous. **Comrade Sentinel** enables analysts and users to paste raw, unformatted text blobs (emails, SMS messages, chat transcripts), automatically harvest all target URLs, and triage their threat level in seconds.

---

## 🚀 Live Demo

Test the scanner live in your browser:  
🔗 **[Comrade Sentinel Live Console](https://caspian1988.github.io/antigravity-threat-scanner/)**

---

## ✨ Key Features

### 🔍 1. Automated Target Harvester
- Uses deep regular expression parsing to extract fully qualified URLs, raw hostnames, and IP addresses from noisy raw text.
- Filters out syntax artifacts, trailing punctuation, and programming keywords.
- Deduplicates targets to ensure unique batch analysis.

### 🧠 2. Multi-Vector Heuristic Risk Engine
Every extracted hostname is evaluated against known attack patterns:
- **Disposable & Abused TLDs**: Flags high-risk registrar extensions frequently leveraged in short-lived scam campaigns (`.shop`, `.xyz`, `.top`, `.online`, `.click`, `.cfd`, `.gq`, etc.).
- **Brand Impersonation**: Detects high-value targets (Amazon, PayPal, Apple, Chase, Netflix, Binance, Microsoft, Bank of America, Target, Aldi) appearing on unofficial domains.
- **Credential-Harvesting Keywords**: Identifies urgency and deception terms (`login`, `verify`, `security`, `alert`, `update`, `wallet`, `claim`).
- **Raw IP Exposure**: Detects direct IPv4 access bypassing legitimate DNS infrastructure.

### 🌐 3. Google Safe Browsing API v4 Integration (Optional)
- Input an optional Google Safe Browsing API key to query Google's live global threat database.
- Checks against active listings for **Malware**, **Social Engineering (Phishing)**, and **Unwanted Software**.
- Automatically elevates confirmed matches to a **100/100 Critical Risk** rating.

### 🖥️ 4. Interactive SOC Console & Audit Log
- **Batch Table**: View risk scores and classifications (`CLEAN`, `SUSPICIOUS`, `HIGH RISK`) at a glance.
- **Domain Inspection**: Click any row to view granular threat attribution and individual risk flags.
- **Terminal Log**: Real-time event log with color-coded diagnostic audit trail.

---

## 🧮 Heuristic Scoring Breakdown

$$\text{Final Risk Score} = \min\left(100, \sum \text{Weights}\right)$$

| Threat Indicator | Condition Tested | Risk Penalty |
| :--- | :--- | :---: |
| **Raw IP Host** | Direct IPv4 address without domain name | **+60 pts** |
| **Brand Spoofing** | Target brand keyword outside official `.com`/`.org` domain | **+45 pts** |
| **Abused TLD** | Extension matches high-spam registry list (`.xyz`, `.top`, etc.) | **+40 pts** |
| **Phishing Trigger** | Action keywords (`login`, `verify`, `wallet`, etc.) present | **+20 pts** |
| **Google Safe Browsing** | Confirmed threat detected in Google's database | **Instant 100/100** |

### Classification Tiers:
- **0 pts**: `CLEAN`
- **1 – 49 pts**: `SUSPICIOUS`
- **50 – 100 pts**: `HIGH RISK`

---

## 🛠️ Built With

- **HTML5 & Vanilla CSS**: Custom cyberpunk / Security Operations Center (SOC) dark terminal theme.
- **Vanilla JavaScript**: Zero build steps, zero external npm packages, instant browser execution.
- **Google Safe Browsing Lookup API (v4)**: Real-time threat intelligence lookup.
- **Typography**: `JetBrains Mono` for authentic security console ergonomics.

---

## 💻 How to Run Locally

1. Clone the repository:
   ```bash
   git clone https://github.com/caspian1988/antigravity-threat-scanner.git
