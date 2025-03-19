# Wazuh

EDR solutions are exactly. Endpoint detection and response (EDR) are a series of tools and applications that monitor devices for an activity that could indicate a threat or security breach. These tools and applications have features that include:

* Auditing a device for common vulnerabilities
* Proactively monitoring a device for suspicious activity such as unauthorised logins, brute-force attacks or privilege escalations
* Visualising complex data and events into neat and trendy graphs
* Recording a device's normal operating behaviour to help with detecting anomalies



Created in 2015, [Wazuh](https://wazuh.com) is an open-source, freely available and extensive EDR solution. It can be used in all scales of environments. Wazuh operates on a management and agent module. Simply, a device is dedicated to running Wazuh named a manager, where Wazuh operates on a management and agent model where the manager is responsible for managing agents installed on the devices you’d like to monitor. Let's look at this model in the diagram below:

<figure><img src="../../../../../.gitbook/assets/4c008954c296fe1fbca005637af73ea1.png" alt=""><figcaption></figcaption></figure>







## Wazuh agent

Devices that record the events and processes of a system are called agents. Agents monitor the processes and events that take place on the device, such as authentication and user management. Agents will offload these logs to a designated collector for processing, such as Wazuh.

In order for Wazuh to be populated, agents need to be installed onto devices to log such events. Wazuh can guide you through the agent deployment process provided with agent wizard.





