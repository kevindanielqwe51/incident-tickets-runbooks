\# INC-002 — Client Cannot Connect to Application



\*\*Severity:\*\* Medium

\*\*Status:\*\* Resolved

\*\*Environment:\*\* Azure VM, NSG, Linux, Apache



\## Symptoms



\- Client can ping the application VM.

\- `curl` fails to connect.

\- Apache service is running.



\## Investigation



\- Checked NSG inbound rules.

\- Checked Linux firewall configuration.

\- Identified restrictions affecting TCP port 80.



\## Root Cause



HTTP traffic was blocked by the NSG and Linux firewall.



\## Resolution



Updated the NSG rule to allow HTTP traffic on TCP port 80 and add a firewall rule to allow traffic in port 80.



\## Validation



\- Ping successful.

\- Apache running.

\- HTTP connectivity restored.



\## Evidence





\## Evidence



\### Application Architecture

!\[Application Architecture](https://github.com/kevindanielqwe51/incident-tickets-runbooks/blob/main/screenshots/INC-002-vm-application-arquitecture.png)





\### NSG Blocking Port 80

!\[NSG Blocking Port 80](https://github.com/kevindanielqwe51/incident-tickets-runbooks/blob/main/screenshots//INC-002-NSG-blocking80.png)



\### Initial Troubleshooting

!\[Ping successful but curl failed](https://github.com/kevindanielqwe51/incident-tickets-runbooks/blob/main/screenshots/INC-002-service-running-ping-success-curl-failed.png)



\### Resolution — Apache Working

!\[Apache working after firewall rule was added](https://github.com/kevindanielqwe51/incident-tickets-runbooks/blob/main/screenshots/INC-002-firewall-rule-added-apache-working.png)



