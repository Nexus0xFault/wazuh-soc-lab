# Wazuh SOC Lab

A home Security Operations Center (SOC) laboratory built using Wazuh and Elastic Stack.

This project simulates a real-world SOC environment for monitoring, detecting, and analyzing security events across Linux and Windows endpoints.

---

## 🎯 Objective

The goal of this lab is to demonstrate practical SOC analyst skills, including:

- Log collection from multiple endpoints
- Threat detection using SIEM rules
- Incident identification and analysis
- Security event visualization in dashboards

---

## 🏗️ Architecture

The environment consists of:

- Debian Linux machine (attacker / endpoint)
- Windows machine (SOC server + Wazuh manager)
- Wazuh Agent for log forwarding
- Elastic Stack (Kibana) for visualization

See `architecture.png` for full diagram.

---

## ⚙️ Technologies Used

- Wazuh (SIEM & XDR)
- Elastic Stack (Kibana)
- Linux (Debian)
- Windows 10/11
- Docker (optional deployment)

---

## ⚔️ Simulated Attacks

- SSH brute-force attack

---

## 📊 Features

- Real-time log monitoring
- Security alerts and rule-based detection
- Dashboard visualization in Kibana
- Incident analysis and reporting

---

## 📸 Screenshots

Screenshots of dashboards, alerts, and incidents are available in the `/screenshots` folder.

---

## 📌 Purpose

This project was created as a portfolio piece for a SOC Analyst role to demonstrate practical skills in security monitoring and incident detection.
