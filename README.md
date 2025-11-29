# boutique-cloud-security-sim
Created a secure Azure environment for a small boutique that would manage inventory, employee access, and business operations. THIS IS A *SIMULATED* SCENARIO! No real names, customer data, or private info! Only fabricated placeholders! 
Main Focus:
Identity & RBAC
Netwrok Segmentation
Logging & Monitoring
Incident Detection & Response
Secure Linux VM Setup
Governance & Polocies

Architecture:
Resource Group (RG-BoutiqueSim) - single, isolated resource group for all sim assests 
Users (Azure AD) - OwnerA, OwnerB, EmployeeA, EmployeeB, Analyst, TestAttacker (simulated threat actor) 
Networking - VNet (VNet-Boutique) Subnets - (Mgmt-Subnet, App-Subnet)
Network Security Groups (NSGs) - Block all inbound ports, allow SSH only for Owners, Analyst and allow port 22 for TestAttacker temporarily for sim
Linux VM - Employee access, dummy inventory files, SSH credential managment, logging & monitoring, attack detection
RBAC - Owners have full control over the Resource Group (RG-BoutiqueSim), Employee have reader or VM contributor, Analystt has security reader & log nalytics contributor

Logging & Monitoring:
Log Analytics Workspace (LAW-Boutique)
Azure Monitor
Microsoft Defender for Cloud

Governance:
Azure Policy - (Resource deployment restricted to US EAST)
Tags - Environment=Simulation

Scenario: Unauthorized SSH attempt
1 TestAttacker attempts SSH with invalid credentials
2 VM logs failed login
3 Analyst detcts the vent using Log Analytics
4 Analyst blocks attcaker IP via NSG
5 Analyst writes a brief incident response report

Cost Controls:
B1S VM
Auto-shutdown enabled
Delete RG (RG-BoutiqueSim) after demo

Deliverables
Architecture diagram
build guide
Permission tables
Attack sim steps
Logs & screenshots
Incident response documentation
