# Join Us in Creating Unique Material

## Introduction

**Scenario:** External email received claiming to be from the Duolingo brand, proposing a collaboration.

This report documents the analysis of a suspected phishing email leveraging brand impersonation and social engineering techniques. The investigation examines the sender domain, email authentication results, header anomalies, and message content to assess legitimacy. The goal is to identify indicators of compromise and determine whether the email poses a potential security risk.

## Report

Suspected Phishing Email – Collaboration Request

### Analyst

M. Tolbert

### Summary of Findings

On July 13, 2025, at 15:50:03 UTC, the mailbox inquiry@mydfir[.]com received an email appearing to originate from the Duolingo brand. The message posed as a collaboration request and leveraged curiosity as a social engineering tactic to prompt a response. The recipient reported no interaction with the email.

Header analysis identified that the message was sent via a freemail account (libero[.]it) using authenticated SMTP (ESMTPSA). The claimed sending host (5[.]9[.]230[.]8) did not match the connecting IP address (90[.]160[.]50[.]35), indicating inconsistent sender identification and potential use of obfuscation or non-standard mailing infrastructure. Additionally, the Reply-To domain differed from the sending domain, further supporting the use of impersonation and typosquatting techniques.

Although SPF and DKIM checks passed for the sending domain, these controls only validate domain authorization and do not confirm the legitimacy of the impersonated Duolingo brand. The Reply-To domain passed SPF but failed both DKIM and DMARC, indicating authentication misalignment and increasing the likelihood of malicious intent.

Domain intelligence for duolingo-team[.]com was inconclusive, with sources reporting the domain as safe, unknown, or returning no detections. Reputation checks for both IP addresses were similarly inconclusive; however, the associated infrastructure resolves to different geographic regions (Spain and Germany), reinforcing the assessment of inconsistent and potentially unrelated sending infrastructure.

The declared sending host has historical associations with domains linked to phishing and other suspicious activity.

Based on the available evidence, this email is assessed to be a phishing attempt leveraging brand impersonation of Duolingo and social engineering techniques to solicit engagement. The use of a freemail service, authenticated SMTP, inconsistent sender infrastructure, and Reply-To domain misalignment further supports the conclusion that the message is malicious.

### Who, What, When, Where, Why, How 

**Who:** 
- **Recipient:** inquiry@mydfir[.]com 
- **Sender:** duolingo.ads@libero[.]it (freemail)
- **Reply-To:** info@duolingo-team[.]com (suspected spoofed domain)
- **Claimed Sending Host:** 5[.]9[.]230[.]8
- **Connecting IP:** 90[.]160[.]50[.]35

**What:** A suspicious email was identified that impersonates Duolingo and presents a collaboration opportunity related to linguistic content creation. The message attempts to establish credibility by referencing the recipient’s perceived involvement in language education. 


**When:** July 13, 2025, at 15:50:03 UTC


**Where:** The email originated from infrastructure associated with the domain libero[.]it, with a connecting IP address of 90[.]160[.]50[.]35. Header analysis also identified a declared sending host of 5[.]9[.]230[.]8, which does not align with the connecting IP. The message was successfully delivered to the internal mailbox inquiry@mydfir[.]com via the organization’s email gateway, indicating that the email bypassed initial filtering controls and reached the recipient environment.


**Why:** The objective of the email appears to be initial engagement through social engineering. By posing as a representative of Duolingo and offering a collaboration opportunity, the sender attempts to build trust and prompt a response from the recipient.

This type of approach is commonly used to:

- Establish rapport for follow-on phishing attempts
- Solicit sensitive information
- Deliver malicious links or attachments in subsequent communications


**How:** The email was submitted via an authenticated SMTP session (ESMTPSA) using a freemail account, allowing it to pass SPF and DKIM checks and bypass basic email security controls. The sending host information does not align with the connecting IP address, indicating inconsistent sender identification and suggesting the use of obfuscation or non-standard email tooling.

Overall, the attack leverages a combination of:

- Legitimate email authentication (SPF/DKIM) to evade detection
- Brand impersonation to establish trust
- Generic social engineering to prompt engagement


### MITRE ATT&CK Techniques 
| **Tactic**              | **Technique**    |
|-------------------------|------------------|
| Initial Access - TA0001 | Phishing - T1566 |

### Email Header Analysis 

**Displayed Sender:** Duolingo <duolingo.ads@libero[.]it> 

#### Authentication Results 
| **Control** | **Result** | **Interpretation**             |
|-------------|------------|--------------------------------|
| SPF         | None       | Passed                         |
| DMARC       | None       | Passed                         |
| DKIM        | None       | No domain protection policy    |

**Reply-To:** info@duolingo-team[.]com

#### Authentication Results 
| **Control** | **Result** | **Interpretation**             |
|-------------|------------|--------------------------------|
| SPF         | None       | Passed                         |
| DMARC       | None       | DKIM signing not implemented   |
| DKIM        | None       | No domain protection policy    |


SPF and DKIM passed for the sending domain but do not validate the impersonated Duolingo brand. The reply-to domain failed DKIM and DMARC, indicating misalignment and potential malicious intent. 
 
**Sending IP:** 213[.]209[.]17[.]209

**Characteristics:** 
- **ISP:** Italiaonline S.p.A. 
- **Domain Name:** italiaonline.it

**Reply-To IP:** Could not be resolved

The discrepancy between the sending domain and reply-to domain indicates an attempt to redirect recipient responses to attacker-controlled infrastructure. The reply-to domain does not resolve and lacks established reputation, suggesting it may be newly created or transient, a technique commonly observed in phishing campaigns.

### Domain Intelligence 

#### WHOIS Information
| **Field**  | **Value**           |
|------------|---------------------|
| Domain     | duolingo-team[.]com |
| Registered | 2025-07-10          |
| Registrar  | WEBCC Web Commerce Communications Limited dba WebNic.cc|
| Age        | 264 Days            |

**Indicators:** 
- Domain age is considerably younger than the legitimate brand domain it is attempting to replicate 
- Registrar associated with the domain differs from that of the legitimate brand’s domain 
- No established reputation 

### Indicators of Compromise 
| **Type**              | **Indicator**               |
|-----------------------|-----------------------------|
| Domain                | duolingo-team[.]com         |
| Sender                | duolingo.ads@libero[.]it    |
| Reply-To              | info@duolingo-team[.]com    |
| Connecting IP Address | 90[.]160[.]50[.]35          |

### Recommendations / Next Steps 
1. Block the impersonating domain (partner-uber[.]com) across email and network security controls. 
2. Quarantine and remove the phishing email from all affected mailboxes. 
3. Conduct a search across email logs to identify additional recipients and similar phishing attempts. 
4. Review user activity for any signs of interaction, including link clicks or credential submission. 
5. Enforce and validate SPF, DKIM, and DMARC policies to strengthen email authentication. 
6. Implement detection mechanisms for lookalike and typosquatted domains. 
7. Provide user awareness guidance regarding phishing and brand impersonation techniques. 
8. If user interaction occurred, initiate credential resets and monitor for suspicious account activity.

### Attachments / Evidence

#### Authentication Results:

**MX Toolbox**
<img width="1747" height="392" alt="image" src="https://github.com/user-attachments/assets/9c53d32b-b24b-4ffa-a5c2-0993cfadd9cb" />

**Google Admin Toolbox**
<img width="1040" height="841" alt="image" src="https://github.com/user-attachments/assets/f5bb7b90-8d83-4eeb-9e38-ec789ba8161c" />

**Vailmail**
<img width="1269" height="600" alt="image" src="https://github.com/user-attachments/assets/f3024ab9-0fa6-4837-ac88-1a5db48965ef" />

#### WHOIS Lookup
**Whois Domain Tools:**

<img width="772" height="809" alt="image" src="https://github.com/user-attachments/assets/a499dbcd-4db2-467f-9e86-4d372ee0b5d5" />

**Bishopi.io**
<img width="1755" height="702" alt="image" src="https://github.com/user-attachments/assets/54516263-7177-4545-b47e-45815712440c" />

#### Domain Reputation Check:

**isMalicious**
<img width="1572" height="594" alt="image" src="https://github.com/user-attachments/assets/488208d6-dfca-46d5-9a70-888de06d6a27" />

**IBM X-FORCE Exchange**
<img width="2007" height="412" alt="image" src="https://github.com/user-attachments/assets/d5432c8f-b7aa-429e-b8c7-be9ec84528ea" />

**AlienVault OTX**
<img width="1291" height="295" alt="image" src="https://github.com/user-attachments/assets/9e3dc3c6-e5ed-422a-9b1d-31f447f4afa6" />

#### IP Reputation Check:

**isMalicious**
<img width="2302" height="1838" alt="image" src="https://github.com/user-attachments/assets/7da69112-4432-4bc2-baa9-631dd22c1081" />

**IBM X-FORCE Exchange**
<img width="2830" height="1859" alt="image" src="https://github.com/user-attachments/assets/8a1f92e6-1c63-4f60-a906-33e799aa1c33" />

**AlienVault OTX**
<img width="3773" height="1799" alt="image" src="https://github.com/user-attachments/assets/31a7fd0f-2aa1-4350-92d6-d9e294e35473" />

#### Infrastructure and OSINT:

**AbuseIPDB**
<img width="1350" height="847" alt="image" src="https://github.com/user-attachments/assets/dd4a75f3-bda2-49e3-91a5-d0691de9f671" />

**AbuseIPDB**
<img width="2060" height="1811" alt="image" src="https://github.com/user-attachments/assets/06fd38a2-3e4e-4a9b-a600-740ae2934d71" />

**VirusTotal**
<img width="3270" height="1833" alt="image" src="https://github.com/user-attachments/assets/cb636f89-20dd-495d-92b1-f73be8ab644a" />

**VirusTotal**
<img width="3299" height="1161" alt="image" src="https://github.com/user-attachments/assets/5babbd46-0ddb-43c0-aa3f-59aa7020eb72" />

**VirusTotal**
<img width="3300" height="1947" alt="image" src="https://github.com/user-attachments/assets/efc1a27a-b4b5-4771-939b-7933132c6060" />

**VirusTotal**
<img width="3294" height="1919" alt="image" src="https://github.com/user-attachments/assets/6ea79bdf-cd2f-4199-9704-032c1659eea7" />

