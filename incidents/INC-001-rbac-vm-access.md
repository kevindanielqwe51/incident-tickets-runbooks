INC-001 — RBAC VM Access



Incident ID: INC-001

Severity: Medium

Environment: Microsoft Azure

Category: Identity \& Access / RBAC

Status: Resolved



Summary



Juan is unable to access the required virtual machines in Azure.



Symptom



Juan attempted to access the virtual machines located in the target Resource Group named RG-Operations but was unable to view the resources but his coworker Daniela was able to see and manage them.



The issue affected access to the Azure resources required for his work.



\## Evidence



\### 1. Initial access failure



Juan was unable to view the virtual machines.



![Initial access failure](screenshots/INC-001-01-juan-no-access.png)



\### 2. RBAC assignment



The Administrators group has the Contributor role assigned at the target Resource Group.



![Contributor assignment](screenshots/INC-001-02-contributor-rg.png)



\### 3. Group membership



Juan was added to the Administrators group.



![User added to group](screenshots/INC-001-03-juan-added-group.png)



\### 4. Access restored



Juan was able to access the virtual machines after the RBAC change.



![Access restored](screenshots/INC-001-04-juan-access-restored.png)



Investigation



The initial symptoms indicated that the issue was related to Azure resource access rather than a problem with the virtual machines themselves.



The RBAC configuration of the target Resource Group was reviewed.



The Administrators group had the Contributor role assigned at the Resource Group scope.



The group membership was then checked and Juan was not a member of the Administrators group.



Since Daniela was already able to manage the virtual machines, the VM configuration itself was not considered the primary cause of the incident.



Root Cause



Juan was not a member of the Administrators group that had the required Contributor role assignment on the RG-Operations Resource Group.



As a result, Juan did not inherit the permissions required to view and manage the virtual machines.



Resolution



Juan was added to the Administrators group.



After the RBAC membership change propagated, Juan was able to view and access the virtual machines in RG-Operations.



Prevention

Use group-based RBAC assignments instead of assigning roles individually whenever possible.

Review group membership when users report unexpected access issues.

Document which groups provide access to specific Azure resources.

Apply the principle of least privilege when assigning Azure RBAC roles.

Periodically review group memberships and role assignments.

Lessons Learned



This incident demonstrates the importance of checking identity, group membership, RBAC role assignments, and assignment scope before troubleshooting the underlying Azure resources.



The virtual machines were operational; the issue was caused by missing permissions inherited through group membership.

