# Defensive Security

**By Leo, Michele, Akiel & Preen**

## Table of Contents
- [Monitoring Environment](#monitoring-environment)
- [Common Information Model (CIM)](#common-information-model-cim)
- [Windows Logs](#windows-logs)
- [Apache Logs](#apache-logs)
- [Attack Analysis](#attack-analysis)
- [Summary and Future Mitigations](#summary-and-future-mitigations)

## Monitoring Environment

### Scenario
We are a team of SOC analysts working for VSI (Virtual Space Industries). VSI hired us because of rumors that a competitor may have launched cybersecurity attacks with the intention to disrupt business.

Using Splunk, we monitor VSI against these potential attacks by examining the following:
- Compare VSI’s Windows Server Logs to the attack logs
- Look at the Apache web server and compare those to their attack logs

## Common Information Model (CIM)

### Purpose
- **Normalization**: Maps raw data fields to CIM data models using field aliases, calculated fields, lookups, and tags.
- **Compatibility**: Ensures data from diverse sources can be used with Splunk apps.
- **Simplification**: Reduces the effort needed to search and analyze data from varied sources.

### Key Components
- **Data Models**: Predefined data schemas for different domains.
- **Field Aliases and Field Extractions**: Maps raw data fields to CIM-compliant names.
- **Tags**: Applied to events for classification.
- **Macros and Lookups**: Simplify complex queries and enhance data correlation.

### Best Practices
- Map data to CIM early.
- Regularly review CIM compliance.
- Validate data models using tools like the Splunk CIM Validator.

### How it Works
- Install the Splunk Add-on for CIM.
- Enable and configure the appropriate data models.
- Map data sources to the CIM schema using aliases, fields, and tags.

### Simple Scenario: Data Normalization with CIM
Imagine a company collects log data from two systems, but the fields for IP addresses are labeled differently. CIM normalizes these fields into a common field called `ip`.

### Logs Analyzed
- **Windows Logs**: Logs for VSI's main website and Windows Server.
- **Apache Logs**: Logs for the Apache web server.

## Windows Logs

### Reports Designed
- **ID Number Associated with Specific Signature**: Shows the ID number for Windows activity.
- **Windows Logs Severity**: Quick overview of the severity levels in the logs.
- **Success and Failure - Windows**: Displays failed activity levels.

### Alerts Designed
- **Suspicious Activity VSI**: Threshold for failed Windows activity reached.
- **Successful Logins VSI**: Monitors successful login attempts.
- **VSI Deleted User Accounts**: Monitors the deletion of user accounts.

### Dashboards
- **Windows Logs Dashboard**: Displays various Windows server log data.

## Apache Logs

### Reports Designed
- **HTTP Methods**: Provides insight into the types of HTTP methods used.
- **Top 10 Domains**: Shows the top 10 domains referring to VSI's website.

### Alerts Designed
- **HTTP POST Count Alert**: Alerts when POST requests exceed a threshold.
- **International Activity Alert**: Flags activity from countries outside the U.S.

### Dashboards
- **Apache Logs Dashboard**: Displays HTTP methods, error codes, and more.

## Attack Analysis

### Attack Summary – Windows
- Increased attempts to reset account passwords and lock out users.
- Suspicious activity from user_a and user_k.

### Attack Summary – Apache
- High volumes of international activity detected between 8pm and 9pm.
- Suspicious POST activity and HTTP methods detected during an attack.

## Summary and Future Mitigations

### Project Summary
On March 25, 2020, VSI faced multiple attacks on their Windows and Apache servers, including brute force password attacks from various regions globally.

### Future Mitigations
- Implement two-factor authentication.
- Lock users out after a set number of failed login attempts.

## Conclusion
This project demonstrates the importance of monitoring network traffic and logs for suspicious activity to protect business systems from cyber threats.

