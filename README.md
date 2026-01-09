# Scoping your CDE

Generally speaking, scoping can be defined as the identification and tracking of people, processes, and technologies that directly interact with account data or could impact the security of account data in your cardholder data environment (CDE).

Key items to consider:
- Scoping exercises should be performed annually (_at minimum_)
- Should include validation of people, processes and technologies that handle account data
- Should include the identification of all current and new payment channels
- Include policies and standards that enforce PCI requirements for your organization 

---

<img width="1089" height="760" alt="Screenshot 2026-01-09 063146" src="https://github.com/user-attachments/assets/21d06ebc-c5f2-4568-97ac-e3b0db28ca40" />

# In-scope vs out-of-scope systems

Systems are in-scope when:
- They store, process, or transmit account data
- They are on the same network segment (_i.e., same subnet or VLAN_) as systems that store, process or transmit account data
- They can impact the configurations or security of the CDE 

Systems are out-of-scope when:
- They do **_not_** store, process, or transmit account data
- They are **_not_** on the same network segment (_i.e., same subnet or VLAN_) as systems that store, process or transmit account data
- They **_cannot_** connect to any system in the CDE and do **_not_** impact configurations or security of the CDE

---
# Creating sustainable, long-term processes for success

In this project, we simulate an organization that is just starting their scoping journey with the goal of identifying and tracking both in-scope and out-of-scope systems.

_**Inception State:**_ organization has no existing policies, standards or processes in place to identify their CDE.

_**Completion State:**_ formal policies, standards and processes are created, stakeholders are bought-in to their annual scoping responsibilities, and a full cycle of scoping exercises are is successfully completed.

---

# Technology Utilized
- PowerShell & BASH scripts (rule out storage of account data across the organization)

---

# Table of Contents

- [Gather a full list of merchant IDs (MIDs)](#step-1-gather-a-full-list-of-MIDs)
- [Creating data flow diagrams](#step-2-creating-data-flow-diagrams)
- [Creating network diagrams](#step-3-creating-network-diagrams)
- [Identifying in-scope software](#step-4-identifying-in-scope-software)
- [Identifying in-scope hardware](#step-5-identifying-in-scope-hardware)
- [Identifying in-scope policies and standards](#step-5-identifying-in-scope-policies-and-standards)

---

### Step 1) Gather a full list of MIDs

---

### Step 2) Creating data flow diagrams

---

### Step 3) Creating network diagrams

---

### Step 4) Identifying in-scope software

---

### Step 5) Identifying in-scope hardware

---

### Step 6) Identifying in-scope policies and standards

---
