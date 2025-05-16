---
title: "Health Dashboard for Direct Routing"
ms.reviewer: nmurav
ms.date: 05/24/2019
ms.author: scottfrancis
author: sfrancis206
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: msteams
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - Tier1
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
description: "Learn how to use Health Dashboard to monitor the connection between your Session Border Controller and Direct Routing."
---

# Health Dashboard for Direct Routing

Health Dashboard for Direct Routing lets you connect a supported Session Border Controller (SBC) to Microsoft Phone System to enable voice calling features. With this dashboard you can add, edit, and view information about your SBCs, voice routes, and PSTN usage records to monitor the connection between your Session Border Controller (SBC) and the Direct Routing interface. The Health Dashboard contains two levels of information to monitor the overall health of connected SBCs as well as detailed information for a given SBC. This information can help to identify issues, including the reason for dropped calls. For example, the SBC might stop sending calls if a certificate on the SBC has expired or if there are network issues. Visit [admin roles](using-admin-roles.md) to manage access to the Health Dashboard.

# View the Health Dashboard for Direct Routing
You can view the Health Dashboard in Teams Admin Center. In the left navigation of the Microsoft Teams Admin Center, click Voice > Direct Routing.

# Overall health

Health Dashboard provides the following information related to overall health of connected SBCs:

 ![Shows Health Dashboard statistics.](media/direct-routing-dashboard-stats1.png)

|Callout |Description  |
|:--------|:-------------|
|**1**   |**Direct Routing Summary** Shows the total number of SBCs, voice routes in the system, and SBCs with issues in the system. <ul><li>**Total SBCs**: The total number of SBCs enrolled in the system, where enrolled means that the tenant administrator added an SBC by using the New-CsOnlinePSTNGateway command.</li><li>**Voice routes**: The total number of voice routes configured in the system.</li><li>**SBCs with issues**: The total number of SBCs with current issues. Issues can include low network effectiveness, certificate expiration, inactivity, no SIP options, and capacity constraints. Note, if an SBC was added in PowerShell, but never connected, the Health Dashboard will show it in an unhealthy status with issues.|
|**2**   |You can click **SBC, SBC test cases, or Voice Routes** to view relevant information in the table. |
|**3**   |**Actions** - Health dashboard lets you add, edit, or delete SBCs, test cases or voice voutes from the system. <ul><li>**Add**: Click to add an FQDN for the SBC from the SBC view, a test suite from the SBC test cases view, or a voice route from the Voice Routes view.</li><li>**Edit**: Select a row in the table and then click Edit to modify parameters for an SBC, test case, or voice route. </li><li>**Delete**: Select a row in the table and then click Delete to remove a given SBC, test case, or voice route from the system. |
|**4**   |The table gives you an overview of Direct Routing Health by SBC, Test Case, or Voice Route. <br><br>**SBCs** <ul><li>**SBC** is the FQDN of the paired SBC.</li><li>**Network effectiveness**(NER) measures the ability of a network to deliver calls by measuring the number of calls sent versus the number of calls delivered to a recipient. The NER measures the ability of networks to deliver calls to the far-end terminal--excluding user actions resulting in call rejections. If the recipient rejected a call or sent the call to voicemail, the call is counted as a successful delivery. This means that an answer message, a busy signal, or a ring with no answer are all considered successful calls. For example, assume Direct Routing sent a call to the SBC and the SBC returns SIP code “504 Server Time-out - The server attempted to access another server in attempting to process the request and didn't receive a prompt response.” This response indicates there's an issue on the SBC side, and this will decrease the NER on the Health Dashboard for this SBC.Because the action you take might depend on the number of calls affected, Health Dashboard shows how many calls were analyzed to calculate a parameter. If the number of calls is less than 100, the NER might be low, but still be normal. The formula used to calculate NER is<br><br> NER = 100 x (Answered calls + User Busy + Ring no Answer + Terminal Reject Seizures)/Total Calls.</li><li>**Average call duration** Average call duration is an indicator of the quality of end user experience. A decrease of the average call duration value often indicates problems with calling experience (noise, glitches, delays, as well as mid-call and other failures). If users experience issues with voice, they can redial the numbers several times or, after a short call, switch to a mobile device. Microsoft recommends establishing a baseline for the average call duration for your company. If this parameter goes significantly below the baseline, it might indicate that your users are having issues with call quality or reliability and are hanging up earlier than usual. If you start seeing extremely low average call duration, for example 15 seconds, callers might be hanging up because your service isn't performing reliably. Because the action you take might depend on the number of calls affected, Health Dashboard shows how many calls were analyzed to calculate a parameter.</li><li>**TLS connectivity status** TLS (Transport Layer Security) connectivity shows the status of the TLS connections between Direct Routing and the SBC. Health Dashboard also analyzes the certificate expiration date and warns if a certificate is set to expire within 30 days so that administrators can renew the certificate before service is disrupted. Click the Warning message for a detailed issue description and recommendations for remediation.</li><li>**SIP Options Status** By default, the SBC sends options messages every minute. This configuration can vary for different SBC vendors. Direct Routing warns if the SIP options aren't sent or aren't configured. For more information about SIP options monitoring, and conditions when an SBC can be marked as not functional, see Monitor and troubleshoot Direct Routing. </li><li>**Concurrent calls capacity** is whether the call was a PSTN outbound or inbound call and the type of call such as a call placed by a user or an audio conference. The calls types you may see include:<br><br>**Enabled**</li></ul><br><li>|
|**5**   |Select **Search for SBCs** to type in a given SBC name. |
|**6**   |Select **Map View** to switch from a table view to a global map view. |
|**7**   |Select **Edit columns** to add or remove columns in the table. |

**Direct Routing summary** Shows the total number of SBCs, voice routes in the system, and SBCs with issues in the system.
-  **Total SBCs**: The total number of SBCs enrolled in the system, where enrolled means that the tenant administrator added an SBC by using the New-CsOnlinePSTNGateway command.
- **Voice routes**: The total number of voice routes configured in the system.
-  **SBCs with issues**: The total number of SBCs with current issues. Issues can include low network effectiveness, certificate expiration, inactivity, no SIP options, and capacity constraints. Note, if an SBC was added in PowerShell, but never connected, the Health Dashboard will show it in an unhealthy status with issues.

- **SBC** - The FQDN of the paired SBC.

- **Network Effectiveness Ratio (NER)** - The NER measures the ability of a network to deliver calls by measuring the number of calls sent versus the number of calls delivered to a recipient.  

   The NER measures the ability of networks to deliver calls to the far-end terminal--excluding user actions resulting in call rejections.  If the recipient rejected a call or sent the call to voicemail, the call is counted as a successful delivery. This means that an answer message, a busy signal, or a ring with no answer are all considered successful calls.
  
   For example, assume Direct Routing sent a call to the SBC and the SBC returns SIP code “504 Server Time-out - The server attempted to access another server in attempting to process the request and didn't receive a prompt response.” This response indicates there's an issue on the SBC side, and this will decrease the NER on the Health Dashboard for this SBC.
  
   Because the action you take might depend on the number of calls affected, Health Dashboard shows how many calls were analyzed to calculate a parameter. If the number of calls is less than 100, the NER might be low, but still be normal.

   The formula used to calculate NER is:

   NER = 100 x (Answered calls + User Busy + Ring no Answer + Terminal Reject Seizures)/Total Calls

- **Average call duration** - Information about average call duration can help you monitor the quality of calls. The average duration of a 1:1 PSTN call is four to five minutes. However, for each company, this average can differ. Microsoft recommends establishing a baseline for the average call duration for your company. If this parameter goes significantly below the baseline, it might indicate that your users are having issues with call quality or reliability and are hanging up earlier than usual. If you start seeing extremely low average call duration, for example 15 seconds, callers might be hanging up because your service isn't performing reliably.

   Because the action you take might depend on the number of calls affected, Health Dashboard shows how many calls were analyzed to calculate a parameter.

- **TLS connectivity status** - TLS (Transport Layer Security) connectivity shows the status of the TLS connections between Direct Routing and the SBC. Health Dashboard also analyzes the certificate expiration date and warns if a certificate is set to expire within 30 days so that administrators can renew the certificate before service is disrupted.

   By clicking the Warning message, you can see a detailed issue description in a popup window on the right and recommendations for how to fix the issue.

- **SIP options status** – By default, the SBC sends options messages every minute. This configuration can vary for different SBC vendors. Direct Routing warns if the SIP options aren't sent or aren't configured. For more information about SIP options monitoring, and conditions when an SBC can be marked as not functional, see [Monitor and troubleshoot Direct Routing](direct-routing-monitor-and-troubleshoot.md).

- **Detailed SIP options status** - In addition to showing that there's an issue with SIP options flow, the Health Dashboard also provides detailed descriptions of the errors. You can access the description by clicking the “Warning” message. A pop-up window on the right shows the detailed error description.

   Possible values for SIP options status messages are as follows:

    - Active – The SBC is active--Microsoft Direct Routing service sees the options flowing on a regular interval.

    - Warning, no SIP options - The Session Border Controller exists in the database (your administrator created it using the command New-CsOnlinePSTNGateway). It's configured to send SIP options, but the Direct Routing service never saw the SIP options coming back from this SBC.

    - Warning, SIP Messages aren't configured - Trunk monitoring using SIP options isn’t turned on. Microsoft Calling System uses SIP options and Transport Layer Security (TLS) handshake monitoring to detect the health of the connected Session Border Controllers (SBCs) at the application level. You’ll have problems if this trunk can be reached at the network level (by ping), but the certificate has expired or the SIP stack doesn’t work. To help identify such problems early, Microsoft recommends enabling sending SIP options. Check your SBC manufacturer documentation to configure sending SIP options.

- **Concurrent calls capacity** - You can specify the limit of concurrent calls that an SBC can handle by using the New- or Set-CsOnlinePSTNGateway command with the -MaxConcurrentSessions parameter. This parameter calculates how many calls were sent or received by Direct Routing using a specific SBC and compares it with the limit set. Note:  If the SBC also handles calls to different PBXs, this number won't show the actual concurrent calls.

## Detailed information for each SBC

You can also view the detailed information for a specific SBC as shown in the following screenshot:

![Health dashboard SBC details.](media/direct-routing-dashboard-SBC-detail1.png)

The detailed view shows the following additional parameters:

- **TLS Connectivity status** – this is the same metric as on the “Overall Health” page;

- **TLS Connectivity last status** – shows time when the SBC made a TLS connection to the Direct Routing service;

- **SIP options status** – the same metric as on the “Overall Health” page.

- **SIP options last checked** – time when the SIP options were received last time.

- **SBC status** – overall status of the SBC, based on all monitored parameters.

- **Concurrent call**- shows  how many concurrent calls the SBC handled. This information is useful to predict the number of concurrent channels you need and see the trend. You can slide the data by number of days and call direction (inbound/outbound/All streams).

- **Network parameters** - All network parameters are measured from the Direct Routing interface to the Session Border Controller. For information about the recommended values, see [Prepare your organization's network for Microsoft Teams](./prepare-network.md), and look at the Customer Edge to Microsoft Edge recommended values.

   - Jitter – Is the millisecond measure of variation in network propagation delay time computed between two endpoints using RTCP (The RTP Control Protocol).

   - Packet Loss – Is a measure of packet that failed to arrive; it's computed between two endpoints.

   - Latency - (Also known as round trip time) is the length of time it takes for a signal to be sent plus the length of time it takes for the acknowledgment of that signal to be received. This time delay consists of the propagation times between the two points of a signal.

   You can slide the data by number of days and call direction (inbound/outbound/All streams).

**Network Effectiveness ratio** - This is the same parameter that appears on the Overall Health dashboard, but with the option to slice the data by time series or call direction.
