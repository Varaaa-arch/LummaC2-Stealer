# LummaC2-Stealer: Fake CAPTCHA Campaign Analysis 🛡️

![Malware-Analysis](https://img.shields.io/badge/Analysis-Malware-red)
![Framework](https://img.shields.io/badge/Framework-Cyber--Kill--Chain-blue)
![Purpose](https://img.shields.io/badge/Purpose-Educational-green)

## 📌 Project Overview
This repository contains a comprehensive security analysis of the **Lumma Stealer** (LummaC2) distribution campaign. Specifically, it focuses on the "Fake CAPTCHA" social engineering technique—a sophisticated method used to trick users into executing malicious PowerShell scripts manually.

The analysis is structured using the **Lockheed Martin Cyber Kill Chain®** framework to provide a systematic breakdown of the attack lifecycle.

---

## 🔍 What is Lumma Stealer?
**Lumma Stealer** is a high-demand *Infostealer* sold on underground forums. It targets sensitive data, including:
* **Browser Data:** Saved passwords, autofill info, and credit card details.
* **Session Cookies:** Bypassing Multi-Factor Authentication (MFA).
* **Crypto Wallets:** Private keys and browser-based wallet extensions.
* **Sensitive Files:** Specific document types (.txt, .pdf, .docx) from the user's desktop.

---

## ⚡ The Cyber Kill Chain Breakdown
This project dissects the attack into 7 critical stages:

1.  **Reconnaissance:** Identification of distribution points (cracked software sites, streaming portals).
2.  **Weaponization:** Crafting encoded PowerShell payloads embedded in "Verify" buttons.
3.  **Delivery:** The "Copy-Paste-Enter" social engineering trick via fake verification pages.
4.  **Exploitation:** Exploiting the "Human Element" to bypass system security prompts.
5.  **Installation:** Execution of the downloader and persistence establishment.
6.  **Command & Control (C2):** Communication with the Lumma C2 infrastructure.
7.  **Actions on Objectives:** Data exfiltration and credential harvesting.

---

## 📑 Full Technical Article
For a detailed step-by-step breakdown and mitigation strategies, please read the full report here:
👉 **[Read Full Analysis (Lumma-Analysis.md)](./Bahasa-Indonesia/Lumma-analysis.md)**

---

## ⚠️ Disclaimer
This content is for **educational and cybersecurity awareness purposes only**. Any information provided here should not be used for malicious activities. The author is not responsible for any misuse of the information provided.

---
**Author:** Bizar Octo Givardi  
**Course:** Cybersecurity Fundamentals - [Meeting Task]