# iotc-edgemodule-vm-deploy

Detailed documentation is available on [Microsoft Docs](https://docs.microsoft.com/en-us/azure/iot-edge/how-to-install-iot-edge-ubuntuvm?WT.mc_id=github-iotedgevmdeploy-pdecarlo)

## ARM Template to deploy IoT Edge enabled VM pre-configured for an IoT Central edge module

ARM template to deploy a VM with IoT Edge pre-installed and configured for an IoT Central edge module (via cloud-init)

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fiot-for-all%2Fiotc-edgemodule-vm-deploy%2Fmaster%2FedgeDeploy.json" target="_blank">
    <img src="https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazure.png" />
</a>

The ARM template visualized for exploration

<a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2Fiot-for-all%2Fiotc-edgemodule-vm-deploy%2Fmaster%2FedgeDeploy.json" target="_blank">
    <img src="https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/visualizebutton.png" /></a>

This template can be used to quickly provide an IoT Edge device to host your module. When you don't have access to a network or a host device to use on your network you can use an Azure VM to simulate a host Edge device. This template will deploy an Azure VM with the latest IoT Edge runtime pre-installed and  pre-configured for DPS Symmetric Key Provisioning for your IoT Central Edge deployment. Simply provide your IoT Central Application `Scope Id`, `Device Id`, and `Device Key`. You can obtain these from your IoT Central Application to use in the template.

## Azure CLI command to deploy IoT Edge enabled VM with IoT Central edge module

```bash
az deployment group create \
  --subscription "<SUBSCRIPTION_NAME>" \
  --name edgeModuleVM \
  --resource-group "<RESOURCE_GROUP_NAME>" \
  --template-file edgeDeploy.json \
  --parameters dnsLabelPrefix="edgeModuleDeploy" \
  --parameters adminUsername="<AZURE_USER>" \
  --parameters scopeId="<IOT_CENTRAL_APP_SCOPE_ID>" \
  --parameters deviceId="<IOT_CENTRAL_DEVICE_ID>" \
  --parameters deviceKey="<IOT_CENTRAL_DEVICE_KEY" \
  --parameters authenticationType="sshPublicKey" \
  --parameters adminPasswordOrKey="$(< ~/.ssh/id_rsa.pub)"
```

# Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
