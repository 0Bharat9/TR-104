# SOC Analyst Rapid7 InsightIDR Training Diary

## 🗓️ Week 5 (Day 21-25): SIEM Foundations & Rapid7 InsightIDR Interface

### Day 21-22: Understanding SIEM and Log Collection 🔍

Our training began with the fundamentals of SIEM technology. We learned that a SIEM (Security Information and Event Management) system is like a security nerve center that collects, analyzes, and correlates security events from across the entire IT infrastructure. The core purpose is to provide real-time visibility into security threats and enable rapid incident response.

We discovered how SIEM solutions work through a systematic process:

- **Data Collection**: Gathering logs from various sources across the network
- **Normalization**: Converting different log formats into standardized formats
- **Correlation**: Applying rules to identify patterns and potential threats
- **Alerting**: Generating notifications when suspicious activities are detected
- **Investigation**: Analyzing and responding to security incidents

The training covered extensive log sources that feed into a SIEM:

- **Endpoint Systems**: Windows Event Logs showing user logins, system changes, and application activities
- **Network Devices**: Firewall logs from devices like FortiGate showing blocked/allowed connections, VPN access attempts, and network traffic patterns
- **Cloud Services**: Office 365 logs tracking mailbox access, file operations, and user activities; Google Cloud Platform (GCP) events; OKTA authentication logs
- **Security Tools**: Antivirus alerts, EDR (Endpoint Detection and Response) findings, and IDS/IPS notifications

Our instructor emphasized that each log source provides a unique perspective on security events, and combining them creates a comprehensive security picture.

### Day 23: Navigating Rapid7 InsightIDR Interface 🖥️

We got hands-on with the Rapid7 InsightIDR interface and learned about its main components:

**Dashboard Tab** 📊: This is the command center where we get an overview of our security posture. It displays:

- Real-time threat indicators and metrics
- Recent high-priority alerts requiring attention
- Timeline views showing activity patterns
- Customizable widgets for different security metrics

**Investigations Tab** 🔍: This powerful feature helps track complex security incidents:

- Creates automatic investigations from triggered alerts
- Provides timeline views showing the sequence of events
- Links related activities across different log sources
- Enables collaboration through comments and assignments

**Log Search** 🔎: The primary tool for analyzing security data:

- Modern interface with guided search capabilities
- Visual query builder for complex searches
- Auto-suggestions to help construct queries
- Filters for time ranges, users, and assets

**Legacy Log Search** 📚: An alternative search interface that offers:

- Traditional search syntax for advanced users
- More granular control over search parameters
- Backward compatibility with older systems
- Useful for specific advanced search scenarios

**Reports Tab** 📈: For generating security reports and documentation:

- Pre-built templates for common security metrics
- Custom report creation capabilities
- Scheduled report generation and distribution
- Executive summaries and detailed technical reports

### Day 24: Advanced Searching and Real Incident Analysis 🧭

We learned to construct sophisticated search queries using real examples from our training data. For instance, we practiced searching for account management events using queries like:

```java
source_user = "johndoe@example.com" AND operation = "AccountDisabled"
```

```java
where(source_user STARTS-WITH "Andrea")
```

```java
where("source_user" = "admin@company.onmicrosoft.com" and "action" = "Set-AntiPhishPolicy")
```

```java
where(destination_asset_address = grpw100.company.local) groupby(source_asset_address,result) calculate(count)
```

```java
where(action ICONTAINS "OBTAIN")groupby(host)calculate(unique:ip)having(unique:ip>=3)
```

We also learned about different search operators:

- AND, OR, NOT for boolean logic
- Wildcards for pattern matching
- Time range filters for specific periods
- Field-specific searches for targeted analysis

The training included analyzing real incidents such as:

- Mass file downloads from OneDrive
- Multiple VPN login failures
- Account disable operations in Office 365
- Mailbox permission delegations

### Day 25: Investigation Techniques and Context Building 📈

We learned how to build comprehensive investigations by:

- Correlating events across different log sources
- Creating timelines of suspicious activities
- Adding context through asset and user profiling
- Documenting findings with screenshots and notes

The instructor showed us how to identify patterns like:

- Multiple failed login attempts followed by a successful login
- Unusual file access patterns
- Account modifications outside business hours
- Activity from unfamiliar geographic locations

---

## 🗓️ Week 6 (Day 26-30): Advanced SOC Reporting and Incident Types

### Day 26-27: Mastering SOC Report Structure 📝

We learned the standard SOC report format used in the industry:

**Alert Header Format**:

```
SOC::[Client] | [Tool] | [Severity] | [Alert Type] | [Affected User/Asset]
```

**Essential Report Sections**:

1. **Introduction**: Brief explanation of what triggered the alert
2. **Security Alert Details**: Key facts like timestamps, users, and systems involved
3. **Source IP Analysis**: Geolocation, ISP information, and reputation checks
4. **SOC Analyst Triage Comments**: Our analysis, findings, and context
5. **Verification Required**: Questions for the client about legitimacy
6. **Recommended Next Steps**: Actionable security improvements

### Day 28-29: Common Incident Types and Detection Patterns 🚨

We studied various incident types commonly seen in SOC environments:

**Authentication Incidents**:

- Multiple login failures (potential brute force attacks)
- Successful logins from foreign countries
- VPN authentication anomalies
- NTLM downgrade attacks

**Account Management**:

- Unauthorized account creation/deletion/modification
- Password reset operations
- Account enable/disable activities
- Group membership changes

**Email Security**:

- Inbox forwarding rule creation
- Mailbox delegation changes
- Anti-phishing policy modifications
- Mass email operations

**File Operations**:

- Mass file downloads/deletions
- Unusual file access patterns
- Large data transfers
- Unauthorized file sharing

### Day 30: Practical Report Writing and Quality Assurance ✅

Our final day focused on creating comprehensive SOC reports. We learned to:

- Write clear, professional language suitable for both technical and non-technical stakeholders
- Include relevant evidence and context without unnecessary details
- Provide actionable recommendations based on findings
- Maintain objectivity while expressing professional opinions

We practiced with real incidents, creating complete reports that included:

- Detailed timeline reconstruction
- Root cause analysis
- Impact assessment
- Recommended remediation steps

## 🎯 Key Skills Developed

- **Technical Proficiency**: Mastered Rapid7 InsightIDR's interface and search capabilities
- **Analytical Skills**: Learned to correlate events across multiple log sources
- **Communication**: Developed clear, professional report writing abilities
- **Incident Response**: Understanding of proper investigation methodology
- **Pattern Recognition**: Ability to identify suspicious behaviors in large datasets
