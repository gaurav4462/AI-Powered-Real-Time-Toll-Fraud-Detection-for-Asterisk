# AI-Powered-Real-Time-Toll-Fraud-Detection-for-Asterisk



## Introduction

Many companies have adopted Voice over Internet Protocol (VoIP) as a replacement
for the traditional Public Switched Telephone Network (PSTN). Also known as in-
ternet telephony, VoIP offers numerous advantages, including text messaging, video
calls, conference calls and identification and provides flexibility to be used from dif-
ferent geographic locations. “The main advantages of using VoIP are the result of the
non-reservation of lines for communication purposes and the transmission of packets
of data along with other data packets on the data network. This translates into cost
savings and effective network utilisation, which can result in further benefits due to
the digitisation of the processAlmutairi [2018].” Despite the many benefits of VoIP
technology, it also presents potential risks, including the possibility of fraud, so we
need to implement security features to protect for fraud.

VoIP communication based on the Session Initiation Protocol (SIP) has evolved
as de-facto standard for voice communication and, support of open IP-based inter-
faces is increasingly essential and VoIP is subject to the fraud schemes known from
traditional telephony services as well as those known from today’s Internet as VoIP
blends these technologiesHoffstadt et al. [2014]. VoIP is a complex technology with
many components, including SIP(Session Initiation Protocol), RTP (Real-time Trans-
port Protocol), and complex signalling and media protocols. In addition, VoIP has
introduced additional risks for misuse. In this paper, we would like to discuss the toll
fraud in VoIP and survey the solutions proposed in various areas.

---

## Introduction to Toll Fraud

Toll fraud, sometimes called International Revenue Share Fraud (IRSF), is a type of scam where a person or group gets into a company’s phone system without permission to make calls.  
— Dexatel [2016]

Fraudsters partner with services that have expensive phone numbers. When they use a hacked phone system to call these numbers, the company gets billed and the fraudster earns a share.  

Typical attack steps:
- Attacker gains access to a system.
- Calls a test number (usually an international premium rate) briefly to check security.
- If successful, attacker confirms the system is vulnerable.
- Then calls premium-rate numbers tied to revenue-sharing agreements.
- The victim pays for these calls.

**Figure 1: Toll Fraud**

Attackers scan the Internet to find vulnerable VoIP PBX systems, often those with weak security or default passwords. Once found, they attempt to log in using weak/default SIP credentials. Upon success, they gain access without the owner realizing.

The attacker makes calls to premium-rate numbers (e.g., +1-900 numbers), which are forwarded by the VoIP PBX through the PSTN network to premium services. Charges accumulate, benefiting the attacker.

Eventually, the company receives an unusually high bill and discovers the unauthorized calls. However, significant financial damage may already be done.

Unlike data theft, toll fraud turns phone systems into a source of income for criminals. It’s especially dangerous for businesses using VoIP or Asterisk systems.  
— Group [2017]

In 2023, phone fraud cost businesses worldwide about $38.95 billion. Toll fraud is one of the main reasons for this huge number.  
— Philippines [2023]

Attackers typically exploit weak passwords or open network doors, then use automated programs to make numerous calls quickly.  
— Dexatel [2016]

---
<img width="832" height="589" alt="Screenshot from 2025-09-21 17-55-58" src="https://github.com/user-attachments/assets/973b54e4-cd86-4df7-9c48-7773ca861357" />

## Table of Contents

- [How Big is the Problem?](#how-big-is-the-problem)
- [How Toll Fraud Happens](#how-toll-fraud-happens)
- [Practical Demonstration of Toll Fraud](#practical-demonstration-of-toll-fraud)
- [Why Current Solutions Fail](#why-current-solutions-fail)
- [Previous Work](#previous-work)
- [Conclusion](#conclusion)
- [Bibliography](#bibliography)

---

## How Big is the Problem?

Toll fraud is a growing global issue affecting businesses of all sizes.

### Money Lost
- **Global Losses:** Telecom fraud caused losses of $38.95 billion globally in 2023, with toll fraud being a top contributor.  
  — Philippines [2023]
- **Individual Impact:** A single toll fraud incident can cost companies thousands up to $500,000.  
  — Group [2017]

### Other Impacts
- **Operational Disruption:** Fake calls clog lines, stopping normal business.  
  — Dexatel [2016]
- **Reputation Damage:** Clients lose trust if a business’s system is used in fraud.  
  — AVOXI [2019]
- **Legal Risks:** Fraudulent activity may lead to legal consequences depending on call content and destination.  
  — Defense

---

## How Toll Fraud Happens

Toll fraud typically happens in three stages: infiltration, execution, and evasion.  
— Defense

### Stage 1: Getting In
- Weak passwords (e.g., default "1234").  
- Unsecured VoIP ports due to firewall misconfiguration.  
- Voicemail exploits allowing outbound calls.  
- Phishing for employee login credentials.  
— Dexatel [2016], Defense

### Stage 2: Making the Calls
- Bulk autodialing of premium numbers.  
- Attacks usually occur off-hours (night/weekends).  
— Dexatel [2016]

### Stage 3: Staying Hidden
- Varying call patterns to avoid detection.  
- Using looped audio to keep calls active longer.  
- Delayed detection after billing.  
— AVOXI [2019], Dialzara [2024], FraudNet [2018]

---

## Practical Demonstration of Toll Fraud

### Setup and Tools

- **VoIP Server:** Asterisk PBX installed on a virtual machine.
- **Softphone Client:** Zoiper for call initiation and reception.
- **Attacker Machine:** Kali Linux with SIPp for call generation.
- **Network Monitoring Tool:** Wireshark for SIP traffic analysis.

### Steps Performed

1. **Deployment of Asterisk PBX:** Configured with weak SIP credentials (e.g., username: 1234, password: 1234) to replicate common security misconfigurations.
2. **Exposing the SIP Port:** Used `svmap` from SIPVicious to scan the target IP (10.100.15.99) for open SIP endpoints.
3. **SIP Endpoint Scanning:** Brute-forced weak SIP credentials using `svcrack` with usernames 1001-1050 and `rockyou.txt` password list.
4. **Unauthorized Access Gained:** Successfully authenticated with weak credentials (id-1001, pass-1234) and registered a SIP softphone client.
5. **Automated Call Generation:** Used SIPp to initiate automated calls to simulated premium-rate numbers, emulating toll fraud.

*(Figures referenced in the original report illustrate these steps.)*

---

## Why Current Solutions Fail

### Phone Bill Review
- Detection is often post-incident after bill review.  
- Problem: Too late, money is already lost.  
— AVOXI [2019]

### Rules-Based Filters
- Blocking certain countries or limiting calls.  
- Problem: Rigid filters cause false positives and miss new tactics.  
— FraudNet [2018]

### Firewalls and Passwords
- Strong passwords and firewalls help but are insufficient.  
- Problem: Skilled attackers bypass these defenses.  
— Defense

### What’s Needed
- Real-time, intelligent detection systems, especially AI-driven, to learn call patterns and detect fraud live.  
— iCONX Solutions, Mode [2019]

---

## Previous Work

- **Toll-Fraud Protection:** Call limits, destination filtering, and multi-layered security.  
  — Society [2018]
- **VoIP Fraud Survey:** Highlights vulnerabilities due to lack of built-in fraud defense.  
  — ResearchGate [2014]
- **AI-Based Detection:** Autoencoders detect anomalies without prior examples.  
  — Mode [2019]
- **Supervised Learning:** AI models trained on past fraud detect patterns in real-time.  
  — iCONX Solutions

---

## Conclusion

Toll fraud remains a significant issue, costing companies billions annually. Our demonstration showed that simple, unsecured phone systems are easy targets for attackers using basic tools. Traditional reactive methods like bill reviews are too slow and leave businesses vulnerable.

The only effective defense is switching to proactive, intelligent, real-time security systems. These systems learn normal network behavior and block suspicious activity before losses occur. Moving from old reactive methods to smart proactive approaches is essential to stay safe in today's digital world.

---

## Bibliography

- Abdulrazaq Alsuhail Almutairi. Toll-fraud protection, detection and prevention. *International Journal of Intelligent Computing Research*, 9(3):939–943, 2018.
- AVOXI. Preventing toll fraud from dismantling your VoIP operations. AVOXI, 2019. [https://www.avoxi.com/blog/telecom-fraud-detection-prevention/](https://www.avoxi.com/blog/telecom-fraud-detection-prevention/).
- Startup Defense. Toll fraud exposed: Understanding risks and prevention. Startup Defense. [https://www.startupdefense.io/cyberattacks/toll-fraud](https://www.startupdefense.io/cyberattacks/toll-fraud).
- Dexatel. What is toll fraud? Dexatel, 2016. [https://dexatel.com/glossary/toll-fraud/](https://dexatel.com/glossary/toll-fraud/).
- Dialzara. Telecom fraud analytics: Key trends 2024. Dialzara, 2024. [https://dialzara.com/blog/telecom-fraud-analytics-key-trends-2024](https://dialzara.com/blog/telecom-fraud-analytics-key-trends-2024).
- FraudNet. Rules-based fraud detection definition. FraudNet, 2018. [https://www.fraud.net/glossary/rules-based-fraud-detection](https://www.fraud.net/glossary/rules-based-fraud-detection).
- IVR Technology Group. Toll fraud costs businesses billions. IVR Technology Group, 2017. [https://www.ivrtechgroup.com/security-compliance/toll-fraud-costs-businesses-billions](https://www.ivrtechgroup.com/security-compliance/toll-fraud-costs-businesses-billions).
- Dirk Hoffstadt, Erwin Rathgeb, Matthias Liebig, Ralf Meister, Yacine Rebahi, and Tran Quang Thanh. A comprehensive framework for detecting and preventing VoIP fraud and misuse. In *2014 International Conference on Computing, Networking and Communications (ICNC)*, pages 807–813, 2014. doi: 10.1109/ICCNC.2014.6785441.
- iCONX Solutions. Unveiling the power of AI in telecom fraud detection. iCONX Solutions. [https://www.iconxsolutions.com/ai-combat-wholesale-telecom-fraud-anomaly-detection/](https://www.iconxsolutions.com/ai-combat-wholesale-telecom-fraud-anomaly-detection/).
- The Fast Mode. AI for telecom fraud detection: Revolutionizing security in the digital age. The Fast Mode, 2019. [https://www.thefastmode.com/expert-opinion/40617-ai-for-telecom-fraud-detection-revolutionizing-security-in-the-digital-age](https://www.thefastmode.com/expert-opinion/40617-ai-for-telecom-fraud-detection-revolutionizing-security-in-the-digital-age).
- TransUnion Philippines. Global telecoms hit hard: $38.95 billion lost to fraud in 2023. TransUnion Philippines, 2023. [https://www.transunion.ph/blog/global-telecoms-hit-hard-38-95-billion-lost-to-fraud-in-2023](https://www.transunion.ph/blog/global-telecoms-hit-hard-38-95-billion-lost-to-fraud-in-2023).
- ResearchGate. A survey on fraud and service misuse in voice over IP (VoIP) networks. ResearchGate, 2014. [https://www.researchgate.net/publication/257547588_A_survey_on_fraud_and_service_misuse_in_voice_over_IP_VoIP_networks](https://www.researchgate.net/publication/257547588_A_survey_on_fraud_and_service_misuse_in_voice_over_IP_VoIP_networks).
- Infonomics Society. Toll-fraud protection, detection and prevention. Infonomics Society, 2018. [https://infonomics-society.org/wp-content/uploads/ijisr/published-papers/volume-8-2018/Toll-Fraud-Protection-Detection-and-Prevention.pdf](https://infonomics-society.org/wp-content/uploads/ijisr/published-papers/volume-8-2018/Toll-Fraud-Protection-Detection-and-Prevention.pdf).

