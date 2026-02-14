# Lumma Stealer Anatomy: A Catastrophe Disguised as "CAPTCHA"

Have you ever tried to download something online, only to be met with a CAPTCHA verification page? Usually, you just click an *"I'm not a robot"* checkbox or pick images of crosswalks. But what if that page asks you to press `Win + R`, then `Ctrl + V`, and finally `Enter`?

> **Warning: Please, never do that.**

This is the latest attack vector for **Lumma Stealer** (also known as LummaC2), a dangerous *Malware-as-a-Service (MaaS)* designed to drain your credentials, browser sessions, and crypto wallets. Instead of hacking your system through complex code, attackers are now hacking **human psychology**.

Let’s dissect the anatomy of this "Fake CAPTCHA" campaign using the **Cyber Kill Chain** framework (7 Stages) to understand how a simple manipulation can lead to a fatal compromise.

---

## Attack Analysis: Cyber Kill Chain Framework

### 1. Reconnaissance
At this stage, threat actors do not target specific individuals (unlike *spear-phishing*). Instead, they use **SEO Poisoning** and distribute malicious links through:
* Cracked software sites, keygens, or Windows activators.
* YouTube video descriptions promising "game cheats" or "skin scripts."
* Pirated content forums and illegal movie streaming sites.

They scout for users who are "letting their guard down"—people eager to download content who view a verification pop-up as a routine step.

### 2. Weaponization
Attackers avoid `.exe` files initially, as they are easily flagged by antivirus software. Instead, they prepare an encoded **PowerShell script** or `mshta` command (often using Base64 to bypass human readability).

This script is embedded behind a **Verify** button on a webpage designed to look 100% identical to Cloudflare Turnstile or Google reCAPTCHA. Using the JavaScript `navigator.clipboard.writeText()` function, the page silently copies the malicious command to your PC’s **clipboard** the moment you click it.

### 3. Delivery
The victim lands on the infected site. This is where high-level **social engineering** occurs. A convincing pop-up displays instructions:
1. Click the **"I'm not a robot"** button (copies the malware to the clipboard).
2. Press `Windows + R` (opens the powerful Windows 'Run' dialog).
3. Press `Ctrl + V` (pastes the malicious PowerShell script).
4. Press `Enter` (executes the command).

Attackers exploit verification fatigue. The victim simply wants to access their file quickly and follows the instructions without realizing they are pasting a system-level command.

### 4. Exploitation
This stage is unique. Technically, it is a **Zero-Click exploit for the software, but a Full-Click exploit for the human** (*Human-Driven*).

Since the command is executed directly by the user via the `Run` dialog, the Windows OS treats it as a **trusted** command. This clever technique bypasses security protocols like *Mark of the Web*, Windows SmartScreen warnings, and many standard *Endpoint Detection and Response* signatures.

### 5. Installation
Once `Enter` is pressed, a terminal window opens for a split second and closes often unnoticed. PowerShell then:
* Connects to the attacker's hosting server (often abusing legitimate services like GitHub, Discord, or Bitbucket to evade firewalls).
* Downloads the primary Lumma Stealer payload.
* Places the executable in hidden directories like `%LocalAppData%` or `%Temp%`.
* Establishes **Persistence** via Scheduled Tasks or Registry `Run` keys to ensure the malware survives a reboot.

### 6. Command and Control (C2)
Lumma Stealer comes to life. The malware uses encryption to contact the attacker's **Command and Control (C2) server**. It reports the successful infection, sends system telemetry (OS version, IP, installed Antivirus), and waits for configuration files detailing which data to steal.

### 7. Actions on Objectives
This is the final execution phase. Lumma Stealer works lightning-fast (within seconds) to harvest and exfiltrate:
* **Browser Databases:** Extracting saved usernames, passwords, autofill data, and credit card info from Chrome, Edge, Firefox, etc.
* **Session Cookies:** Capturing active login cookies. This allows attackers to hijack accounts (Gmail, Social Media, Crypto Exchanges) **without needing OTP or 2FA**, as the site believes the attacker is the legitimate user.
* **Crypto Wallets & Desktop Apps:** Searching for crypto wallet extensions, Telegram sessions, Steam accounts, and Discord tokens.

All data is bundled into a `.zip` file and sent to the C2 server, where it is often automatically listed for sale on **Dark Web** marketplaces.

---

## How to Protect Yourself?

1. **Use Common Sense (Zero Trust):** Legitimate CAPTCHAs (Google, Cloudflare, hCaptcha) **ONLY** require interaction within the browser (clicking images, sliding puzzles). If a site asks you to open your system terminal (`Run`, `CMD`, `PowerShell`), it is **100% malware**.
2. **Enable Clipboard Warnings:** In Windows 11 or modern browsers, pay attention to alerts when a site attempts to read or write to your clipboard automatically.
3. **Windows Hardening:** For IT admins, consider enabling *PowerShell Constrained Language Mode* or restricting script execution for non-admin users.
4. **Avoid Pirated Content:** Refrain from downloading cracked software, as this remains the number one infection vector for stealers.

---
