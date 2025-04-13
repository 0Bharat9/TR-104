# 📋 Rapid7 Client Onboarding

## 📅 Week 12 (Days 56-60): Rapid7 Onboarding & Agent Management

### Days 56-57: Rapid7 Architecture & Agent Deployment

The week began with our transition to the onboarding department where we learned client onboarding tasks for various security consoles. We started with Rapid7 InsightIDR onboarding process and went through comprehensive documentation covering the platform architecture.

We learned about Rapid7 agents and collectors, understanding their roles in log collection and data forwarding. The instructor explained how collectors work as intermediary components that gather logs from multiple sources and forward them to the Rapid7 cloud platform. We studied event sources and their importance in building comprehensive monitoring coverage.

Key topics included agent deployment strategies, collector placement considerations, and network architecture requirements for optimal data collection. We practiced reading deployment guides and understanding prerequisites for different operating systems.

During these days, we focused on understanding client requirements and preparing for agent deployments. The training emphasized proper documentation review and understanding deployment prerequisites for successful client onboarding.

### Days 58-60: Multi-Platform Agent Installation

These days focused on hands-on agent installation across different operating systems. We learned step-by-step installation procedures for Rapid7 InsightIDR agents on Windows, Linux, and Mac systems. Each platform had specific considerations and configuration requirements.

For Mac installations, we learned about Full Disk Access requirements and how to configure nxlog profiles to ensure proper file system monitoring. The instructor demonstrated creating configuration profiles and deploying them through management systems.

We also covered collector installation on Linux servers specifically for network log collection. This included understanding network tap configurations, log parsing requirements, and ensuring collectors could handle high-volume network traffic without performance degradation.

The training included troubleshooting common installation issues, verifying agent connectivity, and validating log collection functionality across all supported platforms.

---

## 📅 Week 13 (Days 61-65): Integration & File Integrity Monitoring

### Days 61: Event Source Integration

This day covered integrating various event sources with Rapid7 InsightIDR. We learned about cloud service integrations including Office 365, Salesforce, Okta, and Google Cloud Platform (GCP). Each integration had specific API requirements, authentication methods, and log format considerations.

The instructor walked us through firewall integration processes, explaining how to configure network devices to send logs to Rapid7 collectors. We learned about syslog configuration, SNMP monitoring, and network device management for security monitoring.

### Days 62-63: File Integrity Monitoring & eBPF Project

These days focused on File Integrity Monitoring (FIM) capabilities within Rapid7 InsightIDR. We learned how to enable FIM on Windows, Linux, and Mac InsightIDR agents during client onboarding processes. The training covered understanding FIM configuration options and ensuring proper file monitoring setup on client systems.

We studied how to configure FIM during agent deployment to monitor critical files and directories on client systems. The training emphasized the onboarding perspective - ensuring FIM is properly enabled and configured during initial client setup rather than ongoing management.

**eBPF FIM Project Development:** During these days, my guide introduced me to an advanced project - developing a better File Integrity Monitoring (FIM) solution using eBPF technology. We discussed the limitations of traditional FIM approaches and how eBPF can provide more efficient, kernel-level file monitoring with reduced system overhead. The project involved writing eBPF programs for file system event capture and creating user-space applications for log processing under my guide's supervision.

### Days 64-65: Troubleshooting & Integration Completion

The final days focused on comprehensive troubleshooting guides covering common integration issues, connectivity problems, and data parsing errors. We learned systematic approaches to diagnosing agent connectivity issues, log collection problems, and event source integration failures.

The training emphasized the importance of proper event source configuration for comprehensive security monitoring coverage and client onboarding success.

---

