# VM-Series deployment Template

This ARM template deloy a VM-Series Next Genartion firewall in an Azure resource group, and you can select the following:
- New or existing resource group.
- New or existing Storage account.
- Instance type
- Number of interfaces.
- VNet resource group same or different than the VM instance.
- New or existing VNet.
- New or existing subnets.
- VM-Series PanOS version (Latest , 8.0.0 , or 7.1.0)
- VM-Series SKU (BYOL, Bundle1, or Bundle2)


[<img src="http://azuredeploy.net/deploybutton.png"/>](https://portal.azure.com/#create/Microsoft.Template/uri/https://raw.githubusercontent.com/melamin0/deploy-vmseries/master/azureDeploy.json)
[<img src="https://camo.githubusercontent.com/536ab4f9bc823c2e0ce72fb610aafda57d8c6c12/687474703a2f2f61726d76697a2e696f2f76697375616c697a65627574746f6e2e706e67" data-canonical-src="http://armviz.io/visualizebutton.png" style="max-width:100%;">](http://armviz.io/#/?load=https://raw.githubusercontent.com/melamin0/deploy-vmseries/master/azureDeploy.json)


## Deploy ARM Template using Azure CLI in ARM mode

1. Download the two JSON files: azureDeploy.json and azureDeploy.parameters.json
1. Customize the azureDeploy.parameters.json file and then deploy it from your computer.
1. Install the latest <a href="https://azure.microsoft.com/en-us/documentation/articles/xplat-cli-install/">Azure CLI</a> for your computer.</li>
1. Validate and deploy the ARM template:

``` azure
    azure login
    azure config mode arm
    azure  group  template  validate  -g YourResourceGroupName \
        -e  azureDeploy.json   -f  azureDeploy.parameters.json
    azure group create -v -n YourResourceGroupName -l YourAzureRegion  \
        -d  YourDeploymentLabel  -f azureDeploy.json -e azureDeploy.parameters.json
```

**Check the status of your deployment:**

- CLI: `azure vm show  -g YourResourceGroupName  -n YourDeploymentLabel`
- Azure Portal: Your Resource Group > Deployment or Alert Logs
