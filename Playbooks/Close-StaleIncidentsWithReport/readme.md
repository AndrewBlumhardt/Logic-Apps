<img src=https://github.com/Azure/Azure-Sentinel/blob/master/Playbooks/logic_app_logo.png alt="LogicApps Logo" width="350" height="200">

# Close-StaleIncidentsWithReport
Author: Andrew Blumhardt

This Playbook closes Sentinel Incidents older than a specified number of days. This may be useful in environments with limited support including labs ane evaluation instances. This may be usefule in a production environment to auto-close incidents before the age out of the primary view.

## Playbook Options:
1. The playbook includes an optional email report
2. The reporting lookback period can be eaily extended if needed
3. The lookup query has a limit of 100 records (which can be easily changed)

## Prerequisites:
1. Consider setting up an administrative email account for notificaiton purposes

## Instructions for deployment and setup
1. Set the Sentinel resource group and workspace name
2. Deploy the template
3. Activate any API-based activities
4. Set the app variables including the stale-days threshold

## Considerations and potential enhancements
* Similar functionality can be managed by (or triggered by) the new Sentinel Automation Rules

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fgithub.com%2FAndrewBlumhardt%2FLogic-Apps%2Fblob%2FPlaybooks%2FPlaybooks%2FGet-BlobStorageCSVtoWatchlist%2Fazuredeploy.json)
[![Deploy to Azure Gov](https://aka.ms/deploytoazuregovbutton)](https://portal.azure.us/#create/Microsoft.Template/uri/https%3A%2F%2Fgithub.com%2FAndrewBlumhardt%2FLogic-Apps%2Fblob%2FPlaybooks%2FPlaybooks%2FGet-BlobStorageCSVtoWatchlist%2Fazuredeploy.json)

## References:
* <a href="https://docs.microsoft.com/en-us/azure/sentinel/automate-incident-handling-with-automation-rules" target="_blank">Automate incident handling in Azure Sentinel with automation rules</a>

## Suggestions and feedback
Let me know if you run into any problems or share your suggestions and feedback by sending email to andrew.blumhardt@microsoft.com
