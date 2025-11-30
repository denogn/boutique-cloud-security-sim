# Architecture

## 1. High-Level Overview

This project simulates a small boutique’s cloud environment in Azure with a focus on:

- Identity & role-based access control (RBAC)
- Network segmentation and secure remote access
- Centralized logging and monitoring
- Governance (policy + tagging)
- Basic incident detection and response

All resources are deployed into a **single, isolated resource group** to keep the simulation contained and easy to tear down.

---

## 2. Logical Architecture Diagram

```text
+---------------------------------------------------------------+
|                      Azure Subscription                       |
|                                                               |
|  +--------------------- Resource Group ---------------------+ |
|  |                      RG-BoutiqueSim                     | |
|  |                                                         | |
|  |  +--------------------+      +-----------------------+  | |
|  |  |   VNet-Boutique    |      |   Azure AD / IAM      |  | |
|  |  |                    |      |                       |  | |
|  |  |  +--------------+  |      |  OwnerA / OwnerB      |  | |
|  |  |  | App-Subnet   |  |      |  EmployeeA / EmployeeB|  | |
|  |  |  |  +--------+  |  |      |  Analyst              |  | |
|  |  |  |  | Linux  |<-NSG------>|  TestAttacker (sim)   |  | |
|  |  |  |  |  VM    |  |  |      +-----------------------+  | |
|  |  |  |  +--------+  |  |                                  |
|  |  |  +--------------+  |                                  |
|  |  |  +--------------+  |                                  |
|  |  |  | Mgmt-Subnet |  |                                  |
|  |  |  +--------------+  |                                  |
|  |  +--------------------+                                  |
|  |                                                         | |
|  |  +---------------------+                                | |
|  |  | Log Analytics       |                                | |
|  |  | Workspace           |<------ VM logs, NSG logs -----+| |
|  |  +---------------------+                                | |
|  |                                                         | |
|  |  +---------------------+                                | |
|  |  | Azure Policy        |--> Restrict region to US East  | |
|  |  +---------------------+                                | |
|  +---------------------------------------------------------+ |
+---------------------------------------------------------------+
