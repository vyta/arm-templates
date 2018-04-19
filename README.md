# Deploying ARM Templates

- Using PowerShell

Installing Azure Powershell module:

```powershell
# Check PowerShellGet version 1.1.2.0 or higher
Get-Module -Name PowerShellGet -ListAvailable | Select-Object -Property Name,Version,Path

# Update PowerShellGet if needed (As Administrator)
Install-Module PowerShellGet -Force

# Install and load the Azure Resource Manager modules from the PowerShell Gallery (As Administrator)
Install-Module -Name AzureRM -AllowClobber
# "Yes to All" when prompted

# Load module
Import-Module -Name AzureRM
```

```powershell
Connect-AzureRmAccount

New-AzureRmResourceGroup -Name examplegroup -Location "East US"
New-AzureRmResourceGroupDeployment -ResourceGroupName examplegroup -TemplateFile azuredeploy.json -TemplateParameterFile azuredeploy.parameters.json
```

- Using Azure CLI

Instructions to install the latest Azure CLI can be found [here](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)

```bash
az login

az group create --name examplegroup --location eastus
az group deployment create --resource-group examplegroup --template-file azuredeploy.json --parameters @azuredeploy.parameters.json
```