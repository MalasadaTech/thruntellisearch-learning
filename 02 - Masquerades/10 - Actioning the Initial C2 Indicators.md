
# 10 - Actioning the Initial C2 Indicators

## Intro

In the last section, we identified an initial C2 domain indicator, and then we performed a pivot on its pattern to identify more C2 domains. In this section, we will use a newly gleaned domain indicator to identify more adversary infrastructure.

## Action the New Indicators

Now that we've got the C2 indicators, we need to action them to identify additional indicators. We will first take the first domain indicator from the results. We will action this as an example. We will search for it in Any Run.

## Actioning C2 in Any Run

Go to the Any Run Reports page. Click the link below to go there directly.

https://app.any.run/submissions# 

For this, let's use `tedbutz.com`. Add a filter for `tedbutz.com` and then run the search.

Observe how the filenames indicate the thractors are using lures for Rufus, Google Meet, and Cisco AnyConnect.

Use this (rufus-4.11.exe):
https://app.any.run/tasks/22fce4b5-4322-4f4a-8344-2bfff302cd5c

## Analyzing the Scheduled Task

We will analyze scheduled task. Review the Any Run submission's Process list. Find the Process with the ID 6840. Click it and you'll see the `Process detail` section show the `Command line` shown below.

```ProcessID-6840

C:\WINDOWS\System32\schtasks.exe /Create /SC MINUTE /MO 18 /TN "EdgeAgentRun" /TR "C:\WINDOWS\System32\rundll32.exe C:\Users\admin\AppData\Roaming\wO0dcIrVDQLM1v5\EdgeAgentRun.dll RTKBootStrv"
```

The simplest explanation is that the command creates a scheduled task to execute `EdgeAgentRun.dll RTKBootStrv` via `rundll32.exe`. Because `rundll32.exe` will execute it, we should check the connections tab to see what `rundll32.exe` connects to.

Check the connections tab. Filter it for `rundll32.exe`. You will see it connects to `185.28.119[.]217`. Unfortunately, it doesn't show the domain associated with that IP. Copy the IP. Click into the DNS tab, and search for the IP. Observe that it is `coretether[.]com`. We will need to add this indicator to the Indicator Table. This C2 is different from the other C2. We will label these C2 domains as `rundll32 C2`. 

## Table Additions

See the additions below that will be applied to the Source Table and the Indicator Table.

| Reference # | Date      | Source       | Title                 | Comments                                                                                  | URL |
| ----------- | --------- | ------------ | --------------------- | ----------------------------------------------------------------------------------------- | --- |
| 17          | 02 JAN 26 | MalasadaTech | 10 - Actioning the C2 | Thruntellisearch section on actioning the Oyster C2 to find new indicators (rundll32 C2). | N/A |

| Indicator # | Source # | Phase Description | Indicator        | Notes                                                   |
| ----------- | -------- | ----------------- | ---------------- | ------------------------------------------------------- |
| 45          | 17       | C2 - rundll32 C2  | coretether[.]com | rundll32 C2 gleaned from section 10 - Actioning the C2. |

## Analyze the GoogleMeet Submission

Next, we'll go back to the Any Run Submissions results for `tedbutz.com` and analyze the next one. It's for `GoogleMeet.exe`. Review the Any Run session here: https://app.any.run/tasks/d9e4d486-c215-4580-99f6-a64865eceec1. Perform the same analysis steps. Check the `Connections` tab and filter for `rundll`. This one is simpler because it shows the `rundll32 C2` domain `registrywave[.]com`.

## Table Additions

See the addition below that will be applied to the Indicator Table.

| Indicator # | Source # | Phase Description | Indicator          | Notes                                                   |
| ----------- | -------- | ----------------- | ------------------ | ------------------------------------------------------- |
| 46          | 17       | C2 - rundll32 C2  | registrywave[.]com | rundll32 C2 gleaned from section 10 - Actioning the C2. |
## Current Tables

See below for the current versions of all the tables.

## Pivot Table

This is the current Pivot Table.

| Pivot # | Description                        | Pivot Platform | Pivot                                                                                                     |
| ------- | ---------------------------------- | -------------- | --------------------------------------------------------------------------------------------------------- |
| 1       | Teams Masqs                        | urlscan        | page.title:"Download Microsoft Teams Desktop and Mobile Apps \| Microsoft Teams" AND filename:"download*" |
| 2       | Dynamic Delivery Domains (apiUrls) | urlscan        | page.title:"dream-me.com"                                                                                 |
| 3       | PuTTy Masqs                        | urlscan        | page.title:"Download PuTTY - a free SSH and telnet client for Windows" AND filename:"download*"           |
| 4       | Oyster C2                          | urlscan        | hash:4176caf548e995285c2f32701426289a0fefc21fd427a4c2c6164282fa04bba0                                     |
## Source Table

This is the current Source Table.

| Reference # | Date      | Source                     | Title                                                                                            | Comments                                                                                        | URL                                                                                                                                 |
| ----------- | --------- | -------------------------- | ------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| 1           | 25 SEP 25 | David Kasabji (@roo7cause) | (Untitled X Post)                                                                                | Initial Lead                                                                                    | https://x.com/roo7cause/status/1971453273862176887                                                                                  |
| 2           | 27 OCT 25 | MalasadaTech               | 01 - Oyster Malware via Teams FakeApp                                                            | Analysis on Reference #1 revealed Dynamic Delivery Mechanism                                    | N/A; Reference the titled training section.                                                                                         |
| 3           | 27 OCT 25 | MalasadaTech               | (Pivot #1 from Pivot Table)                                                                      | Pivot to find additional Teams lures.                                                           | N/A; Pivot #1 from the Pivot Table.                                                                                                 |
| 4           | 27 SEP 25 | Bleeping Computer          | Fake Microsoft Teams installers push Oyster malware via malvertising                             | Bleeping Computer                                                                               | https://www.bleepingcomputer.com/news/security/fake-microsoft-teams-installers-push-oyster-malware-via-malvertising/                |
| 5           | 02 JUL 25 | Arctic Wolf Networks       | Malvertising Campaign Delivers Oyster/Broomstick Backdoor via SEO Poisoning and Trojanized Tools | Includes indicators for PuTTy fake apps. Mentions WinSCP masqs, but doesn't include indicators. | https://arcticwolf.com/resources/blog/malvertising-campaign-delivers-oyster-broomstick-backdoor-via-seo-poisoning-trojanized-tools/ |
| 6           | 26 SEP 25 | blackpoint                 | Malicious Teams Installers Drop Oyster Malware                                                   | Includes indicators for Teams and AnyDesk masqs.                                                | https://blackpointcyber.com/blog/malicious-teams-installers-drop-oyster-malware/                                                    |
| 7           | 17 JUN 25 | Rapid7                     | Malvertising Campaign Leads to Execution of Oyster Backdoor                                      | May be too aged for action, but good for situational awareness.                                 | https://www.rapid7.com/blog/post/2024/06/17/malvertising-campaign-leads-to-execution-of-oyster-backdoor/                            |
| 8           | 06 DEC 25 | MalasadaTech               | 04 - Dynamic Delivery Domain Analysis                                                            | Analysis on the Dynamic Delivery Domains                                                        | N/A; Reference the titled training section.                                                                                         |
| 9           | 07 DEC 25 | MalasadaTech               | (Pivot #2 from Pivot Table)                                                                      | Pivot to find Dynamic Delivery Domains                                                          | N/A; Pivot #2 from the Pivot Table.                                                                                                 |
| 10          | 07 DEC 25 | MalasadaTech               | (Pivot #3 from Pivot Table)                                                                      | Pivot to find PuTTy lures.                                                                      | N/A; Pivot #3 from the Pivot Table.                                                                                                 |
| 11          | 23 AUG 25 | LevelBlue                  | Like PuTTY in Admin’s Hands                                                                      | Analysis on PuTTy lures delivering Oyster                                                       | https://levelblue.com/blogs/security-essentials/like-putty-in-admins-hands                                                          |
| 12          | 07 DEC 25 | MalasadaTech               | 06 - Actioning the AnyDesk Lure Intel                                                            | Thruntellisearch section on AnyDesk lures.                                                      | N/A                                                                                                                                 |
| 13          | 09 DEC 25 | MalasadaTech               | 07 - Using Proofpoint's Suricata Rules                                                           | Thruntellisearch section on using Proofpoint's Suricata Rules in Any Run to find new leads..    | N/A                                                                                                                                 |
| 14          | 09 DEC 25 | MalasadaTech               | 08 - Use Any Run Tag to Identify More Indicators                                                 | Thruntellisearch section on using the Any Run Oyster tag to find new leads.                     | N/A                                                                                                                                 |
| 15          | 09 DEC 25 | MalasadaTech               | 09 - Analyzing the C2                                                                            | Thruntellisearch section on analyzing the Oyster C2 to find new indicators.                     | N/A                                                                                                                                 |
| 16          | 09 DEC 25 | MalasadaTech               | (Pivot #4 from Pivot Table)                                                                      | Pivot to find additional C2 indicators.                                                         | N/A; Pivot #4 from the Pivot Table.                                                                                                 |
| 17          | 02 JAN 26 | MalasadaTech               | 10 - Actioning the C2                                                                            | Thruntellisearch section on actioning the Oyster C2 to find new indicators (rundll32 C2).       | N/A                                                                                                                                 |

## Indicator Table

This is the current Indicator Table. Take note of the updates to the indicators that were previously added just as `C2`. Since we have two types of C2 domains, I renamed the first ones as `C2 - Initial C2` in order to show the distinction between the two.

| Indicator # | Source # | Phase Description                  | Indicator                    | Notes                                                                                |
| ----------- | -------- | ---------------------------------- | ---------------------------- | ------------------------------------------------------------------------------------ |
| 1           | 1, 6     | Delivery - Landing Masq            | teams-install[.]icu          | Initial lead indicator                                                               |
| 2           | 2        | Delivery - Dynamic Delivery Domain | witherspoon-law[.]com        | Gleaned from analysis of Source #1                                                   |
| 3           | 3, 13    | Delivery - Landing Masq            | teams-app[.]bet              | Indicator from pivot #1                                                              |
| 4           | 3        | Delivery - Dynamic Delivery Domain | compaq-computers[.]com       | Gleaned from analysis of Indicator #3                                                |
| 5           | 4, 6     | Delivery - Landing Masq            | teams-install[.]top          |                                                                                      |
| 6           | 5, 11    | Delivery - Landing Masq            | updaterputty[.]com           | Actioned this in section 05 - Actioning the PuTTy Lure Intel                         |
| 7           | 5        | Delivery - Landing Masq            | zephyrhype[.]com             | First glance, unable to determine if it's malicious                                  |
| 8           | 5, 11    | Delivery - Landing Masq            | putty[.]run                  |                                                                                      |
| 9           | 5, 11    | Delivery - Landing Masq            | putty[.]bet                  |                                                                                      |
| 10          | 5, 11    | Delivery - Landing Masq            | puttyy[.]org                 |                                                                                      |
| 11          | 6        | Delivery - Landing Masq            | team[.]frywow[.]com          |                                                                                      |
| 12          | 6        | Delivery - Landing Masq            | anydesksoftware[.]net        | 07 DEC 25: Attempted a pivot. Found a result. Was unable to validate.                |
| 13          | 8        | Delivery - Landing Masq            | winscp[.]id                  | WinSCP-themed lure.                                                                  |
| 14          | 8        | Delivery - Dynamic Delivery Domain | dream-me[.]com               | Gleaned from Pivot #2.                                                               |
| 15          | 8        | Delivery - Dynamic Delivery Domain | msaonl[.]com                 | Gleaned from Pivot #2.                                                               |
| 16          | 8        | Delivery - Dynamic Delivery Domain | ncvalor[.]com                | Gleaned from Pivot #2.                                                               |
| 17          | 8        | Delivery - Dynamic Delivery Domain | newfrontieradvisorsllc[.]com | Gleaned from Pivot #2.                                                               |
| 18          | 8        | Delivery - Dynamic Delivery Domain | newhampshirehomebuyer[.]com  | Gleaned from Pivot #2.                                                               |
| 19          | 9        | Delivery - Dynamic Delivery Domain | doctorreportcard[.]com       | Indicator from pivot #2                                                              |
| 20          | 9        | Delivery - Dynamic Delivery Domain | toshibaaccessories[.]com     | Indicator from pivot #2                                                              |
| 21          | 9        | Delivery - Dynamic Delivery Domain | space-amazons[.]com          | Indicator from pivot #2                                                              |
| 22          | 8, 13    | Delivery - Landing Masq            | notepad-plus-plus[.]run      | Notepad++ themed lure                                                                |
| 23          | 10       | Delivery - Landing Masq            | www-putty[.]com              | PuTTy themed lure from Pivot #3                                                      |
| 24          | 10, 11   | Delivery - Landing Masq            | putty[.]network              | PuTTy themed lure from Pivot #3                                                      |
| 25          | 10       | Delivery - Landing Masq            | putty[.]fyi                  | PuTTy themed lure from Pivot #3                                                      |
| 26          | 11       | Delivery - Landing Masq            | puttysystems[.]com<br>       |                                                                                      |
| 27          | 11       | Delivery - Landing Masq            | puttyy[.]com                 |                                                                                      |
| 28          | 11       | Delivery - Landing Masq            | putty[.]lat                  |                                                                                      |
| 29          | 11       | Delivery - Landing Masq            | putty[.]us[.]com             |                                                                                      |
| 30          | 11       | Delivery - Dynamic Delivery Domain | heartlandenergy[.]ai         |                                                                                      |
| 31          | 11       | Delivery - Dynamic Delivery Domain | ruben.findinit[.]com         |                                                                                      |
| 32          | 11       | Delivery - Dynamic Delivery Domain | ekeitoro.siteinwp[.]com      |                                                                                      |
| 33          | 11       | Delivery - Dynamic Delivery Domain | danielaurel[.]tv             |                                                                                      |
| 34          | 12       | Delivery - Dynamic Delivery Domain | cleancarcatalog[.]com        | Gleaned in section 06 - Actioning the AnyDesk Lure Intel                             |
| 35          | 12       | Delivery - Dynamic Delivery Domain | anydesknow[.]net             | 07 DEC 25 - It is a suspicious masq, but unable to validate that this is related.    |
| 36          | 13       | Delivery - Landing Masq            | cisco-support-software.run   |                                                                                      |
| 37          | 14       | Delivery - Landing Masq            | zoom-install[.]us            | Zoom-themed lure gleaned in section 08 - Use Any Run Tag to Identify More Indicators |
| 38          | 14       | Delivery - Dynamic Delivery Domain | mce-associates[.]com         | Gleaned in section 08 - Use Any Run Tag to Identify More Indicators                  |
| 39          | 15       | C2 - Initial C2                    | lorrieobrien[.]com           | C2 indicator gleaned from section 09 - Analyzing the C2                              |
| 40          | 16       | C2 - Initial C2                    | tedbutz[.]com                | C2 indicator gleaned from Pivot #4.                                                  |
| 41          | 16       | C2 - Initial C2                    | scs-techresources[.]com      | C2 indicator gleaned from Pivot #4.                                                  |
| 42          | 16       | C2 - Initial C2                    | macsimizers[.]com            | C2 indicator gleaned from Pivot #4.                                                  |
| 43          | 16       | C2 - Initial C2                    | pont-express[.]com           | C2 indicator gleaned from Pivot #4.                                                  |
| 44          | 16       | C2 - Initial C2                    | nickbush24[.]com             | C2 indicator gleaned from Pivot #4.                                                  |
| 45          | 17       | C2 - rundll32 C2                   | coretether[.]com             | rundll32 C2 gleaned from section 10 - Actioning the C2.                              |
| 46          | 17       | C2 - rundll32 C2                   | registrywave[.]com           | rundll32 C2 gleaned from section 10 - Actioning the C2.                              |

## Summary

In this section we took action on the initial C2 indicators. Specifically, we filtered the Any Run sessions for the indicator `tedbutz[.]com`. We sampled two file submissions. We identified the scheduled task pattern, and how it schedules a task to use rundll32.exe to execute a function from a DLL file. We took that observation and found that `rundll32.exe` connects to another C2 domain. Because we have two different types of C2, we named them accordingly to show the distinction between the two.