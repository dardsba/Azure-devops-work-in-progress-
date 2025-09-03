# Lab 02: Network Security Groups and Application Security Groups (Exercise 2)

This exercise builds on the virtual network and NSG setup from Exercise 1. You will deploy two VMs (Web and Management servers), associate them with Application Security Groups (ASGs), and validate NSG rules.  
**Customizations applied:**  
- Changed **VM sizes** to fit subscription quotas and Cost ( i pay).  
- Adjusted **region** (from East US to Poland Central) for resource availability.  
- Modified **OS disk type** and **storage tier** for cost optimization.  
- Restarted VMs and verified connectivity due to initial deployment issues.

---

## Lab Scenario (condensed)

- Two server groups: **Web Servers** and **Management Servers**.
- Each group in its own **Application Security Group**.
- **RDP** allowed only to Management Servers.
- **HTTP/HTTPS** allowed only to Web Servers.
- Validate NSG rules by testing connectivity.

---

## Tasks Overview

### Task 1 — Create Web Server VM
- **Name:** `myVmWeb`
- **Region:** `<PolandCentral>` (original lab uses East US)
- **Image:** Windows Server 2022 Datacenter (Gen2)
- **Size:** Adjusted from `Standard D2s v3` to `<Standard B2>` (due to quota/availability)
- **OS Disk:** Changed to `Standard SSD` (instead of Standard HDD)
- **Public inbound ports:** None (NSG handles access)
- **Boot diagnostics:** Enabled with managed storage account

---

### Task 2 — Create Management Server VM
- **Name:** `myVmMgmt`
- Same adjustments as Web VM (region, size, disk type)
- **Public inbound ports:** None

---

### Task 3 — Associate NICs with ASGs
- `myVmWeb` → **myAsgWebServers**
- `myVmMgmt` → **myAsgMgmtServers**

---

### Task 4 — Validate Network Filters
- **RDP** into `myVmMgmt` (should succeed)
- **RDP** into `myVmWeb` (should fail)
- **HTTP/HTTPS** to `myVmWeb` (should display IIS page)
- **HTTP/HTTPS** to `myVmMgmt` (should fail)

---

## Custom Fixes & Troubleshooting Notes
- **VM Size Errors:** Adjusted to available sizes in region (e.g., `Standard B2ms`).
- **Region Change:** Used `<Poland Central>` instead of East US for quota compliance.
- **Disk Tier:** Upgraded to `Standard SSD` for better performance.
- **VM Connectivity Issues:** Restarted both VMs and re-checked NSG associations.
- **Validation:** Confirmed RDP and HTTP/HTTPS behavior matched NSG rules.

---

## Verification Steps
- From Azure portal or PowerShell:
  - Check **ASG associations** under each NIC.
  - Review **NSG inbound rules** (Allow-Web-All, Allow-RDP-All).
- Test connectivity:
  - `mstsc` for RDP to Management VM.
  - Browser to Web VM public IP for IIS page.

---

## References
