# Wazuh Agent Deployment and Configuration Guide

## Introduction
This document provides a comprehensive guide on deploying and configuring the Wazuh agent in your environment. Wazuh is a security monitoring solution that can help you detect and respond to security threats in real-time.

## Prerequisites
- A server with root access.
- Basic understanding of command-line operations.
- Wazuh server up and running.

## Step 1: Download the Wazuh Agent
First, you need to download the Wazuh agent. You can do this by following the official installation instructions for your operating system.

## Step 2: Install the Wazuh Agent
Once downloaded, install the Wazuh agent using the appropriate package manager for your system. For example, in Ubuntu:
```
sudo dpkg -i ./wazuh-agent-<version>.deb
```

## Step 3: Configure the Wazuh Agent
- Open the Wazuh agent configuration file located at `/var/ossec/etc/ossec.conf`.
- Update the following line to point to your Wazuh manager:
```
<manager>Your_Wazuh_Manager_IP</manager>
```

## Step 4: Enable and Start the Agent
Enable the Wazuh agent to start on boot and then start the service:
```
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent
```

## Verification
To verify that the Wazuh agent is running, you can use the command:
```
sudo systemctl status wazuh-agent
```

## Conclusion
You have successfully deployed and configured the Wazuh agent. Make sure to monitor its performance and adjust settings as necessary to ensure optimal operation.