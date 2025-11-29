# Boutique Cloud Security Simulation

## Overview
This project simulates a secure Azure environment for a small boutique that manages inventory, employee access, and business operations.

> 🚨 **SIMULATED SCENARIO**  
> No real names, customer data, or private info. Only fabricated placeholders.

---

## Main Focus
- Identity & RBAC  
- Network segmentation  
- Logging & monitoring  
- Incident detection & response  
- Secure Linux VM setup  
- Governance & policies  

---

## Architecture

### Resource Group
- **RG-BoutiqueSim** — isolated resource group for all simulation assets

### Users (Azure AD)
- `OwnerA`, `OwnerB`  
- `EmployeeA`, `EmployeeB`  
- `Analyst`  
- `TestAttacker` (simulated threat actor)

### Networking
- **VNet:** `VNet-Boutique`  
- **Subnets:**
  - `Mgmt-Subnet`
  - `App-Subnet` (VM lives here)

### Network Security Groups (NSGs)
- Block all inbound ports  
- Allow SSH (22) only for:
  - Owners  
  - Analyst  
- Temporarily allow SSH from `TestAttacker` for simulated attack  

### Linux VM
Used for:
- Employee access  
- Dummy inventory files  
- SSH credential management  
- Logging & monitoring  
- Attack detection  

### RBAC Roles

| Role       | Permissions |
|------------|-------------|
| **Owners** | Full control of Resource Group |
| **Employees** | Reader or VM Contributor |
| **Analyst** | Security Reader + Log Analytics Contributor |

---

## Logging & Monitoring
- Log Analytics Workspace (**LAW-Boutique**)  
- Azure Monitor  
- Microsoft Defender for Cloud  

---

## Governance
- **Azure Policy:** Resource deployment restricted to **US East**  
- **Tags:** `Environment=Simulation`  

---

## Incident Simulation

### Scenario: Unauthorized SSH Attempt
1. `TestAttacker` attempts SSH with invalid credentials  
2. VM logs the failed login  
3. Analyst detects the event using Log Analytics  
4. Analyst blocks attacker IP via NSG  
5. Analyst writes a brief incident response report  

---

## Cost Controls
- B1S VM  
- Auto-shutdown enabled  
- Delete RG (**RG-BoutiqueSim**) after demo  

---

## Deliverables
- Architecture diagram  
- Build guide  
- Permission tables  
- Attack simulation steps  
- Logs & screenshots  
- Incident response documentation

---

## Documentation

- [Architecture](docs/architecture.md)
- [Build Guide](docs/build-guide.md)
- [RBAC Design](docs/rbac-design.md)
- [NSG Rules](docs/nsg-rules.md)
- [Incident Simulation](docs/incident-simulation.md)
- [Incident Response Report](docs/incident-response-report.md)

