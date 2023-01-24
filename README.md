# AS-Incident-Host-Exposure-Level

Author: Accelerynt

For any technical questions, please contact info@accelerynt.com  

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAccelerynt-Security%2FAS-Incident-Host-Exposure-Level%2Fmain%2Fazuredeploy.json)
[![Deploy to Azure Gov](https://aka.ms/deploytoazuregovbutton)](https://portal.azure.us/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAccelerynt-Security%2FAS-Incident-Host-Exposure-Level%2Fmain%2Fazuredeploy.json)       

This playbook is intended to be run from a Microsoft Sentinel Incident. It will match the Hosts from a Microsoft Sentinel Incident with Microsoft Defender Machines and add each Machine's exposure level as a comment on the Microsoft Sentinel Incident.
                                                                                                                                     
![ExposureLevel_Demo](Images/ExposureLevel_Demo.png)

#
### Deployment                                                                                                         
                                                                                                        
To configure and deploy this playbook:
 
Open your browser and ensure you are logged into your Microsoft Sentinel workspace. In a separate tab, open the link to our playbook on the Accelerynt Security GitHub Repository:

https://github.com/Accelerynt-Security/AS-Incident-Host-Exposure-Level

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAccelerynt-Security%2FAS-Incident-Host-Exposure-Level%2Fmain%2Fazuredeploy.json)
[![Deploy to Azure Gov](https://aka.ms/deploytoazuregovbutton)](https://portal.azure.us/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAccelerynt-Security%2FAS-Incident-Host-Exposure-Level%2Fmain%2Fazuredeploy.json)                                             

Click the “**Deploy to Azure**” button at the bottom and it will bring you to the custom deployment template.

In the **Project Details** section:

* Select the “**Subscription**” and “**Resource Group**” from the dropdown boxes you would like the playbook deployed to.  

In the **Instance Details** section:   

* **Playbook Name**: This can be left as "**AS-Incident-Host-Exposure-Level**" or you may change it.

Towards the bottom, click on “**Review + create**”. 

![ExposureLevel_Deploy_1](Images/ExposureLevel_Deploy_1.png)

Once the resources have validated, click on "**Create**".

![ExposureLevel_Deploy_2](Images/ExposureLevel_Deploy_2.png)

The resources should take around a minute to deploy. Once the deployment is complete, you can expand the "**Deployment details**" section to view them.
Click the one corresponding to the Logic App.

![ExposureLevel_Deploy_3](Images/ExposureLevel_Deploy_3.png)

Click on the “**Edit**” button. This will bring us into the Logic Apps Designer.

![ExposureLevel_Deploy_4](Images/ExposureLevel_Deploy_4.png)

The first and seconds steps labeled "**Connections**" use a shared azuresentinel connection created during the deployment of this playbook. Before the playbook can be run, this connection will either need to be authorized, or an existing authorized connection may be alternatively selected for each.  

![ExposureLevel_Deploy_5](Images/ExposureLevel_Deploy_5.png)

To validate the azuresentinel connection created for this playbook, expand either of the "**Connections**" steps and click the exclamation point icon next to the name matching the playbook.
                                                                                                
![ExposureLevel_Deploy_6](Images/ExposureLevel_Deploy_6.png)

When prompted, sign in to validate the connection.                                                                                                
                                                                                                
![ExposureLevel_Deploy_7](Images/ExposureLevel_Deploy_7.png)                                                                                                                                                                                                                                                   
Since the first two steps share the same connection, there is no need to repeat the process here. Simply refresh the page to ensure the first two steps now have valid connections.

This process will need to be repeated for the two wdatp connections, responsible for communicating with Microsoft Defender. Expand the step labeled "**Condition - Check for Hosts**"

![ExposureLevel_Deploy_8](Images/ExposureLevel_Deploy_8.png)

Repeat the same process above for the connection used in the indicated steps.

![ExposureLevel_Deploy_9](Images/ExposureLevel_Deploy_9.png)

#
### Running the Playbook 

To run this playbook from a Microsoft Sentinel incident, navigate to Microsoft Sentinel:

https://portal.azure.com/#view/HubsExtension/BrowseResource/resourceType/microsoft.securityinsightsarg%2Fsentinel

Select a workspace and then click the "**Incidents**" menu option located under "**Threat management**". Select an incident with compromised host entities.

Click on the "**Action**" list button on the bottom right of the screen and select "**Run playbook**".

![ExposureLevel_Run_1](Images/ExposureLevel_Run_1.png)

From the "**Run playbook on incident**" view, type "**AS-Incident-Host-Exposure-Level**" into the search bar, then click run.

![ExposureLevel_Run_2](Images/ExposureLevel_Run_2.png)
