# 🛡️ Phishing Email Analysis – BANCO DO BRADESCO LIVELO

## 🎯 Objective

Analyze a phishing email using manual investigation techniques. Review headers, identify the sender, validate domains and IPs, and extract phishing indicators.

---

## 🧪 General Steps for Phishing Email Analysis

When analyzing a suspicious email, perform the following steps to identify phishing indicators:

1. **Check the full email address of the sender** — Is it a legitimate domain or spoofed?  
2. **Review the sending domain** from headers like `From` and `Return-Path` — Does it match the official organization?  
3. **Extract the sender’s IP address** from the email headers.  
4. **Check if the sender IP is blacklisted** on databases like AbuseIPDB or VirusTotal.  
5. **Verify SPF (Sender Policy Framework) authentication** — Does it pass or fail?  
6. **Identify suspicious URLs or links** in the email body — Hover over links without clicking.  
7. **Look for urgent language or branding mismatches** that could indicate phishing.  

---

## 🧪 Scenario

An email claims that your Bradesco card has **92,990 Livelo points** expiring today. It uses Bradesco branding and sends you a link to "rescue" your points.

---

## 🔍 Analysis of the Scenario Email

### 1. What is the full email address of the sender?

📧 `banco.bradesco@atendimento.com.br`

---

### 2. What domain is used to send this email?

📤 From / Return-Path: `atendimento.com.br`  
⚠️ This is not an official Bradesco domain. Likely spoofed.

---

### 3. What is the sender’s IP address from the header?

🌐 `137.184.34.4`

> Found in the `Received:` header line from `ubuntu-s-1vcpu-1gb-35gb-intel-sfo3-06`.

---

### 4. Is the sender IP blacklisted?

✅ **Yes**  
🔍 IP `137.184.34.4` is reported on [AbuseIPDB](https://abuseipdb.com) and [VirusTotal](https://www.virustotal.com/gui/ip-address/137.184.34.4)

![IP Reputation](screenshots/ip-reputation.png)

---

### 5. What is the result of SPF authentication?

❌ **SPF: TempError**  
The SPF check failed due to a DNS Timeout. Indicates possible misconfiguration or intentional evasion.

> Also, `compauth=fail` in the header indicates Microsoft anti-spam did not trust the sender.

---

### 6. What is one suspicious URL or link found in the email body?

🔗 `https://blog1seguimentmydomaine2bra[.]me/`  
(Disguised as Bradesco but not affiliated)

![Suspicious Link](screenshots/suspicious-link.png)

---

## 📸 Screenshots Required

| Screenshot         | Description                                 |
|--------------------|---------------------------------------------|
| `email-header.png`  | Header with `From`, `Return-Path`, and IP  |
| `ip-reputation.png` | IP lookup on VirusTotal or AbuseIPDB        |
| `suspicious-link.png` | Hovered phishing link                      |

---

## ✅ Summary

This email is a **phishing attempt** using:

- Spoofed sender domain (`atendimento.com.br`)  
- Blacklisted IP (`137.184.34.4`)  
- Failing SPF + compauth checks  
- Fake branding and urgent call to action  
- Suspicious link with fake domain  

🛡️ **Conclusion:** Never click such links or enter sensitive data. Always verify the sender's domain and link URLs.

