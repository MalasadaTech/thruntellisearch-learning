# 05 - Actioning the PuTTy Lure Intel

Actioning the PuTTy lures.

## Taking Action

In this section, we will take action on the additional indicators. From the last section, we started the table below. We haven't actioned Indicator #5. We will skip it since we've already actioned the Teams lure theme. This section will cover the PuTTy-themed lures. See below for the current tables.

## Pivot Table

This is the current Pivot Table.

| Pivot # | Description                        | Pivot Platform | Pivot                                                                                                     |
| ------- | ---------------------------------- | -------------- | --------------------------------------------------------------------------------------------------------- |
| 1       | Teams Masqs                        | urlscan        | page.title:"Download Microsoft Teams Desktop and Mobile Apps \| Microsoft Teams" AND filename:"download*" |
| 2       | Dynamic Delivery Domains (apiUrls) | urlscan        | page.title:"dream-me.com"                                                                                 |
## Update the Source Table

This is the current Source Table.

| Reference # | Date      | Source                     | Title                                                                                            | Comments                                                                                        | URL                                                                                                                                 |
| ----------- | --------- | -------------------------- | ------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| 1           | 25 SEP 25 | David Kasabji (@roo7cause) | (Untitled X Post)                                                                                | Initial Lead                                                                                    | https://x.com/roo7cause/status/1971453273862176887                                                                                  |
| 2           | 27 OCT 25 | MalasadaTech               | 01 - Oyster Malware via Teams FakeApp                                                            | Analysis on Reference #1 revealed Dynamic Delivery Mechanism                                    | N/A; Reference the titled training section.                                                                                         |
| 3           | 27 OCT 25 | MalasadaTech               | (Pivot #1 from Pivot Table)                                                                      | Pivot. Date is the general date for the Thruntellisearch content                                | N/A; Pivot #1 from the Pivot Table.                                                                                                 |
| 4           | 27 SEP 25 | Bleeping Computer          | Fake Microsoft Teams installers push Oyster malware via malvertising                             | Bleeping Computer                                                                               | https://www.bleepingcomputer.com/news/security/fake-microsoft-teams-installers-push-oyster-malware-via-malvertising/                |
| 5           | 02 JUL 25 | Arctic Wolf Networks       | Malvertising Campaign Delivers Oyster/Broomstick Backdoor via SEO Poisoning and Trojanized Tools | Includes indicators for PuTTy fake apps. Mentions WinSCP masqs, but doesn't include indicators. | https://arcticwolf.com/resources/blog/malvertising-campaign-delivers-oyster-broomstick-backdoor-via-seo-poisoning-trojanized-tools/ |
| 6           | 26 SEP 25 | blackpoint                 | Malicious Teams Installers Drop Oyster Malware                                                   | Includes indicators for Teams and AnyDesk masqs.                                                | https://blackpointcyber.com/blog/malicious-teams-installers-drop-oyster-malware/                                                    |
| 7           | 17 JUN 25 | Rapid7                     | Malvertising Campaign Leads to Execution of Oyster Backdoor                                      | May be too aged for action, but good for situational awareness.                                 | https://www.rapid7.com/blog/post/2024/06/17/malvertising-campaign-leads-to-execution-of-oyster-backdoor/                            |
| 8           | 06 DEC 25 | MalasadaTech               | 04 - Dynamic Delivery Domain Analysis                                                            | Analysis on the Dynamic Delivery Domains                                                        | N/A; Reference the titled training section.                                                                                         |
| 9           | 07 DEC 25 | MalasadaTech               | (Pivot #2 from Pivot Table)                                                                      | Pivot. Date is the general date for the Thruntellisearch content                                | N/A; Pivot #2 from the Pivot Table.                                                                                                 |

## Indicator Table

This is the current Indicator Table.

| Indicator # | Source # | Phase Description                  | Indicator                    | Notes                                               |
| ----------- | -------- | ---------------------------------- | ---------------------------- | --------------------------------------------------- |
| 1           | 1, 6     | Delivery - Landing Masq            | teams-install[.]icu          | Initial lead indicator                              |
| 2           | 2        | Delivery - Dynamic Delivery Domain | witherspoon-law[.]com        | Gleaned from analysis of Source #1                  |
| 3           | 3        | Delivery - Landing Masq            | teams-app[.]bet              | Indicator from pivot #1                             |
| 4           | 3        | Delivery - Dynamic Delivery Domain | compaq-computers[.]com       | Gleaned from analysis of Indicator #3               |
| 5           | 4, 6     | Delivery - Landing Masq            | teams-install[.]top          |                                                     |
| 6           | 5        | Delivery - Landing Masq            | updaterputty[.]com           |                                                     |
| 7           | 5        | Delivery - Landing Masq            | zephyrhype[.]com             | First glance, unable to determine if it's malicious |
| 8           | 5        | Delivery - Landing Masq            | putty[.]run                  |                                                     |
| 9           | 5        | Delivery - Landing Masq            | putty[.]bet                  |                                                     |
| 10          | 5        | Delivery - Landing Masq            | puttyy[.]org                 |                                                     |
| 11          | 6        | Delivery - Landing Masq            | team[.]frywow[.]com          |                                                     |
| 12          | 6        | Delivery - Landing Masq            | anydesksoftware[.]net        |                                                     |
| 13          | 8        | Delivery - Landing Masq            | winscp[.]id                  | WinSCP-themed lure.                                 |
| 14          | 8        | Delivery - Dynamic Delivery Domain | dream-me[.]com               |                                                     |
| 15          | 8        | Delivery - Dynamic Delivery Domain | msaonl[.]com                 |                                                     |
| 16          | 8        | Delivery - Dynamic Delivery Domain | ncvalor[.]com                |                                                     |
| 17          | 8        | Delivery - Dynamic Delivery Domain | newfrontieradvisorsllc[.]com |                                                     |
| 18          | 8        | Delivery - Dynamic Delivery Domain | newhampshirehomebuyer[.]com  |                                                     |
| 19          | 9        | Delivery - Dynamic Delivery Domain | doctorreportcard[.]com       | Indicator from pivot #2                             |
| 20          | 9        | Delivery - Dynamic Delivery Domain | toshibaaccessories[.]com     | Indicator from pivot #2                             |
| 21          | 9        | Delivery - Dynamic Delivery Domain | space-amazons[.]com          | Indicator from pivot #2                             |
| 22          | 8        | Delivery - Landing Masq            | notepad-plus-plus[.]run      | Notepad++ themed lure                               |

We will first take action on Indicator #6 - updaterputty[.]com. We will start by searching for it in urlscan.

https://urlscan.io/search/#updaterputty.com%20

(SNIP)

Let's select and analyze the oldest good scan result:

https://urlscan.io/result/0197359b-4487-73b8-be74-3f60435cf6ec/

(SNIP)

Observe the page title is: "_Download PuTTY - a free SSH and telnet client for Windows_". Recall the first query from "02 - 01 - Oyster Malware via Teams FakeApp" is below:

page.title:"Download Microsoft Teams Desktop and Mobile Apps | Microsoft Teams" AND filename:"download*"

In the query above, we have the part that specifies it must contain a file that starts with "download". The section below discusses the previously observed pattern with the download-script##.js file.

## Unique Property that was Previously Identified

The unique property that is different in this kit is the file that follows the pattern download-script##.js where the # symbol is a random number that is optional. It contains the code for the next step in the delivery. We can use this to specifically search for this kit.

## Apply a Filter to use the Previously-Identified Pattern

Since we are looking for a putty themed lure, that is likely from the same thractor, we can modify the existing query with the newly observed putty lure page title as shown below.

page.title:"Download PuTTY - a free SSH and telnet client for Windows" AND filename:"download*"

Here's a link to the query:

https://urlscan.io/search/#page.title%3A%22Download%20PuTTY%20-%20a%20free%20SSH%20and%20telnet%20client%20for%20Windows%22%20AND%20filename%3A%22download*%22

(SNIP)

Here's the first result (at the time of creating the content):

https://urlscan.io/result/019926e9-b246-7488-a36c-da7f5c6f130e/

Go to the HTTP transactions tab, and then look for the file that matches download-script*. Compare the download script file structure. It also contains the apiUrls. We have a confirmed match. That is our internal validation.

(SNIP)
## External Validation

For external validation, we can check Proofpoint.

The link below will take you to the search. Follow the link below, and we can see that it was published in v11014.

https://community.emergingthreats.net/search?q=www-putty%20order%3Alatest

(SNIP)

## Update the Pivot and Source Tables

Now that we've validated the new pivot works, we must add it to the Pivot Table, and then add the pivot to the Source Table so that it can be referenced in the Indicator Table. The Source and Indicator Tables are becoming too long. Instead of pasting the entire tables every time from now on, I will just have the current tables at the beginning. As we add to them, I will only show the rows that should be added. Then, at the end, I will show the current tables with the additions incorporated to them.

Add the following row to the Pivot Table:

| Pivot # | Description | Pivot Platform | Pivot                                                                                           |
| ------- | ----------- | -------------- | ----------------------------------------------------------------------------------------------- |
| 3       | PuTTy Masqs | urlscan        | page.title:"Download PuTTY - a free SSH and telnet client for Windows" AND filename:"download*" |

Add the following row to the Source Table.

| Reference # | Date      | Source       | Title                       | Comments                   | URL                                 |
| ----------- | --------- | ------------ | --------------------------- | -------------------------- | ----------------------------------- |
| 10          | 07 DEC 25 | MalasadaTech | (Pivot #3 from Pivot Table) | Pivot to find PuTTy lures. | N/A; Pivot #3 from the Pivot Table. |

## Add the Additional Indicators from the Pivot

We validated the indicator www-putty[.]com. The two indicators listed below were also gleaned from this pivot. I've included the links to the VT comments for your validation.

putty[.]network
https://urlscan.io/result/0198a8d0-d8a6-72bb-a4b9-d486e6ff7f1f/

https://www.virustotal.com/gui/domain/putty.network/community

putty[.]fyi
https://urlscan.io/result/01988c23-51b6-7744-9a9e-8a36d857d778/

https://www.virustotal.com/gui/domain/putty.fyi/community

Here are the rows that we need to add to the indicator table.

| Indicator # | Source # | Phase Description       | Indicator       | Notes                           |
| ----------- | -------- | ----------------------- | --------------- | ------------------------------- |
| 23          | 10       | Delivery - Landing Masq | www-putty[.]com | PuTTy themed lure from Pivot #3 |
| 24          | 10       | Delivery - Landing Masq | putty[.]network | PuTTy themed lure from Pivot #3 |
| 25          | 10       | Delivery - Landing Masq | putty[.]fyi     | PuTTy themed lure from Pivot #3 |
## Additional Lead

I skipped over it in the previous part above because I didn't want to interrupt the flow as we went down the rabbit hole. We're done with the Pivot #3 stuff, so we can continue to the next related thing. 

In the VT Community tab for putty[.]network (https://www.virustotal.com/gui/domain/putty.network/community), there is a comment from "rectifyq" showing that it was listed in the following LevelBlue report.

https://levelblue.com/blogs/security-essentials/like-putty-in-admins-hands

This research activity has shown itself to be complicated. The thractor uses many different lure themes. I don't think I've been doing this, so I wanted to highlight this process so that you understand you should be doing this. As we thruntellisearch, you may find more indicators that are referenced in additional reporting. Each time you find a new report, you should ingest it. As such, here is the additional source that should be added to the Source Table. 


| Reference # | Date      | Source    | Title                       | Comments                                  | URL                                                                        |
| ----------- | --------- | --------- | --------------------------- | ----------------------------------------- | -------------------------------------------------------------------------- |
| 11          | 23 AUG 25 | LevelBlue | Like PuTTY in Admin’s Hands | Analysis on PuTTy lures delivering Oyster | https://levelblue.com/blogs/security-essentials/like-putty-in-admins-hands |

I put the additional indicator rows that need to get added. Take a moment to observe how some indicators were already listed in the Indicator Table. We will merge them to the existing table at the end of the section. For the indicators that already exist, we will just add the Source # to the existing indicator row in the Indicator Table.

| Indicator # | Source # | Phase Description                  | Indicator               | Notes |
| ----------- | -------- | ---------------------------------- | ----------------------- | ----- |
| 26          | 11       | Delivery - Landing Masq            | puttyy[.]org            |       |
| 27          | 11       | Delivery - Landing Masq            | puttysystems[.]com<br>  |       |
| 28          | 11       | Delivery - Landing Masq            | updaterputty[.]com      |       |
| 29          | 11       | Delivery - Landing Masq            | putty[.]bet             |       |
| 30          | 11       | Delivery - Landing Masq            | puttyy[.]com            |       |
| 31          | 11       | Delivery - Landing Masq            | putty[.]run             |       |
| 32          | 11       | Delivery - Landing Masq            | putty[.]lat             |       |
| 33          | 11       | Delivery - Landing Masq            | putty[.]us[.]com        |       |
| 34          | 11       | Delivery - Landing Masq            | putty[.]network         |       |
| 35          | 11       | Delivery - Dynamic Delivery Domain | heartlandenergy[.]ai    |       |
| 36          | 11       | Delivery - Dynamic Delivery Domain | ruben.findinit[.]com    |       |
| 37          | 11       | Delivery - Dynamic Delivery Domain | ekeitoro.siteinwp[.]com |       |
| 38          | 11       | Delivery - Dynamic Delivery Domain | danielaurel[.]tv        |       |

## Final Section Table Merges

The tables below show the tables after the merges from this section.

## Pivot Table

This is the current Pivot Table.

| Pivot # | Description                        | Pivot Platform | Pivot                                                                                                     |
| ------- | ---------------------------------- | -------------- | --------------------------------------------------------------------------------------------------------- |
| 1       | Teams Masqs                        | urlscan        | page.title:"Download Microsoft Teams Desktop and Mobile Apps \| Microsoft Teams" AND filename:"download*" |
| 2       | Dynamic Delivery Domains (apiUrls) | urlscan        | page.title:"dream-me.com"                                                                                 |
| 3       | PuTTy Masqs                        | urlscan        | page.title:"Download PuTTY - a free SSH and telnet client for Windows" AND filename:"download*"           |
## Update the Source Table

This is the current Source Table. Note that I've updated the comments on the pivot rows so that it clearly states what the pivot is about.

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

## Indicator Table

This is the current Indicator Table.

| Indicator # | Source # | Phase Description                  | Indicator                    | Notes                                                        |
| ----------- | -------- | ---------------------------------- | ---------------------------- | ------------------------------------------------------------ |
| 1           | 1, 6     | Delivery - Landing Masq            | teams-install[.]icu          | Initial lead indicator                                       |
| 2           | 2        | Delivery - Dynamic Delivery Domain | witherspoon-law[.]com        | Gleaned from analysis of Source #1                           |
| 3           | 3        | Delivery - Landing Masq            | teams-app[.]bet              | Indicator from pivot #1                                      |
| 4           | 3        | Delivery - Dynamic Delivery Domain | compaq-computers[.]com       | Gleaned from analysis of Indicator #3                        |
| 5           | 4, 6     | Delivery - Landing Masq            | teams-install[.]top          |                                                              |
| 6           | 5, 11    | Delivery - Landing Masq            | updaterputty[.]com           | Actioned this in section 05 - Actioning the PuTTy Lure Intel |
| 7           | 5        | Delivery - Landing Masq            | zephyrhype[.]com             | First glance, unable to determine if it's malicious          |
| 8           | 5, 11    | Delivery - Landing Masq            | putty[.]run                  |                                                              |
| 9           | 5, 11    | Delivery - Landing Masq            | putty[.]bet                  |                                                              |
| 10          | 5, 11    | Delivery - Landing Masq            | puttyy[.]org                 |                                                              |
| 11          | 6        | Delivery - Landing Masq            | team[.]frywow[.]com          |                                                              |
| 12          | 6        | Delivery - Landing Masq            | anydesksoftware[.]net        |                                                              |
| 13          | 8        | Delivery - Landing Masq            | winscp[.]id                  | WinSCP-themed lure.                                          |
| 14          | 8        | Delivery - Dynamic Delivery Domain | dream-me[.]com               | Gleaned from Pivot #2.                                       |
| 15          | 8        | Delivery - Dynamic Delivery Domain | msaonl[.]com                 | Gleaned from Pivot #2.                                       |
| 16          | 8        | Delivery - Dynamic Delivery Domain | ncvalor[.]com                | Gleaned from Pivot #2.                                       |
| 17          | 8        | Delivery - Dynamic Delivery Domain | newfrontieradvisorsllc[.]com | Gleaned from Pivot #2.                                       |
| 18          | 8        | Delivery - Dynamic Delivery Domain | newhampshirehomebuyer[.]com  | Gleaned from Pivot #2.                                       |
| 19          | 9        | Delivery - Dynamic Delivery Domain | doctorreportcard[.]com       | Indicator from pivot #2                                      |
| 20          | 9        | Delivery - Dynamic Delivery Domain | toshibaaccessories[.]com     | Indicator from pivot #2                                      |
| 21          | 9        | Delivery - Dynamic Delivery Domain | space-amazons[.]com          | Indicator from pivot #2                                      |
| 22          | 8        | Delivery - Landing Masq            | notepad-plus-plus[.]run      | Notepad++ themed lure                                        |
| 23          | 10       | Delivery - Landing Masq            | www-putty[.]com              | PuTTy themed lure from Pivot #3                              |
| 24          | 10, 11   | Delivery - Landing Masq            | putty[.]network              | PuTTy themed lure from Pivot #3                              |
| 25          | 10       | Delivery - Landing Masq            | putty[.]fyi                  | PuTTy themed lure from Pivot #3                              |
| 26          | 11       | Delivery - Landing Masq            | puttysystems[.]com<br>       |                                                              |
| 27          | 11       | Delivery - Landing Masq            | puttyy[.]com                 |                                                              |
| 28          | 11       | Delivery - Landing Masq            | putty[.]lat                  |                                                              |
| 29          | 11       | Delivery - Landing Masq            | putty[.]us[.]com             |                                                              |
| 30          | 11       | Delivery - Dynamic Delivery Domain | heartlandenergy[.]ai         |                                                              |
| 31          | 11       | Delivery - Dynamic Delivery Domain | ruben.findinit[.]com         |                                                              |
| 32          | 11       | Delivery - Dynamic Delivery Domain | ekeitoro.siteinwp[.]com      |                                                              |
| 33          | 11       | Delivery - Dynamic Delivery Domain | danielaurel[.]tv             |                                                              |

## Summary

We have successfully identified additional lures. The thractor is also using PuTTy lures. We continued actioning indicators in this ongoing cycle.





