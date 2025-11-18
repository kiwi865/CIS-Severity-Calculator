# CIS Severity Calculator
Assess the risk severity of CIS benchmark controls for cloud platforms (AWS, Azure, GCP) and on-premises systems (Windows, Linux, network devices). Generate comprehensive severity scores (0-100 scale).

# Comparison Table of Risk Scoring Methodologies

| Aspect                         | CVSS v3.1/v4.0                | 5×5 Risk Matrix                         | CIS Severity Calculator           |
|--------------------------------|-------------------------------|------------------------------------------|----------------------------------------------|
| **Primary Use Case**           | Software vulnerabilities (CVEs) | General enterprise risk management        | Configuration/hardening compliance            |
| **Target Audience**            | Security researchers, patch managers, vulnerability management teams | Business executives, risk managers, auditors | System administrators, security engineers, compliance teams |
| **Scoring Scale**              | 0–10 (decimal precision)      | 1–25 (5 likelihood × 5 impact)            | 0–100 (integer scale)                        |
| **Standardization**            | Highly standardized (FIRST.org) | No universal standard, varies by organization | Custom framework based on security best practices |
| **Complexity**                 | High — 11+ metrics across 3 groups | Low — 2 dimensions only                   | Medium — 8 factors across 3 categories        |
| **Subjectivity**               | Low (technical/objective criteria) | High (significant interpretation needed) | Medium (guided criteria with context)         |

# What Each Tool Measures

---

## **CVSS – Common Vulnerability Scoring System**

**Measures:**  
The inherent severity of a *software vulnerability* (a flaw or bug in code).

### **Key Metrics**

#### **Base Metrics (intrinsic characteristics of the vulnerability):**
- **Attack Vector:** Network, Adjacent, Local, Physical  
- **Attack Complexity:** Low, High  
- **Privileges Required:** None, Low, High  
- **User Interaction:** None, Required  
- **Scope:** Changed, Unchanged  
- **Confidentiality Impact:** None, Low, High  
- **Integrity Impact:** None, Low, High  
- **Availability Impact:** None, Low, High  

#### **Temporal Metrics (change over time):**
- Exploit Code Maturity  
- Remediation Level  
- Report Confidence  

#### **Environmental Metrics (organization-specific context):**
- Modified Base Metrics  
- Confidentiality / Integrity / Availability Requirements  

### **Example Use Cases**
- "CVE-2024-1234: Remote Code Execution in Apache Log4j has CVSS score **9.8**"  
- "This SQL injection vulnerability in our web application scores **8.2**"  
- "Zero-day exploit in Windows kernel receives CVSS **7.8**"

### **What It Tells You**
- How severe is this specific vulnerability?  
- How easily can it be exploited?  
- What access does an attacker gain?  
- Should we patch this immediately or can it wait?

---

## **5×5 Risk Matrix**

**Measures:**  
General *likelihood and impact* of any risk scenario.

### **Key Metrics**

#### **Likelihood (1–5 scale):**
1. **Rare** – may occur in exceptional circumstances  
2. **Unlikely** – could occur sometime  
3. **Possible** – might occur at some time  
4. **Likely** – will probably occur  
5. **Almost Certain** – expected to occur  

#### **Impact / Consequence (1–5 scale):**
1. **Insignificant** – minimal impact  
2. **Minor** – small impact, easily managed  
3. **Moderate** – medium impact, requires management attention  
4. **Major** – significant impact, substantial resources needed  
5. **Catastrophic** – extreme impact, threatens organization survival  

### **Risk Score Formula**
**Risk Score = Likelihood × Impact**  
(Range: **1–25**)

### **Example Use Cases**
- "Risk of ransomware attack: **4 × 5 = 20 (Critical)**"  
- "Risk of key vendor bankruptcy: **2 × 4 = 8 (Medium)**"  
- "Risk of regulatory fine for data breach: **3 × 4 = 12 (High)**"

### **What It Tells You**
- What’s the overall risk level of this threat scenario?  
- How should we prioritize this risk among other business risks?  
- Does this risk require board-level attention?

---

## **CIS Severity Calculator**

**Measures:**  
The urgency and importance of implementing a *security configuration control*.

### **Key Metrics**

#### **Security Impact Assessment (45% weight):**
- Confidentiality Impact — potential data exposure  
- Integrity Impact — potential unauthorized modifications  
- Availability Impact — potential service disruption  

#### **Threat Assessment (35% weight):**
- Exploitability — ease of exploitation  
- Scope — number of systems/users affected  
- Detection Difficulty — ability to identify exploitation  

#### **Implementation Context (20% weight):**
- Compliance Requirements — regulatory mandates  
- Implementation Complexity — effort to remediate  

### **Example Use Cases**
- "Control 1.1.1 **Enforce password history**: Severity Score **61 (Medium)** – implement within 1 month"  
- "Control 2.3.1.1 **Ensure auditing is enabled**: Severity Score **78 (High)** – implement within 1 week"  
- "Control 5.1.1 **Disable Guest account**: Severity Score **45 (Low)** – address in quarterly review"

### **What It Tells You**
- Which CIS controls should we prioritize?  
- How urgently do we need to implement this hardening measure?  
- What’s the business justification for this configuration change?

# Key Philosophical Differences

---

## **1. Nature of the Problem**

| Tool | Problem Type | Analogy |
|------|--------------|---------|
| **CVSS** | A flaw exists that *shouldn’t* be there | Finding a broken lock on your door |
| **5×5 Matrix** | A threat scenario that *might* occur | Assessing if burglars might target your neighborhood |
| **CIS Severity Calculator** | A security control that is *missing* | Deciding whether to install a lock on your door |

---

## **2. Remediation Approach**

### **CVSS**
- **Remediation:** Patch the vulnerability (eliminate the flaw)  
- Often requires vendor patch release  
- Timeline driven by vendor + exploitability  
- **Binary outcome:** patched or not patched  

### **5×5 Risk Matrix**
- **Remediation:** Implement controls to reduce likelihood or impact  
- Flexible — can choose from multiple control options  
- Timeline driven by organizational risk tolerance  
- **Continuous outcome:** risk can be reduced incrementally  

### **CIS Severity Calculator**
- **Remediation:** Enable the security control (fix the configuration)  
- Usually under your direct control (no vendor dependency)  
- Timeline driven by risk + implementation complexity  
- **Binary outcome:** compliant or non-compliant  

---

## **3. Context Sensitivity**

### **CVSS**
- Base score is *universal* (same for everyone)  
- Environmental metrics rarely used in practice  
- Focuses on technical exploitability  
- Limited organizational context  

### **5×5 Risk Matrix**
- Highly context-dependent  
- Same scenario may score differently across organizations  
- Heavy reliance on subjective judgment  
- Strong organizational context  

### **CIS Severity Calculator**
- Moderate context sensitivity  
- Mix of universal factors (exploitability) and contextual factors (compliance, scope)  
- Structured guidance reduces subjectivity  
- Balanced approach to context  

# When to Use Each Tool

---

## **Use CVSS When:**
- ✅ You're managing **software vulnerabilities (CVEs)**
- ✅ You need to **prioritize patching activities**
- ✅ You're tracking **known exploits** in software products
- ✅ You need **standardized scores** for vulnerability reporting
- ✅ You're comparing **severity of different software flaws**

### **❌ Don't use CVSS for:**
- Configuration issues (**use CIS Severity Calculator instead**)
- General risk scenarios (**use 5×5 Matrix instead**)
- Missing security controls that aren't vulnerabilities

---

## **Use 5×5 Risk Matrix When:**
- ✅ You're conducting **enterprise risk assessments**
- ✅ You need simple communication for **non-technical stakeholders**
- ✅ You're comparing **diverse risk types** (cyber, financial, operational, etc.)
- ✅ You need **executive-level risk summaries**
- ✅ You're performing **initial high-level risk identification**

### **❌ Don't use 5×5 Matrix for:**
- Technical security prioritization (**too simplistic**)  
- Vulnerability management (**use CVSS instead**)  
- Detailed remediation planning (**lacks specificity**)  

---

## **Use CIS Severity Calculator When:**
- ✅ You're implementing **CIS benchmarks** or security hardening
- ✅ You have **hundreds of configuration findings to prioritize**
- ✅ You need to **justify remediation timelines** to management
- ✅ You're working with **system configurations**, not software bugs
- ✅ You need to balance **security risk with implementation effort**
- ✅ You're conducting **configuration compliance assessments**

### **❌ Don't use CIS Severity Calculator for:**
- Software vulnerabilities (**use CVSS instead**)  
- General business risks (**use 5×5 Matrix instead**)  
- Risks not related to **configuration controls**  

# Real-World Example: Same Security Issue, Three Different Approaches

## **Scenario**
Your Windows Servers have **weak password policies**  
(no history enforcement, short minimum length)

---

## **How Each Tool Would Approach This**

### **CVSS Approach**
- "Is there a CVE for this?" → **No**, this isn't a software vulnerability  
- "Can't score this with CVSS" → ❌ *Wrong tool for the job*  
- CVSS doesn't apply because weak password policy is **not a code flaw**

---

### **5×5 Risk Matrix Approach**
- **Likelihood of password compromise:** 4 (Likely)  
- **Impact of compromised accounts:** 4 (Major)  
- **Risk Score:** **16 (High Risk)**  

**What this tells you:**  
A high-priority risk, but **no guidance** on which security controls to implement or their priority order.

---

### **CIS Severity Calculator Approach**
| Control | Description | Score | Recommended Action |
|---------|-------------|--------|----------------------|
| **1.1.1** | Enforce password history | **61 (Medium)** | Implement in **1 month** |
| **1.1.2** | Minimum password length | **73 (High)** | Implement in **1 week** |
| **1.1.3** | Password complexity | **68 (Medium–High)** | Implement in **2 weeks** |

**What this tells you:**  
Clear, actionable, **prioritized remediation guidance**.

---

# Common Misconceptions

## ❌ **"CVSS and CIS scores should align"**

### **Reality:**  
They measure **completely different things**.

Example:  
- **CVE-2024-XXXX:** Remote code execution in Apache → **CVSS 9.8 (Critical)**  
- **CIS Control 2.3.1:** "Ensure Apache service runs as non-root user" → **~55 (Medium)**  

A critical vulnerability does **not** imply the related hardening control has the same urgency.

---

## ❌ **"A 5×5 score can replace detailed security scoring"**

### **Reality:**  
5×5 matrices are useful for **executive summaries**, but terrible for **operational prioritization** because:

- They oversimplify complex issues  
- They are highly subjective  
- They lack actionable remediation guidance  
- Different scorers often produce inconsistent results  

---

## ❌ **"CIS scores are just opinion-based like 5×5"**

### **Reality:**  
The CIS Severity Calculator uses **structured**, semi-objective scoring based on:

- Guided selection options  
- Weighted scoring algorithms  
- Clear, defined evaluation criteria  

It’s **not as objective as CVSS**, but far more structured and reliable than a 5×5 matrix.

---

# How These Tools Complement Each Other

In a mature security program, you would use **all three tools**, each serving a different purpose.

<img width="945" height="549" alt="image" src="https://github.com/user-attachments/assets/5dfaefd6-a7ee-4171-b515-d858319d0cbc" />

---

# Example Integrated Workflow

## **Strategic Level (Quarterly): Use 5×5 Risk Matrix**
- *Example:* “Insider threat risk: 4 × 4 = 16 (**High**)”  
- **Decision:** Allocate **$200K** for access control improvements

---

## **Tactical Level (Monthly): Use CIS Severity Calculator**
- Review CIS Windows Server benchmark  
- Score **200+ controls**  
- Build prioritized remediation backlog  
- **Top priority:** Audit logging controls (**score ≥ 75**)

---

## **Operational Level (Weekly): Use CVSS**
- New vulnerabilities released: **CVE-2024-XXXX (CVSS 8.8)**  
- Emergency patching required  
- Coordinate with change management teams  

---

# Limitations of Each Approach

## **CVSS Limitations**
- Doesn’t consider exploitability **in your environment**  
- Base scores ignore **organization-specific context**  
- Environmental metrics rarely used  
- Doesn’t account for compensating controls  
- Can create **patch fatigue** when treated as absolute truth  

---

## **5×5 Risk Matrix Limitations**
- Highly subjective—different people score differently  
- Oversimplifies complex risks  
- Prone to cognitive biases  
- No remediation guidance  
- Can create false precision (“Is this really a 12 or a 15?”)  
- Known mathematical flaws in using simple multiplication  

---

## **CIS Benchmark Calculator Limitations**
- Not industry-standard (organization-specific scoring)  
- Requires security expertise to score accurately  
- Doesn’t replace full risk assessment  
- Weighting model may not fit every organization  
- Assumes CIS benchmarks are relevant to your environment  
- Some factors still require human judgment  

---

# Summary: Choose the Right Tool

| If You're Asking… | Use This Tool |
|-------------------|----------------|
| **"How severe is this software vulnerability?"** | CVSS |
| **"Should we patch CVE-2024-XXXX urgently?"** | CVSS |
| **"What are our top organizational risks?"** | 5×5 Matrix |
| **"How should we allocate security budget?"** | 5×5 Matrix |
| **"Which CIS controls should we implement first?"** | CIS Severity Calculator |
| **"Is disabling the Guest account urgent?"** | CIS Severity Calculator |
| **"How do we prioritize our hardening backlog?"** | CIS Severity Calculator |

---


