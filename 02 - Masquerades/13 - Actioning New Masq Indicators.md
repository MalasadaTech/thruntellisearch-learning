# 13 - Actioning New Masq Indicators

## Intro

If you haven't already caught it yet, this whole process is a repetitive loop where you find new indicators, and then take action on those new indicators for even more new indicators. That's what we'll do next. We most recently identified the two indicators listed below. For this part, we'll check for updated behaviors.

``` New-Masq-Indicators

microsoft-teams[.]bet
microsoft-teams[.]icu
```

## Action microsoft-teams[.]bet

First check: https://urlscan.io/search/#microsoft-teams.bet. We observe that there are scan tasks that show the scan was redirected to Google. Take https://urlscan.io/result/019ae00d-a480-710b-8d4f-9922778708c1/ for example. This shows that the thractor is now filtering for unwanted traffic, and unwanted requests are redirected to Google.

Additionally, back in the first urlscan search, we can see there was a scan task for `hxxps[:]//microsoft-teams[.]bet/download/TeamsSetup_v7.852.exe`. This shows that the thractor is hosting the malware on the same domain as the masq landing page. They may not be using `apiUrls` anymore. 

## Action microsoft-teams[.]icu

Let's repeat the steps for the next indicator. Use this: https://urlscan.io/search/#microsoft-teams.icu. We can see that these scan tasks aren't forwarded to Google. We also observe scan tasks for the malware on the masq landing page.

Review this scan task: https://urlscan.io/result/019ac2d5-dbfd-728d-8b0a-32b8f9d7e679/. Check the HTTP Transactions tab here: https://urlscan.io/result/019ac2d5-dbfd-728d-8b0a-32b8f9d7e679/#transactions. I don't observe the download* or market* JS naming patterns. 

Check the response for the base request here: https://urlscan.io/responses/aeef6b0e4c142df36ba5a46868c1dfa5c71b13da810ad6c910a56d865516274f/. Observe that now the `Download` button has a simple HREF link to `href="/files/setupV7.8.exe"`. The thractor is no longer using apiUrls.

Go back to the main urlscan search, and then choose a scan task for the file. I chose this scan task to analyze: https://urlscan.io/result/019ac359-cab7-7618-ac4e-682fa7655329/. Scroll down to the bottom of the result page, and you can see the SHA256 for the downloaded file. Search that in VT and observe that it is malicious.

Review the VT Behavior tab here: https://www.virustotal.com/gui/file/b5f86a350a6ceb3647f6c35dd276986a7cbfd72e97dcffd57311225e092a8126/behavior. Check the `DNS Resolutions` section and observe that it resolves three domains that we're already tracking as malicious: 

``` Already-Identified-Malish-Indicators
coretether[.]com
scs-techresources[.]com
registrywave[.]com
```

## Use VT to Find Matching Process Behaviors

Additionally, scroll down to the `Process Tree` section and observe `PID: 6732` is created with the command line `C:\Windows\System32\schtasks.exe /Create /SC MINUTE /MO 18 /TN "AlphaSecurity" /TR "C:\Windows\System32\rundll32.exe C:\Users\<USER>\AppData\Roaming\i4fXDg5h26t3DBA\AlphaSecurity.dll RTKBootStrv"`. This matches the previously identified scheduled task behavior.

## Summary

In this section, we analyzed the newly discovered Teams Masq indicators. We've identified the thractors are now filtering out unwanted requests and redirecting them to Google in some cases. We also identified the thractors are no longer using the apiUrls, but instead the thractor is hosting the malware on the masq landing page domain.