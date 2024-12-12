# Suricata Project: Comprehensive Network Security Monitoring

## Overview
Suricata is a robust open-source network security solution designed to enhance network visibility, detect threats, and provide intrusion detection (IDS) and intrusion prevention (IPS) capabilities. This project demonstrates the deployment, configuration, and utilization of Suricata to improve traffic monitoring and security management. The repository will provide insights into Suricata's features, installation steps, rule creation, and use-case scenarios.

---

## Project Goals

1. **Understand IDS vs IPS**:
   - Differentiate between Intrusion Detection Systems (IDS) and Intrusion Prevention Systems (IPS).
   - Learn how IDS detects and reports threats, while IPS takes automated action against threats.

2. **Install and Configure Suricata**:
   - Successfully install Suricata on a system.
   - Configure necessary rule sets for effective functionality.

3. **Explore Signature and Anomaly-Based Detection**:
   - Leverage custom and built-in rules for threat detection.
   - Understand how Suricata supports various protocols (e.g., TCP, UDP, HTTP).

4. **Conduct Network Monitoring**:
   - Use Suricata to monitor network traffic.
   - Generate and interpret logs and alerts to identify suspicious activities.

5. **Deploy Suricata in IPS Mode**:
   - Automate threat response actions (e.g., dropping malicious packets).
   - Implement proactive security measures.


## Key Features

### 1. Installation
- **Directory Creation**: Properly set up directories for rule storage.
- **Rule Integration**: Add and modify rules from Emerging Threats and custom sources.
- **Configuration**: Adjust default paths and validate service activity.

### 2. Configuration
- Modify rule paths for recognizing diverse files.
- Enable logging for detailed traffic monitoring.

### 3. Traffic Analysis
- Monitor multiple ports and analyze alerts.
- Identify and classify potentially harmful traffic.
- Utilize logs for troubleshooting and performance verification.

### 4. Threat Response
- Automate responses using IPS mode.
- Demonstrate incident response by blocking malicious traffic.

---

## Getting Started

### Prerequisites
- A Linux environment (e.g., Ubuntu or CentOS).
- Root or sudo privileges.

### Installation
# Installing Suricata IDS on Ubuntu Server

1. Install Suricata on the Ubuntu endpoint. We tested this process with version 6.0.8 and it can take some time:
```
sudo add-apt-repository ppa:oisf/suricata-stable
sudo apt-get update
sudo apt-get install suricata -y
```

2. Download and extract the Emerging Threats Suricata ruleset:
```
cd /tmp/ && curl -LO https://rules.emergingthreats.net/open/suricata-6.0.8/emerging.rules.tar.gz
sudo tar -xvzf emerging.rules.tar.gz && sudo mv rules/*.rules /etc/suricata/rules/
sudo chmod 640 /etc/suricata/rules/*.rules
```

3. Modify Suricata settings in the /etc/suricata/suricata.yaml file and set the following variables:
```JavaScript
HOME_NET: "<UBUNTU_IP>"
EXTERNAL_NET: "any"

default-rule-path: /etc/suricata/rules
rule-files:
- "*.rules"

# Global stats configuration
stats:
enabled: Yes

# Linux high speed capture support
af-packet:
  - interface: eth0
```

4. Restart the Suricata service:
```
sudo systemctl restart suricata
```




## Use Cases

### Network Visibility
- Use Suricata to monitor traffic for anomalies, including port scans and unauthorized access attempts.

### Custom Rule Creation
- Create custom rules to detect specific threats relevant to your environment.

### Incident Response
- Deploy in IPS mode to automate actions such as packet dropping, ensuring proactive security.
