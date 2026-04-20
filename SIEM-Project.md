# SIEM Project Report


## Purpose of the Project

The purpose of this project was to design, deploy, and configure a Security Information and Event Management (SIEM) solution within a virtualized environment, in order to gain practical experience with security monitoring and SOC (Security Operations Centre) workflows.

Key Outcomes:
- Successfully deployed a functional SIEM using Wazuh across multiple virtual machines.
- Ingested and analyzed system logs, focusing on authentication and security-related events.
- Observed and interpreted alerts, including classification using the MITRE ATT&CK framework.
The project focused on building a foundational SIEM environment rather than a production-scale deployment.

## Tools & Environment

SIEM Platform: Wazuh

Virtual Lab Setup: Ubuntu 64-bit

Architecture: Distributed SIEM setup with a centralized server and monitored endpoint agent

## Implementation

**Step 1 – Installation & Configuration:**

The initial phase of the project involved preparing the virtual environment and successfully deploying the Wazuh SIEM solution across multiple virtual machines.

To support the installation requirements, disk space on the Ubuntu virtual machine was expanded using GParted. The lsblk command was used to identify the primary partition, which was then resized to ensure sufficient capacity for the Wazuh installation.

Following system preparation, two separate Ubuntu virtual machines were configured to simulate a basic monitored network environment:

- Wazuh Server VM – Responsible for log collection, analysis, and management 
- Wazuh Agent VM – Configured to generate and forward logs to the server

Required dependencies such as curl were installed to facilitate package retrieval and installation.

The Wazuh server was installed using the official installation script, which automates the deployment of core components including the Wazuh manager, indexer, and dashboard. Once installed, the dashboard interface was accessed via a web browser to confirm successful deployment.

On the second virtual machine, the Wazuh agent was installed and configured to communicate with the server by specifying the server’s IP address. The agent was then registered and connected to the Wazuh manager.

Successful communication between the agent and server was verified through the Wazuh dashboard, where the agent appeared as active and began forwarding system logs for analysis.

This setup established a functional SIEM environment capable of collecting and monitoring endpoint activity across multiple systems.
 
<br>

**Step 2 – Data Sources:**

Following the successful deployment of the SIEM, log collection was validated using the Wazuh agent installed on the endpoint virtual machine.

The primary data source for this project was Linux authentication logs located at /var/log/auth.log, which record login attempts, authentication failures, and privilege escalation activity.

The Wazuh agent was configured to monitor these logs and forward them to the Wazuh manager in real time.

To generate relevant security events, authentication failures and privilege escalation attempts were simulated using system commands.

These activities produced log entries which were successfully ingested, processed, and analysed by the SIEM.
  

<br>

**Step 3: Analysis of Findings**

The simulated attacks demonstrated how SIEM systems transform raw log data into actionable security insights.

The detection of failed privilege escalation attempts highlights how seemingly simple system events can indicate potentially malicious behavior. By correlating repeated authentication failures, Wazuh was able to classify the activity within the MITRE ATT&CK framework, providing additional context for analysis.

This reinforces the importance of centralized logging and automated detection in identifying early indicators of compromise.


## Challenges & Lessons Learned

A key challenge was understanding why certain logs were not immediately visible in the SIEM, which required troubleshooting log sources and agent configuration.

Interpreting detected events also required deeper analysis, as activities such as failed su attempts were classified as privilege escalation rather than simple login failures.

Additionally, setting up the virtual environment presented challenges such as disk management and dependency configuration.

These challenges improved my understanding of log ingestion, event classification, and the importance of accurate configuration in security monitoring systems.

## Future Improvements

Future improvements to this project would focus on expanding both the scope of data collection and the sophistication of detection and response capabilities.

One key enhancement would be the integration of automated response mechanisms, such as triggering alerts or predefined actions when suspicious activity is detected. For example, repeated failed authentication attempts or indicators of privilege escalation could automatically initiate defensive measures such as blocking IP addresses or isolating affected systems.

Additional log sources could also be incorporated, including network traffic and application logs, to provide a more comprehensive view of system activity and improve detection accuracy.

Further development would include creating custom detection rules and refining dashboards to better visualize threats and trends over time.

Finally, more advanced attack simulations, such as privilege escalation techniques or malware execution scenarios, could be implemented to further test and validate the effectiveness of the SIEM environment

## Conclusion

This project successfully demonstrated the deployment and use of a SIEM platform to monitor and analyze system activity. Through simulating attack scenarios and observing detection mechanisms, I developed a practical understanding of how security operations centers identify and respond to threats.

The experience strengthened my knowledge of log analysis, detection workflows, and real-world security monitoring practices.
