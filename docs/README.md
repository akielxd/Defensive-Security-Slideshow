# Defensive Security (Log analysis and Attack Detection)

**By Leo, Michele, Akiel & Preen**

## Table of Contents
- [Project Overview](#project-overview)
- [Monitoring Environment](#monitoring-environment)
- [Windows Logs Analysis](#windows-logs-analysis)
- [Apache Web Server Logs Analysis](#apache-web-server-logs-analysis)
- [Review Questions](#review-questions)
- [Summary and Future Mitigations](#summary-and-future-mitigations)

---

## Project Overview

In this project, we analyzed various security logs from a Windows Server and Apache Web Server to detect suspicious activities using tools like Splunk and Elasticsearch. We explored different log sources and created alerts based on log anomalies to understand the security posture of the system.

---

## Monitoring Environment

The monitoring environment includes two main log sources:
- **Windows Server Logs**: Capturing activities on the server and user logins.
- **Apache Web Server Logs**: Capturing HTTP requests and response codes for web traffic.

Both log types were analyzed for any unusual activity indicative of a security incident.

---

## Windows Logs Analysis

We used Splunk to analyze Windows Server logs and assess the severity of various events. Key findings include:
- **Severity Changes**: A significant increase in high-severity events was observed, indicating a potential attack.
- **Failed Activities**: A decrease in failed activities was noted, while successful activities increased.
- **Alert Threshold**: Thresholds for failed logins and activities were set to minimize alert fatigue while ensuring significant events are flagged.

---

## Apache Web Server Logs Analysis

The Apache Web Server logs revealed several patterns of suspicious activity:
- **HTTP Methods**: A drastic increase in POST methods was detected, indicating potential data exfiltration attempts.
- **Referrer Domains**: Changes in the top 10 referrer domains were observed, signaling possible malicious traffic sources.
- **International Activity**: A surge in traffic from non-local regions triggered alerts for potential international attacks.

---

## Review Questions

### Windows Server Log Questions

#### Report Analysis for Severity
- **Did you detect any suspicious changes in severity?**
  Our Splunk report detected a significant increase in high-severity events from 7% in normal logs to 20% in attack logs.

#### Report Analysis for Failed Activities
- **Did you detect any suspicious changes in failed activities?**
  We saw a significant decrease in failed activities, while successful activities increased.

#### Alert Analysis for Failed Windows Activity
- **Did you detect a suspicious volume of failed activity?**
  Yes, 35 failed Windows activities occurred at 08:00 AM on March 25, 2020.

#### Alert Analysis for Successful Logins
- **Did you detect a suspicious volume of successful logins?**
  Yes, there was a suspicious lack of user logins. At 02:00 AM on March 25, 2020, there were 16 successful logins, dropping to 4 by 12:00 PM.

#### Dashboard Analysis for Time Chart of Signatures
- **Does anything stand out as suspicious?**
  Yes, two significant increases were noted in the signatures for "An attempt was made to reset an account password" and "A user account was locked out."

### Apache Web Server Log Questions

#### Report Analysis for HTTP Methods
- **Did you detect any suspicious changes in HTTP methods?**
  Yes, POST methods had a drastic increase, potentially indicating an attack vector.

#### Report Analysis for Referrer Domains
- **Did you detect any suspicious changes in referrer domains?**
  Yes, suspicious changes were observed in the top 10 referrer domains.

#### Alert Analysis for International Activity
- **Did you detect a suspicious volume of international activity?**
  Yes, international activity peaked at 939 hits at 08:00 AM on March 25, 2020.

#### Dashboard Analysis for Cluster Map
- **Does anything stand out as suspicious?**
  Yes, there was a high volume of activity from cities like Kyiv, Kharkiv, and Lvov in Ukraine.


---

## Summary and Future Mitigations

This project highlights the importance of continuously monitoring security logs to detect suspicious activity in real-time. Based on the findings, we recommend the following mitigations:
- **Review alert thresholds**: Consider creating multiple levels of alerts to reduce alert fatigue while ensuring the SOC team is notified of critical activities.
- **Increase logging granularity**: Collect more detailed logs to better detect and trace suspicious activities, especially in high-risk areas like HTTP POST methods and international activity.
- **Implement behavior analytics**: Use machine learning techniques to identify anomalies in user activity, especially around logins and account-related actions.

---

