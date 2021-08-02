<img src=https://github.com/Azure/Azure-Sentinel/blob/master/Playbooks/logic_app_logo.png alt="LogicApps Logo" width="350" height="200">

## Get-BlobStorageCSVtoWatchlist
Author: Andrew Blumhardt

This Playbook automates importing CSV files from Azure Blob Storage into a Sentinel Watchlist. It checks blob storage and imports CSV file(s) into a Sentinel watchlist on a schedule.

One obstacle to importing CSV data using a Logic App is that there is no built-in CSV-to-JSON parser. This playbook demonstrates using the Log Analytics externaldata operator as a workaround. By reading the data using the Log Analytics Data Collector activity, you can avoid the need to use a CSV-to-JSON parser.

## Playbook Options:
1. The logic app is configured to read one or more CSV files from a target storage container
2. Option to exclude the first title column from the CSV file(s)
3. Specify an optional key column to limit ingesting duplicate records (only imports record with unique key values)

## Prerequisites:
1. Prepare a CSV sample file (template provided if needed)
2. Upload a sample CSV file in the Sentinel portal to seed the Watchlist
3. Create an Azure Storage account and container
4. Upload a sample import CSV file to the storage container

## Instructions for deployment and setup
After selecting a playbook, in the Azure portal:
1. Set the Sentinel resource group and workspace name
2. Deploy the template
3. Authorize the API-based activities (key-based read access recommended for the blob container)
3. Set the storage account name and container
4. Set the Watchlist name and optional key column name
5. Add a JSON-style column list (example provided) based on your CSV file

## Considerations and potential enhancements
*Use a key value name to avoid importing duplicate records
*Consider adding activities to archive CSV files after processing
*Consider testing a blob-update trigger

## References:
*https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/externaldata-operator?pivots=azuremonitor

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fgithub.com%2FAndrewBlumhardt%2FLogic-Apps%2Fblob%2FPlaybooks%2FPlaybooks%2FGet-BlobStorageCSVtoWatchlist%2Fazuredeploy.json)
[![Deploy to Azure Gov](https://aka.ms/deploytoazuregovbutton)](https://portal.azure.us/#create/Microsoft.Template/uri/https%3A%2F%2Fgithub.com%2FAndrewBlumhardt%2FLogic-Apps%2Fblob%2FPlaybooks%2FPlaybooks%2FGet-BlobStorageCSVtoWatchlist%2Fazuredeploy.json)

# Suggestions and feedback
Let me know if you run into any problems or share your suggestions and feedback by sending email to andrew.blumhardt@microsoft.com
