# Code Pipeline Configuration Instructions

The following document elaborates in detail the method by which you can update your naming and IP scheme prior to running the code pipeline.
Please see [Landing Zone Base Cloud Architecture Instructions](LandingZone_BaseCloudArchitectureInstructions.pdf)

# Azure Terraform Deployments Example

This folder contains example deployments you can use to get familiar with Azure and understand how you can deploy complex infrastructure using Terraform configuration files and modules.

The basic steps to deploy a Demo infrastructure in your own subscription are the following:

1. open a powershell prompt, clone this github repo and login to your azure subscription with:

```powershell
git clone https://github.com/canada-ca/accelerators_accelerateurs-azure.git
az login
az account list
az account set --subscription <subscriptionID from previous command>
```

2. Go in the 1st demo folder with:

```powershell
cd accelerators_accelerateurs-azure/Deployments/terraform/demo/<firewall of choice>/infra
```

3. Initialise and deploy the base network and keyvault infrastructure with:

```powershell
terraform init
terraform apply
```

4. Go in the firewall folder. If using the fortigate firewall, copy the fwconfig/coreA-lic-demo.conf to fwconfig/coreA-lic.conf and fwconfig/coreB-lic-demo.conf to fwconfig/coreB-lic.conf and replace the license section at the bottom of the files with your own fortigate license
5. Initialise and deploy the HA firewall infrastructure with:

```powershell
terraform init
terraform apply
```

6. Go in the demo-servers folder
7. Initialise and deploy the demo server infrastructure with:

```powershell
terraform init
terraform apply
```

8. In the Azure Portal look at the Demo-FW-B-EXT-PubIP resource in the Demo-Core-FWCore-RG resourcegroup to obtain the IP address you will need to connect to the demo web server and jumpbox with:

```text
http://<Demo-FW-B-EXT-PubIP>

RDP to <Demo-FW-B-EXT-PubIP>
```
