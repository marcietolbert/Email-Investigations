# Join Us in Creating Unique Material

## Introduction

**Scenario:** External email received claiming to be from the Duolingo brand, proposing a collaboration.

This report documents the analysis of a suspected phishing email leveraging brand impersonation and social engineering techniques. The investigation examines the sender domain, email authentication results, header anomalies, and message content to assess legitimacy. The goal is to identify indicators of compromise and determine whether the email poses a potential security risk.

## Report

Suspected Phishing Email – Collaboration Request

### Analyst

M. Tolbert

### Summary of Findings

On July 13, 2025, at 15:50:03 UTC, the mailbox inquiry@mydfir[.]com received an email appearing to originate from the Duolingo brand. The message posed as a collaboration request and used curiosity to encourage the recipient to respond. The recipient did not report any interaction with the email.

Header analysis revealed the email was sent via a freemail account (libero.it) using authenticated SMTP (ESMTPSA). The claimed sending host (5[.]9[.]230[.]8) did not match the connecting IP (90[.]160[.]50[.]35), indicating inconsistent sender identification and potential use of obfuscation or non-standard email tools. Additionally, the reply-to domain differed from the sending domain, further demonstrating impersonation and typosquatting tactics.

While SPF and DKIM checks passed for the sending domain, these mechanisms only validate domain authorization and do not confirm the legitimacy of the impersonated Duolingo brand. The reply-to domain passed SPF but failed DKIM and DMARC, indicating authentication misalignment and an increased likelihood of malicious intent. 

Domain intelligence results for duolingo-team[.]com were inconclusive, with sources reporting the domain as safe, unknown, or returning no detections. Reputation checks for both IP addresses returned inconclusive results; however, the associated infrastructure resolves to different geographic locations (Spain and Germany), indicating inconsistent sender identification and suggesting the use of disparate or unrelated systems.

The declared sending host is historically associated with a domain linked to phishing and other suspicious activity.

Based on the analysis, the email is assessed to be a phishing attempt leveraging brand impersonation of Duolingo and social engineering techniques to solicit engagement. The use of a freemail domain, authenticated SMTP (ESMTPSA), inconsistent sender infrastructure, and reply-to domain misalignment further supports the conclusion that the message is malicious in nature.


### Who, What, When, Where, Why, How 

**Who:** 
- **Recipient:** inquiry@mydfir[.]com 
- **Sender:** duolingo.ads@libero[.]it (suspected spoofed domain)

**What:** A suspicious email was identified that impersonates Duolingo and presents a collaboration opportunity related to linguistic content creation. The message attempts to establish credibility by referencing the recipient’s perceived involvement in language education. 


**When:** July 13, 2025, at 15:50:03 UTC


**Where:** The email originated from infrastructure associated with the domain libero.it, specifically the sending IP address 213[.]209[.]10[.]34, which is not affiliated with the legitimate mail systems of Duolingo. The message was successfully delivered to the internal mailbox inquiry@mydfir[.]com via the organization’s email gateway, indicating that the email bypassed initial filtering controls and reached the recipient environment.


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

