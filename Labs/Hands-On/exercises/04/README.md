# Lab 04: Configuring and Securing ACR and AKS (Exercise 1)

This exercise deploys a containerized workload by building an image, storing it in **Azure Container Registry (ACR)**, provisioning **Azure Kubernetes Service (AKS)**, and securing access for both **external** and **internal** services. The official lab covers: creating an ACR, building/pushing an image, creating AKS, granting AKS permissions to pull from ACR, deploying an external service, verifying it, and deploying an internal service and verifying it. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_04_ConfiguringandSecuringACRandAKS.MD)

**Customizations applied (to fit quotas/costs and your environment):**
- **Region:** used `Poland Central` instead of the default East US in the lab. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_04_ConfiguringandSecuringACRandAKS.MD)  
- **AKS node pool VM size:** changed from the default D‑series to `Standard B2ms` (e.g., `Standard B2ms`).  
- **Node OS disk type/tier:** set to `Standard SSD` and adjusted disk size as needed.  
- **ACR SKU (storage tier):** selected `Standard` instead of `Basic/Premium` to balance throughput and cost.  
- Performed **connectivity checks** and **restarted** nodes/pods if needed after changes.

---

## Tasks Overview

### Task 1 — Create Azure Container Registry
Create an ACR in a dedicated resource group for the lab (the official exercise begins by provisioning ACR). [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_04_ConfiguringandSecuringACRandAKS.MD)

### Task 2 — Build and Push the Image
Use a **Dockerfile** to build the sample image locally (Cloud Shell or your dev box) and push it to ACR as `sample/nginx:v1` as per the lab pattern. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_04_ConfiguringandSecuringACRandAKS.MD)

### Task 3 — Create AKS Cluster
Provision **AKS** in `polandcentral` with your **custom node size** and **OS disk tier** (e.g., `Standard SSD`), keeping the control plane public for the lab simplicity. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_04_ConfiguringandSecuringACRandAKS.MD)

### Task 4 — Grant AKS Permissions to Pull from ACR
Attach ACR to AKS using the **`--attach-acr`** integration so the cluster’s kubelet identity is granted **`AcrPull`** automatically; you can do this at creation or later via `az aks update`. [3](https://learn.microsoft.com/en-us/azure/aks/cluster-container-registry-integration)

> **CLI reference:** `az aks update --attach-acr <acrNameOrResourceId>`; use `az aks check-acr` to validate connectivity between the cluster and the registry. [4](https://learn.microsoft.com/en-us/cli/azure/aks?view=azure-cli-latest)

### Task 5 — Deploy the External Service
Apply the provided manifest **`nginxexternal.yaml`** which defines a Deployment and a **LoadBalancer** Service to publish externally; replace `<ACRUniquename>` in the image path. [2](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Allfiles/Labs/09/nginxexternal.yaml)

### Task 6 — Verify External Access
Retrieve the service’s **public IP** and browse to confirm the NGINX response (as outlined in the lab’s verification flow). [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_04_ConfiguringandSecuringACRandAKS.MD)

### Task 7 — Deploy the Internal Service
Apply **`nginxinternal.yaml`** which exposes the app internally (ClusterIP) or via an internal LB pattern per the lab file. [2](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Allfiles/Labs/09/nginxexternal.yaml)

### Task 8 — Verify Internal Access
Use `kubectl` port-forwarding or a jump host/pod to confirm internal reachability as indicated by the lab verification steps. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_04_ConfiguringandSecuringACRandAKS.MD)

---

## Custom Changes You Implemented

- **AKS Node Size:** Switched to `Standard B2ms` to satisfy subscription **quota** and **regional availability** constraints. After scaling, validated pod scheduling.  
- **Node OS Disk Type/Tier:** Set to `Standard SSD` and tuned disk size to balance IOPS/cost for the node pool.  
- **ACR SKU:** Moved to `Standard` for improved throughput over `Basic` while avoiding `Premium` costs.  
- **Connectivity Validation:**  
  - Confirmed AKS↔ACR via `az aks check-acr`. [4](https://learn.microsoft.com/en-us/cli/azure/aks?view=azure-cli-latest)  
  - Ensured ACR pull permissions with `az aks update --attach-acr`. [3](https://learn.microsoft.com/en-us/azure/aks/cluster-container-registry-integration)  
  - Restarted nodes/pods and re‑applied manifests when initial pulls failed (common after identity or SKU changes).

---

## Verification Checklist

- **ACR created** and image `sample/nginx:v1` exists in your registry. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_04_ConfiguringandSecuringACRandAKS.MD)  
- **AKS cluster running** with your customized **VM size** and **disk tier**. [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_04_ConfiguringandSecuringACRandAKS.MD)  
- **AKS has AcrPull** access to ACR (`--attach-acr` used successfully). [3](https://learn.microsoft.com/en-us/azure/aks/cluster-container-registry-integration)  
- **External Service** (`nginxexternal`) has a **public IP** and returns NGINX welcome page. [2](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Allfiles/Labs/09/nginxexternal.yaml)  
- **Internal Service** (`nginxinternal`) reachable only from within the cluster/VNet as designed. [2](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Allfiles/Labs/09/nginxexternal.yaml)

---

## Troubleshooting Tips

- **ImagePullBackOff / Unauthorized:** Re-run `az aks update --attach-acr` (or specify at cluster creation) and wait for role assignment propagation, then redeploy. [3](https://learn.microsoft.com/en-us/azure/aks/cluster-container-registry-integration)  
- **Validate ACR Access Quickly:** Use `az aks check-acr -g <rg> -n <cluster> --acr <acrNameOrId>`. [4](https://learn.microsoft.com/en-us/cli/azure/aks?view=azure-cli-latest)  
- **Manifests:** Ensure image references in `nginxexternal.yaml` and `nginxinternal.yaml` use your actual ACR **login server** name. [2](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Allfiles/Labs/09/nginxexternal.yaml)

---

## References
- Official lab: **Lab 04 – Configuring and Securing ACR and AKS** (AZ‑500). [1](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Instructions/Labs/LAB_04_ConfiguringandSecuringACRandAKS.MD)  
- Lab files: **`nginxexternal.yaml`** and **`nginxinternal.yaml`**. [2](https://github.com/MicrosoftLearning/AZ500-AzureSecurityTechnologies/blob/master/Allfiles/Labs/09/nginxexternal.yaml)  
- ACR↔AKS integration (Learn): `--attach-acr` guidance and role assignment details. [3](https://learn.microsoft.com/en-us/azure/aks/cluster-container-registry-integration)  
