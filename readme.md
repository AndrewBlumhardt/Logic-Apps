# Get-AlienValut_OTX_V2
author: Andrew Blumhardt

This is a Logic App to import threat indicators from AlienVault into Azure Sentinel using the Graph Security API.

Summary:

Designed to exceed the 1000 workflow limit for large datasets by breaking the results into pages. Set the Lookback to gather historic IOC data. Prevents failed collections when results exceed 1000 records. Tested using 200k records (5 years).

Instructions:
-Get an API key from AlienVault: https://otx.alienvault.com/
-Create an App  Registration in Azure AD:
-Import the Logic App (disabled by default)
-Set the run variables (Tennant ID, Client ID, App Secret, and OTX API Key).
-Enable and run.

Historic Data Lookback (RUN ONCE):
Set the lookback days to a desired value (example 365)
Enable and run the Logic App (estimate 10 minutes processing time for every 10k records)
Set the Lookback days to the default 1 day

Notes:
API sets a record lookup URL for the profile page on AlienVault in “additionalInformation”
API uses the “FileCreatedDateTime” column to log the time ingested

During testing the provider returned some incorrectly formatted records. This was only observed in large collections. The app does not have error checking. Incorrectly formatted records will fail if encountered but the overall app will complete. This will cause the log to show the parent app as failed.

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAndrewBlumhardt%2FLogic-Apps%2Fmain%2Fazuredeploy.json" target="_blank">
    <img src="https://aka.ms/deploytoazurebutton""/>
</a>
<a href="https://portal.azure.us/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAndrewBlumhardt%2FLogic-Apps%2Fmain%2Fazuredeploy.json" target="_blank">
<img src="https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazuregov.png"/>
</a>