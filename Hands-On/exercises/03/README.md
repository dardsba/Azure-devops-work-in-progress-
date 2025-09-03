# Lab 03: Azure Firewall (Exercise 3)

This exercise demonstrates how to deploy and configure **Azure Firewall** to control network traffic between subnets and the internet.  
**Customizations applied:**  
- Used **VM and sizes** due to quota/availability.
- Changed **OS disk type** and **storage tier** for performance/cost optimization.
- Verified connectivity after deployment and restarted VMs when needed.

---

## Lab Scenario (condensed)

- Deploy a **hub-and-spoke** network topology:
  - **Hub VNet** with Azure Firewall.
  - **Spoke VNets** hosting workloads (two VMs).
- Configure **User Defined Routes (UDRs)** to route traffic through the firewall.
- Validate that traffic flows through the firewall and rules are enforced.

---

## Tasks Overview

### Task 1 — Deploy the Hub VNet and Azure Firewall
- **Hub VNet** with dedicated subnet `AzureFirewallSubnet`.
- Deploy **Azure Firewall** in the hub.
- Configure **Firewall Policy** with rules for outbound internet access.

---

### Task 2 — Deploy Spoke VNets and VMs
- Two spoke VNets (e.g., `Spoke1`, `Spoke2`).
- Each spoke hosts a VM:
  - **Custom VM sizes** (e.g., `Standard B2ms` instead of D-series).
  - **OS Disk:** Changed to `Standard SSD`.
  - **Region:** `Poland Central` (original lab uses East US).
- Ensure **no public IPs** on VMs (traffic must route via firewall).

---

### Task 3 — Configure Routing
- Create **Route Tables** for each spoke.
- Add **UDR**: `0.0.0.0/0` → Next hop: Azure Firewall private IP.
- Associate route tables with spoke subnets.

---

### Task 4 — Validate Connectivity
- From Spoke VMs:
  - Test outbound internet access (should succeed via firewall).
  - Test blocked traffic per firewall rules.
- Verified by:
  - Restarting VMs after deployment.
  - Checking **effective routes** in NIC settings.
  - Using `Test-NetConnection` in PowerShell.

---

## Custom Fixes & Troubleshooting Notes
- **VM Size Adjustments:** Used available sizes in region (e.g., `Standard B2ms`).
- **Disk Tier Changes:** Upgraded to `Standard SSD` for better performance.
- **Connectivity Issues:** Restarted VMs and confirmed UDR associations.
- **Firewall Logs:** Checked in Azure Monitor for rule hits.

---

## Verification Steps
- Confirm **firewall IP** in route tables.
- Validate **firewall rules** in Firewall Policy.
- Test connectivity from VMs:
  - Allowed traffic → succeeds.
  - Blocked traffic → fails.

---

## References
