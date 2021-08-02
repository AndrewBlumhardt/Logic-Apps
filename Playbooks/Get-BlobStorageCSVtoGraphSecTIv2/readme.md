<img src=https://github.com/Azure/Azure-Sentinel/blob/master/Playbooks/logic_app_logo.png alt="LogicApps Logo" width="350" height="200">

# Get-BlobStorageCSVtoGraphSecTIv2
Author: Andrew Blumhardt

This Playbook automates importing CSV files from Azure Blob Storage into a Sentinel Threat Intelligence using the Graph Security API.

One obstacle to importing CSV data using a Logic App is that there is no built-in CSV-to-JSON parser. This playbook demonstrates using the Log Analytics externaldata operator as a workaround. By reading the data using the Log Analytics Data Collector activity, you can avoid the need to use a CSV-to-JSON parser.

V1 is a simple option that may be easier for reuse and V2 has more complex options.

## Playbook Options:
1. The logic app is configured to read one CSV files from a target storage container
2. Option to exclude the first title column from the CSV file(s)

## Prerequisites:
1. Prepare a CSV sample file (template provided if needed)
2. Create an Azure Storage account and container
3. Upload a sample import CSV file to the storage container
4. Activate the Threat Intelligence Platforms connector in Sentinel
5. Setup an App registration (assigning ThreatIndicators.ReadWrite.OwnedBy)

NOTE: The TI Platform connector will link Sentinel to the Graph Security API indicator list. The IOCs are joined to the ThreatIntelligenceIndicator table. Ingesting new indicators using the Graph Security API may involve a short delay before being visible in Sentinel.

## Instructions for deployment and setup
1. Set the Sentinel resource group and workspace name
2. Deploy the template
3. Authorize the API-based activities (key-based read access recommended for the blob container)
4. Set the Tenant, App ID, and key for the API connection
5. Add a JSON-style column list (example provided) based on your CSV file

NOTE: By default, Blob Storage actions can read or write files that are 50 MB or smaller. Chunking is suported for larger files.

## Considerations and potential enhancements
* The Grpah Security API has specific input requirements that are provided the template file. Avoid removing colums from the template unless repalacing with static values.
* There are several required values that can be hard coded or replaced with internal variables (rather than cluttering up your CSV file). See the Confidence Score variable in the playbook as an example.
* The ThreatType column is required to meet specific API requirements (this is the key-value to the case statement).
* Use a key value name to avoid importing duplicate records
* Consider adding activities to archive CSV files after processing
* Consider testing a blob-update trigger

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fgithub.com%2FAndrewBlumhardt%2FLogic-Apps%2Fblob%2FPlaybooks%2FPlaybooks%2FGet-BlobStorageCSVtoWatchlist%2Fazuredeploy.json)
[![Deploy to Azure Gov](https://aka.ms/deploytoazuregovbutton)](https://portal.azure.us/#create/Microsoft.Template/uri/https%3A%2F%2Fgithub.com%2FAndrewBlumhardt%2FLogic-Apps%2Fblob%2FPlaybooks%2FPlaybooks%2FGet-BlobStorageCSVtoWatchlist%2Fazuredeploy.json)

## References:
* <a href="https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/externaldata-operator?pivots=azuremonitor" target="_blank">External Data Operator Documentation</a>
* <a href="https://docs.microsoft.com/en-us/azure/connectors/connectors-create-api-azureblobstorage" target="_blank">Create and manage blobs in Azure Blob Storage by using Azure Logic Apps</a>
* <a href="https://docs.microsoft.com/en-us/graph/api/resources/tiindicator" target="_blank">Graph Security API - tiindicator Documentation</a>
* <a href="https://thewindowsupdate.com/2020/02/11/bring-your-threat-intelligence-to-azure-sentinel/" target="_blank">Example of Creating App Registration for the Graph Security API</a>

## Suggestions and feedback
Let me know if you run into any problems or share your suggestions and feedback by sending email to andrew.blumhardt@microsoft.com
