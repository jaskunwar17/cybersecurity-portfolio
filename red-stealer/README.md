#  Red Stealer Blue Team Lab — Threat Intelligence Project

**Platform:** CyberDefenders  
**Date:** ************  
**Tools:** VirusTotal · MalwareBazaar · ThreatFox · WHOIS · YARA · CyberChef  

---

##  Summary
“Red Stealer” is a **blue-team CTF** focused on analyzing a malicious executable.  
I investigated its hash, mapped it to MITRE ATT&CK, and identified related IOCs and YARA rules.  
The lab simulates real-world malware profiling for SOC analysts.

---

##  Objectives
- Identify malware type and family  
- Find first-seen timestamp  
- Map MITRE techniques (e.g., **T1005 — Data from Local System**)  
- Extract network indicators (domains, IPs, ports)  
- Retrieve YARA and ThreatFox signatures  

---

##  Methodology
1. **VirusTotal Hash Analysis** → classified as Trojan · file `Wextract.exe` · first seen 2023-10-06 04:41:50 utc  
   - ![VirusTotal](../assets/red-stealer/Screenshot(231).png)
2. **MalwareBazaar** → found YARA rule `detect_Redline_Stealer (by Varp0s)`  
   - ![YARA Signature](../assets/red-stealer/Screenshot(236).png)
3. **WHOIS Lookup** → C2 IP `77.91.124.55:19071` hosted on Yeezyhost  
4. **ThreatFox Correlation** → Alias: `RecordStealer`  
5. **Host Behavior** → uses `advapi32.dll` for privilege operations  

---

##  Results
| Indicator | Value |
|------------|--------|
| Malware Type | Trojan (RedLine Stealer variant) |
| First Seen | 2023-10-06 04:41:50 UTC |
| MITRE ID | T1005 — Data from Local System |
| C2 Server | 77.91.124.55 : 19071 |
| Hosting | Yeezyhost |
| YARA Rule | `detect_Redline_Stealer (Varp0s)` |
| Alias | RecordStealer |
| DLL | advapi32.dll |

---

##  Reflection
This project strengthened my **threat-intel workflow** skills — from IOC correlation to report writing.  
I learned to interpret cross-source intel and apply MITRE ATT&CK mapping accurately.  
Next time, I’d add sandbox dynamic analysis and automate hash queries via API.

---

*All screenshots and data are from my own analysis. Sensitive info is redacted as `************`.*
