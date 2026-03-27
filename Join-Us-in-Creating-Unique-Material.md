# Join Us in Creating Unique Material

## Introduction

**Scenario:** External email claiming to be from a trusted brand requesting collaboration.

This report documents the analysis of a suspected phishing email leveraging brand impersonation techniques. The investigation focuses on evaluating the sender domain, email authentication results, and message content to determine legitimacy. The goal is to identify indicators of compromise and assess whether the email poses a security risk.

## Report

Suspicious Brand Impersonation Email – Collaboration Request

### Analyst

M. Tolbert

### Summary of Findings

On March 19, 2025, at 7:03:51 UTC, a phishing email impersonating the Uber brand was received by inquiry@mydfir[.]com. The email attempted to lure the recipient with a collaboration proposal and encouraged a reply for further communication. 

The message claimed to originate from “Vanessa,” allegedly a manager with Uber, using the sender address manager@partners-uber[.]com. The use of “manager” in the local-part of the email address is intended to convey authority and reinforce the sender’s claimed position. Additionally, the hyphenated second-level domain (partners-uber[.]com) is designed to visually impersonate the legitimate Uber brand, increasing the likelihood of user trust. A legitimate domain would more likely follow a structure such as partners[.]uber[.]com. 

The email lacked personalization and used generic brand collaboration language. No URLs or attachments were present, indicating the absence of an immediate technical payload and suggesting a social engineering objective focused on eliciting a response. 

Email authentication analysis revealed that the domain has no SPF record configured, no DKIM signature present, and no DMARC policy in place. The absence of these controls prevents verification of sender legitimacy and is commonly associated with malicious or untrusted domains. 

Domain intelligence results were inconclusive, with sources reporting the domain as safe, unknown, or returning no detections. However, this does not indicate legitimacy, as newly registered or low-reputation domains often lack sufficient visibility in reputation systems. In contrast, the most recently resolved IP address associated with the domain was flagged as suspicious by multiple reputation sources, indicating a stronger likelihood of malicious activity. 

Additionally, related IP infrastructure has been associated with phishing, brute-force activity, fraud, and other malicious behaviors, including malware distribution and cryptojacking. 

Based on the combination of brand impersonation, deceptive domain structure, lack of email authentication, and supporting IP reputation data, this email is assessed to be a phishing attempt. 

The recipient did not report responding to the email.

### Who, What, When, Where, Why, How 

**Who:** 
- **Recipient:** inquiry@mydfir[.]com 
- **Sender:** duolingo.ads@libero[.]it (suspected spoofed domain)

**What:** Delivery of a phishing email using a spoofed, hyphenated second-level domain to visually impersonate the Uber brand and support a social engineering attempt aimed at eliciting a response from the recipient. 


**When:** July 13, 2025, at 15:50:03 UTC


**Where:** inquiry@mydfir[.]com inbox


**Why:** This activity is assessed as a social engineering attempt intended to build trust and establish communication with the recipient, enabling a staged follow-up attack. Potential objectives include: 
- Delivering malicious links or attachments in later interactions 
- Harvesting sensitive information (e.g., credentials or internal data) 
- Gaining unauthorized account access 
- Facilitating financial fraud or business email compromise (BEC)


**How:** The attack leveraged multiple social engineering and deception techniques, including: 
- A spoofed, hyphenated second-level domain to impersonate a trusted brand
- An authoritative sender identity to reinforce legitimacy and influence recipient trust 
- Generic, low-personalization messaging designed to initiate engagement and enable follow-on interaction

### MITRE ATT&CK Techniques 
| **Tactic**              | **Technique**    |
|-------------------------|------------------|
| Initial Access - TA0001 | Phishing - T1566 |

### Email Header Analysis 

**Displayed Sender:** Vanessa <manager@partners-uber[.]com> 

#### Authentication Results 
| **Control** | **Result** | **Interpretation**             |
|-------------|------------|--------------------------------|
| SPF         | None       | No sender authorization policy |
| DMARC       | None       | DKIM signing not implemented   |
| DKIM        | None       | No domain protection policy    |

The domain lacks SPF, DKIM, and DMARC configurations, preventing validation of sender authenticity and weakening email security controls. This significantly increases the domain’s susceptibility to spoofing and makes it a viable candidate for abuse in phishing campaigns. 
 
**Sending IP mapped to domain:** 216[.]120[.]147[.]200 

**Characteristics:** 
- **ISP:** Bodis, LLC 
- **Domain Name:** Bodis 

The sending domain and IP address do not align with Uber’s known infrastructure, supporting the assessment that the domain is unauthorized and potentially malicious.

### Domain Intelligence 

#### WHOIS Information
| **Field**  | **Value**           |
|------------|---------------------|
| Domain     | partners-uber[.]com |
| Registered | 2025-03-05          |
| Registrar  | Hello Internet Corp |
| Age        | 378 Days                 |

**Indicators:** 
- Domain age is considerably younger than the legitimate brand domain it is attempting to replicate 
- Registrar associated with the domain differs from that of the legitimate brand’s domain 
- No established reputation 

### Indicators of Compromise 
| **Type**           | **Indicator**               |
|--------------------|-----------------------------|
| Domain             | partners-uber[.]com         |
| Sender             | manager@partners-uber[.]com |
| IP Address         | 216[.]120[.]147[.]200       |
| Related IP Address | 34[.]98[.]99[.]30           |

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

