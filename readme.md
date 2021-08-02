<img src=https://github.com/Azure/Azure-Sentinel/blob/master/Playbooks/logic_app_logo.png alt="LogicApps Logo" width="350" height="200">

# Logic Apps Playbook Lab
author: Andrew Blumhardt

This repository contains Logic Apps that I am currently supporting or testing. I will eventually migrate these to the official Azure Sentinel repository. Intended for testing, peer review, and early access.

Download links will be updated prior to formal publishing. <b>To deploy these templates, download the template manually and paste the contents in the 'Build your own template in the editor' in the Azure portal. </b>

##Inventory:

* Close-StaleIncidentsWithReport - Closes incidents older than the threshold days with an optional email report.
* Get-AlienValut_OTX_V2 - API-based logic app for intesgrating Sentinel and AlienVault Threat Intelligence.
* Get-BlobStorageCSVtoCustomLog - Import CSV files into Log Analytics using a CSV-JSON parser workaround.
* Get-BlobStorageCSVtoGraphSecTIv1 - Import CSV files into Sentinel Threat Intelligence (no frills).
* Get-BlobStorageCSVtoGraphSecTIv2 - Import CSV files into Sentinel Threat Intelligence (testing more options).
* Get-BlobStorageCSVtoWatchlist - Import CSV files into a Sentinel watchlist using a CSV-JSON parser workaround.

## Suggestions and feedback
Let me know if you run into any problems or share your suggestions and feedback by sending email to andrew.blumhardt@microsoft.com
