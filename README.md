# Create a simple windows VM and configure backup

This template allows you to deploy simple Windows VM and Recovery Services Vault configured with the DefaultPolicy for Protection.

## Deploy using

```
# Login to Azure
az login

# Create Resource Group
az group create \
  --name arm-test-rg \
  --location eastus

# Edit parameters file according to your needs (e.g. for test-vm-01):
vi test-vm-01.parameters.json

# Create Deployment
az deployment group create \
  --name test-vm-01 \
  --resource-group arm-test-rg \
  --template-file azuredeploy.json \
  --parameters test-vm-01.parameters.json
```

## Undeploy using

Prerequisites:
* Make sure to not have any backup data left in the Recovery Services vault before proceeding

```
# Login to Azure
az login

# Delete Deployment (optional)
az deployment group delete \
  --name test-vm-01 \
  --resource-group arm-test-rg

# Delete Resource Group
az group delete --name arm-test-rg
```
