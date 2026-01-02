# 08 - Use Any Run Tag to Identify More Indicators


In the previous section, we used Proofpoint's Suricata Rules to identify additional adversary infrastructure. In this section, we will use Any Run's Oyster tag to identify more adversary infrastructure. It will be generally short, and we will highlight one instance only.

## Search Oyster Tag in Any Run

Go to the Any Run Reports page. Click the link below to go there directly.

https://app.any.run/submissions# 

Search for the tag "oyster ", and set the Runtype to URL.

At the time of creating this content, the result on the top is for a URL submission to `zoom-install[.]us`. It is linked below.

https://app.any.run/tasks/d4852e06-f90c-485d-a59c-475f58d7d47a

## Verify Known Patterns

Let's see if it uses the download*.js filename or if it's something different. Search for the domain in urlscan. Click the link below to go directly to the search.

https://urlscan.io/search/#zoom-install.us

The link below is the result on the top - at the time of making the content.

https://urlscan.io/result/0199bd10-430a-762f-8b81-c9a6e8026366/

Review the HTTP transactions and check for the filename pattern.

https://urlscan.io/result/0199bd10-430a-762f-8b81-c9a6e8026366/#transactions

Cool! It uses the filename "download-script.js". Click the link below to confirm it has the apiUrls const at the top of the file.

https://urlscan.io/responses/0bb9d0a51afae7eea8fa2a4dbe2f414f013ba862cfe135b4bab0b93880c120ed/

From that, we can observe the additional indicator `mce-associates[.]com`. 

## Table Additions

This is not really a pivot on any patterns. This section demonstrated how to use Any Run tags. Because it is not really pivots, we will use this section as a source, and not a pivot entry.

### Source Table

The part below will be added to the Source Table.

| Reference # | Date      | Source       | Title                                            | Comments                                                                    | URL |
| ----------- | --------- | ------------ | ------------------------------------------------ | --------------------------------------------------------------------------- | --- |
| 14          | 09 DEC 25 | MalasadaTech | 08 - Use Any Run Tag to Identify More Indicators | Thruntellisearch section on using the Any Run Oyster tag to find new leads. | N/A |

### Indicator Table

The part below will be added to the Indicator Table.

| Indicator # | Source # | Phase Description       | Indicator            | Notes                                                                                |
| ----------- | -------- | ----------------------- | -------------------- | ------------------------------------------------------------------------------------ |
| 37          | 14       | Delivery - Landing Masq | zoom-install[.]us    | Zoom-themed lure gleaned in section 08 - Use Any Run Tag to Identify More Indicators |
| 38          | 14       | Dynamic Delivery Domain | mce-associates[.]com | Gleaned in section 08 - Use Any Run Tag to Identify More Indicators                  |

## Update Tables

Now that we've listed the specific parts that need to get added, I'll add them to the current tables.

## Pivot Table

This is the current Pivot Table.

| Pivot # | Description                        | Pivot Platform | Pivot                                                                                                     |
| ------- | ---------------------------------- | -------------- | --------------------------------------------------------------------------------------------------------- |
| 1       | Teams Masqs                        | urlscan        | page.title:"Download Microsoft Teams Desktop and Mobile Apps \| Microsoft Teams" AND filename:"download*" |
| 2       | Dynamic Delivery Domains (apiUrls) | urlscan        | page.title:"dream-me.com"                                                                                 |
| 3       | PuTTy Masqs                        | urlscan        | page.title:"Download PuTTY - a free SSH and telnet client for Windows" AND filename:"download*"           |
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

## Indicator Table

This is the current Indicator Table. 

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
| 34          | 12       | Dynamic Delivery Domain            | cleancarcatalog[.]com        | Gleaned in section 06 - Actioning the AnyDesk Lure Intel                             |
| 35          | 12       | Dynamic Delivery Domain            | anydesknow[.]net             | 07 DEC 25 - It is a suspicious masq, but unable to validate that this is related.    |
| 36          | 13       | Delivery - Landing Masq            | cisco-support-software.run   |                                                                                      |
| 37          | 14       | Delivery - Landing Masq            | zoom-install[.]us            | Zoom-themed lure gleaned in section 08 - Use Any Run Tag to Identify More Indicators |
| 38          | 14       | Dynamic Delivery Domain            | mce-associates[.]com         | Gleaned in section 08 - Use Any Run Tag to Identify More Indicators                  |

## Summary

In this section we use the Oyster tag in Any Run to identify additional indicators. We added the `zoom-install[.]us` masq and the `mce-associates[.]com` dynamic delivery domain.
