# 🛡️ Incident Report Analysis — NIST CSF
> **Portfolio Activity** | Google Cybersecurity Certificate — Course 3  
> **Framework Used:** NIST Cybersecurity Framework (CSF)  
> **Incident Type:** DoS Attack (ICMP Flood)

---

## 📋 Summary of the Security Event

A multimedia company providing web design, graphic design, and social media marketing services experienced a **Denial of Service (DoS) attack** that disrupted internal network operations for approximately **two hours**.

The attack involved a malicious actor flooding the company's network with a high volume of **ICMP (Internet Control Message Protocol) ping packets** through an **unconfigured firewall**. This caused all internal network services to become unresponsive, preventing normal traffic from accessing any network resources.

The incident management team responded by:
- Blocking all incoming ICMP packets
- Taking non-critical network services offline
- Restoring critical network services

**Root Cause:** An unconfigured firewall that allowed unrestricted ICMP traffic into the internal network.

---

## 🔍 Identify

> *Identify security risks through regular audits of internal networks, systems, devices, and access privileges.*

| Item | Details |
|------|---------|
| **Attack Type** | Denial of Service (DoS) — ICMP Flood |
| **Attack Vector** | Unconfigured firewall (no ICMP rate limiting) |
| **Systems Affected** | Entire internal network infrastructure |
| **Impact** | All network services unavailable for ~2 hours |
| **Attack Source** | External malicious actor sending mass ICMP pings |
| **Vulnerability** | Firewall misconfiguration — no ingress filtering on ICMP |

**Security Gaps Identified:**
- No firewall rules to limit or filter ICMP packet rates
- No source IP address verification (spoofing possible)
- Absence of IDS/IPS systems for traffic anomaly detection
- No network monitoring baseline to detect unusual traffic spikes

---

## 🔒 Protect

> *Protect internal assets through the implementation of policies, procedures, training, and tools that help mitigate cybersecurity threats.*

The following protective measures must be implemented to prevent recurrence:

### Firewall Hardening
- ✅ Implement a **firewall rule to rate-limit incoming ICMP packets**
- ✅ Enable **source IP address verification** to detect and block spoofed IP addresses on incoming ICMP traffic
- ✅ Configure **ingress and egress filtering** on all network perimeter devices

### Network Policy Updates
- ✅ Establish a formal **firewall configuration policy** requiring review before deployment
- ✅ Implement a **change management process** for all network device configurations
- ✅ Enforce the **principle of least privilege** for network access controls

### Training & Awareness
- ✅ Conduct security training for network administrators on firewall best practices
- ✅ Document and distribute updated network security procedures to all relevant staff

---

## 📡 Detect

> *Detect potential security incidents and improve monitoring capabilities to increase speed and efficiency of detection.*

To detect similar incidents in the future, the following detection capabilities will be deployed:

### Monitoring Tools
- ✅ Deploy **network monitoring software** (e.g., Wireshark, PRTG, SolarWinds) to continuously track traffic patterns
- ✅ Establish a **network traffic baseline** to identify anomalies (e.g., sudden spike in ICMP packets)
- ✅ Implement an **IDS/IPS system** (e.g., Snort, Suricata) configured to filter suspicious ICMP traffic based on volume and source characteristics

### Detection Rules
- ✅ Set **alerting thresholds** for ICMP packet rates exceeding the baseline
- ✅ Configure alerts for **unauthorized user account activity**
- ✅ Monitor logs for **repeated connection attempts from single IP addresses**

### Log Management
- ✅ Enable centralized **log collection and analysis** (SIEM solution)
- ✅ Retain firewall and network logs for a minimum of **90 days** for forensic purposes

---

## 🚨 Respond

> *Respond to contain, neutralize, and analyze security incidents; implement improvements to the security process.*

### Containment Procedures
1. **Immediately block** all incoming ICMP traffic at the firewall upon detection
2. **Isolate affected systems** from the rest of the network to prevent lateral spread
3. **Take non-critical services offline** to preserve bandwidth for critical systems
4. **Notify stakeholders** (management, IT team) within 15 minutes of confirmed incident

### Neutralization Steps
1. Identify and **null-route** the attacking IP address(es)
2. Apply emergency firewall rules to **filter malicious traffic**
3. **Restore critical services** in order of business priority
4. Verify network integrity before bringing all services back online

### Post-Incident Analysis
- Document the **timeline** of the attack (start, detection, containment, resolution)
- Identify **what data or systems** were exposed or affected
- Conduct a **root cause analysis** to determine how the firewall misconfiguration occurred
- Update the **incident response playbook** based on lessons learned

### Improvement Actions
- Review all firewall configurations quarterly
- Implement **automated configuration compliance checks**
- Establish an **escalation matrix** for security incidents

---

## 🔄 Recover

> *Recover affected systems to normal operation and restore systems data and/or assets affected by an incident.*

### Immediate Recovery (0–24 hours)
- ✅ Restore all **critical network services** (email, file servers, business-critical applications)
- ✅ Verify **data integrity** — confirm no data was corrupted or lost during the attack
- ✅ Validate that **firewall rules** are correctly applied and functioning
- ✅ Confirm **all systems are operational** and performing within normal parameters

### Short-term Recovery (1–7 days)
- ✅ Restore **non-critical services** after security verification
- ✅ Conduct a full **vulnerability assessment** of all network devices
- ✅ Patch or reconfigure any **additional misconfigured devices** discovered during assessment
- ✅ Communicate a **status update** to all stakeholders and affected clients

### Long-term Recovery & Prevention (1–4 weeks)
- ✅ Implement a formal **Business Continuity Plan (BCP)** for DoS scenarios
- ✅ Set up **redundant network paths** to maintain service availability during future attacks
- ✅ Subscribe to a **DoS/DDoS mitigation service** (e.g., Cloudflare, AWS Shield)
- ✅ Schedule a **third-party security audit** to validate all improvements

---

## 📊 Incident Timeline

```
[Day 0 - Attack]
  │
  ├── Malicious actor begins sending ICMP flood
  ├── Unconfigured firewall fails to block traffic
  ├── Network services become unresponsive
  │
  ├── Incident Management Team responds:
  │     ├── Blocks incoming ICMP packets
  │     ├── Takes non-critical services offline
  │     └── Restores critical services
  │
  └── Network restored after ~2 hours

[Post-Incident]
  ├── Security investigation conducted
  ├── Root cause identified: unconfigured firewall
  └── Remediation plan developed (this report)
```

---

## 🛠️ Tools & Technologies Referenced

| Category | Tools |
|----------|-------|
| Firewall | pfSense, Cisco ASA, iptables |
| IDS/IPS | Snort, Suricata |
| Network Monitoring | Wireshark, PRTG, SolarWinds |
| SIEM | Splunk, IBM QRadar |
| DDoS Mitigation | Cloudflare, AWS Shield |

---

## 📚 References

- [NIST Cybersecurity Framework (CSF)](https://www.nist.gov/cyberframework)
- [NIST SP 800-61 — Computer Security Incident Handling Guide](https://csrc.nist.gov/publications/detail/sp/800-61/rev-2/final)
- [CIS Controls — DoS Attack Mitigation](https://www.cisecurity.org/controls/)

---

> **Author:** Beldjouhri Abdelhamid  
> **Course:** Google Cybersecurity Certificate — Course 3  
> **Date:** May 30, 2026  
> **Framework:** NIST CSF (Identify · Protect · Detect · Respond · Recover)
