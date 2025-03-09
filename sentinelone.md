# 🛡️ SentinelOne Training Daily Diary

## 📅 Day 31-32: Fundamentals of EDR & XDR

Our training began with the fundamentals of EDR (Endpoint Detection and Response) and XDR (Extended Detection and Response). The instructor explained how traditional antivirus solutions are insufficient for modern cyber threats. We learned that EDR provides continuous monitoring and response capabilities on endpoints, going beyond prevention to detect threats that have already bypassed initial defenses.

The instructor emphasized the key difference between EDR and traditional antivirus - its focus on behavior rather than signature-based detection. We discovered that EDR solutions collect and analyze behavioral data from endpoints in real-time, enabling security teams to hunt for threats, investigate incidents, and respond to attacks quickly.

On the second day, we explored XDR and how it evolved from EDR to provide broader visibility across multiple security layers including network, endpoints, servers, and cloud workloads. The instructor demonstrated how XDR correlates data from various sources to provide a unified view of the security landscape, reducing alert fatigue by providing context and helping security teams move from reactive to proactive threat hunting.

---

## 📅 Day 33-35: Deep Dive into SentinelOne

During these three days, we delved deep into SentinelOne's architecture and capabilities. The instructor introduced us to the Singularity platform and explained how SentinelOne differs from other EDR solutions through its AI and machine learning core. We learned that the platform operates entirely from the cloud, with lightweight agents deployed on endpoints that don't require internet connectivity for protection.

The instructor walked us through the various detection engines that make SentinelOne powerful:

- **Behavioral AI Engine** - Monitors process behavior and identifies malicious activities based on patterns
- **Static AI Engine** - Analyzes files before execution
- **Cloud Detection Engine** - Leverages global threat intelligence
- **Reputation Engine** - Uses community-driven data
- **Anti-Exploitation/Fileless Engine** - Detects memory-based attacks
- **Lateral Movement Engine** - Identifies horizontal spread within networks
- **User-Defined Blocklist** - Allows custom organizational rules
- **Documents & Scripts Detection** - Identifies malicious files and scripts

We practiced understanding how these engines work together and learned about the importance of engine tuning based on organizational needs. The instructor provided hands-on demonstrations of how multiple engines correlate to minimize false positives while maintaining high detection accuracy.

---

## 📅 Day 36-38: SentinelOne Console Navigation

These three days were dedicated to mastering the SentinelOne management console. We started with the Dashboard, where the instructor showed us how to interpret various widgets and charts. We learned to read the "Threats by Detection Engine" visualization, which showed User-Defined Blocklist as the most active engine, followed by SentinelOne Cloud detection and Behavioral AI.

The "Threats by Type" chart revealed that Malware constituted the majority of threats in our environment, followed by Ransomware and PUA (Potentially Unwanted Applications). The instructor emphasized how these visual representations help communicate security status to management and quickly identify trends.

In the Sentinels tab, we learned endpoint management with over 8,500 connected endpoints in our lab environment. The instructor showed us how to identify agents requiring attention (we saw 120+ requiring attention and another 120+ attention needed), handle permission issues, and manage agent versions across the organization. We practiced filtering endpoints and learned about proper agent upgrade planning.

The Incidents tab became our primary focus as the instructor explained this is where SOC analysts spend most of their time. We learned to use the "Group by Hash" feature effectively and practiced analyzing different incident types like elastic-agent.exe, r.004150, and various malware samples. The instructor demonstrated how to determine analyst verdicts (Suspicious, True Positive, etc.) and manage incident statuses from "In Progress" to "Resolved."

---

## 📅 Day 39-40: Reporting & OSINT Integration

The final two days focused on proper reporting and OSINT integration. The instructor provided us with SafeAeon's standard report format, which begins with a clear subject line: SOC::Organization | Endpoint | Priority | Type | File | Actions | Status.

We learned to structure reports with essential sections:

- Impacted Endpoint details (Domain, OS Version, IP Address, User)
- Threat Summary (Classification, Status, Confidence Level)
- Analyst Triage Comments (Technical analysis and findings)
- Recommended Next Steps (False/True positive procedures)

The instructor emphasized making reports clear for both technical and non-technical stakeholders. We analyzed actual incidents from our training, including the LovinguApplication.exe case (identified as a 7zS.sfx self-extracting archive), demo32.exe (legitimate DemoShield component), certutil.exe (misused for Mimikatz deployment), and mouse jiggle utility ($R2U5XX5.exe).

We learned to integrate OSINT tools effectively:

- **VirusTotal** - For multi-engine file analysis and reputation checks
- **Joe Sandbox** - For dynamic malware analysis
- **Hybrid Analysis** - For comprehensive static and dynamic analysis
- **File. net** - For legitimate file verification

The instructor demonstrated how to correlate findings from these tools with SentinelOne detections to make informed analyst verdicts. We practiced verifying suspicious files through multiple sources before determining if they were false positives or true threats.
