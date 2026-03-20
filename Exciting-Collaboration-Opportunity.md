# Exciting Collaboration Opportunity

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

The recipient did not report responding to the email

### Who, What, When, Where, Why, How 

#### Who

**Recipient:** inquiry@mydfir[.]com 

**Sender:** manager@partners-uber[.]com (external sender) 

<br>

#### What 

Delivery of a phishing email using a spoofed, hyphenated second-level domain to visually impersonate the Uber brand and support a social engineering attempt aimed at eliciting a response from the recipient. 

<br>

#### When 

**Initial delivery timestamp:** 
March 19, 2025, at 7:03:51 UTC

<br>

#### Where 

Email delivered to inquiry@mydfir[.]com

<br>

#### Why 

This activity is assessed as a social engineering attempt intended to build trust and establish communication with the recipient, enabling a staged follow-up attack. Potential objectives include: 

- Delivering malicious links or attachments in later interactions 
- Harvesting sensitive information (e.g., credentials or internal data) 
- Gaining unauthorized account access 
- Facilitating financial fraud or business email compromise (BEC)

<br>

#### How 

The attack leveraged multiple social engineering and deception techniques, including: 

- A spoofed, hyphenated second-level domain to impersonate a trusted brand
- An authoritative sender identity to reinforce legitimacy and influence recipient trust 
- Generic, low-personalization messaging designed to initiate engagement and enable follow-on interaction

### MITRE ATT&CK Techniques 

| **Tactic**              | **Technique**    |
|-------------------------|------------------|
| Initial Access - TA0001 | Phishing - T1566 |

### Email Header Analysis 

#### Sender Information 
**Displayed Sender:** Vanessa <manager@partners-uber[.]com> 

<br> 
#### Authentication Results 
 
| **Control** | **Result** | **Interpretation**             |
|-------------|------------|--------------------------------|
| SPF         | None       | No sender authorization policy |
| DMARC       | None       | DKIM signing not implemented   |
| DKIM        | None       | No domain protection policy    |

The domain lacks SPF, DKIM, and DMARC configurations, preventing validation of sender authenticity and weakening email security controls. This significantly increases the domain’s susceptibility to spoofing and makes it a viable candidate for abuse in phishing campaigns. 

<br>

#### Sending Infrastructure 
Sending IP observed mapped to domain: 216[.]120[.]147[.]200 

Characteristics: 
- ISP: Bodis, LLC 
- Domain Name: Bodis 

 The sending domain and IP address do not align with Uber’s known infrastructure, supporting the assessment that the domain is unauthorized and potentially malicious.
