## 07 - Use Proofpoint's Suricata Rules

## Intro

Before moving forward, I wanted to inject a new method of Thruntellisearching.
So far, we've used an x post as an intel lead. Then, we used Grok as an external validation, but we also used one of the validation sources as an intel lead (Source #4). From that intel lead in section 05 - Actioning the PuTTy Lure Intel, we used Proofpoint as an external validation. This led me to an idea. I've used it before in other Thruntellisearching activities, and it applies to this activity.

## Find the Checkin Rule

Often times, Proofpoint will have "Checkin" rule. We want that rule.

Search Proofpoint for "oyster". Use the link below to go to the search.

https://community.emergingthreats.net/search?q=oyster%20order%3Alatest

It just so happens, the most recent (at the time of writing) Oyster-related ruleset has the Checkin rules. The link below goes to the Ruleset Summary Update.

https://community.emergingthreats.net/t/ruleset-update-summary-2025-10-03-v11031/3073

Review the Suricata rules listed below.

- 2065047 - ET MALWARE Oyster Backdoor CnC Checkin M5 (malware.rules)
- 2065048 - ET MALWARE Oyster Backdoor CnC Checkin M6 (malware.rules)

We can use this. The Suricata IDs (SIDs) are 2065047 and 2065048. Take those and search app.any.run/submissions. You will need to paste the SID in the "Suricata SID" field.

The most recent submission is here: https://app.any.run/tasks/9f3574bc-9bbf-423d-a052-86ae19778125. by the filename, we can glean they are using a Rufus-themed lure. We might be able to use that later.

Select the filter icon. Click the Runtype dropdown, and then select URL.

We can see the submission for the url cisco-support-software[.]run. Click the link in your search, or you can click the link below to go to the session.

https://app.any.run/tasks/85c7e2d1-abe5-4ab4-8552-c448ffc66979

We see it masquerades as a Cisco AnyConnect-themed lure.

Search for it in urlscan. You can use the link below to go directly to the search. 

https://urlscan.io/search/#cisco-support-software.run

Take the most recent scan task with a 200 response. I've pasted the link below for the scan task that I'm using. 

https://urlscan.io/result/019a97eb-bc86-733a-8038-06f5589ebc9a/

Analyze the responses for pattern matches.

https://urlscan.io/result/019a97eb-bc86-733a-8038-06f5589ebc9a/#transactions

It has market12.js instead of download*.js. View the response linked below.

https://urlscan.io/responses/67d6082327e5e9f056da5fd60495a4f542e602f6bd53e2496e6635e7bea98aaf/

We observe a change in the thractor behavior. Instead of using the download*.js filename pattern, they are using market*.js. With this newly observed behavior, we should revisit Pivot #1 to check if it's changed.

## Table Additions

We will now need to make updates to the tables! View the updates listed below.

| Reference # | Date      | Source       | Title                                  | Comments                                                                                     | URL |
| ----------- | --------- | ------------ | -------------------------------------- | -------------------------------------------------------------------------------------------- | --- |
| 13          | 09 DEC 25 | MalasadaTech | 07 - Using Proofpoint's Suricata Rules | Thruntellisearch section on using Proofpoint's Suricata Rules in Any Run to find new leads.. | N/A |

| Indicator # | Source # | Phase Description       | Indicator                  | Notes |
| ----------- | -------- | ----------------------- | -------------------------- | ----- |
| 36          | 13       | Delivery - Landing Masq | cisco-support-software.run |       |
| 37          | 13       | Delivery - Landing Masq | notepad-plus-plus.run      |       |
| 38          | 13       | Delivery - Landing Masq | teams-app.bet              |       |

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

## Indicator Table

This is the current Indicator Table. Note that I've merged in two indicators by adding the Source #13 to the existing indicators.

| Indicator # | Source # | Phase Description                  | Indicator                    | Notes                                                                             |
| ----------- | -------- | ---------------------------------- | ---------------------------- | --------------------------------------------------------------------------------- |
| 1           | 1, 6     | Delivery - Landing Masq            | teams-install[.]icu          | Initial lead indicator                                                            |
| 2           | 2        | Delivery - Dynamic Delivery Domain | witherspoon-law[.]com        | Gleaned from analysis of Source #1                                                |
| 3           | 3, 13    | Delivery - Landing Masq            | teams-app[.]bet              | Indicator from pivot #1                                                           |
| 4           | 3        | Delivery - Dynamic Delivery Domain | compaq-computers[.]com       | Gleaned from analysis of Indicator #3                                             |
| 5           | 4, 6     | Delivery - Landing Masq            | teams-install[.]top          |                                                                                   |
| 6           | 5, 11    | Delivery - Landing Masq            | updaterputty[.]com           | Actioned this in section 05 - Actioning the PuTTy Lure Intel                      |
| 7           | 5        | Delivery - Landing Masq            | zephyrhype[.]com             | First glance, unable to determine if it's malicious                               |
| 8           | 5, 11    | Delivery - Landing Masq            | putty[.]run                  |                                                                                   |
| 9           | 5, 11    | Delivery - Landing Masq            | putty[.]bet                  |                                                                                   |
| 10          | 5, 11    | Delivery - Landing Masq            | puttyy[.]org                 |                                                                                   |
| 11          | 6        | Delivery - Landing Masq            | team[.]frywow[.]com          |                                                                                   |
| 12          | 6        | Delivery - Landing Masq            | anydesksoftware[.]net        | 07 DEC 25: Attempted a pivot. Found a result. Was unable to validate.             |
| 13          | 8        | Delivery - Landing Masq            | winscp[.]id                  | WinSCP-themed lure.                                                               |
| 14          | 8        | Delivery - Dynamic Delivery Domain | dream-me[.]com               | Gleaned from Pivot #2.                                                            |
| 15          | 8        | Delivery - Dynamic Delivery Domain | msaonl[.]com                 | Gleaned from Pivot #2.                                                            |
| 16          | 8        | Delivery - Dynamic Delivery Domain | ncvalor[.]com                | Gleaned from Pivot #2.                                                            |
| 17          | 8        | Delivery - Dynamic Delivery Domain | newfrontieradvisorsllc[.]com | Gleaned from Pivot #2.                                                            |
| 18          | 8        | Delivery - Dynamic Delivery Domain | newhampshirehomebuyer[.]com  | Gleaned from Pivot #2.                                                            |
| 19          | 9        | Delivery - Dynamic Delivery Domain | doctorreportcard[.]com       | Indicator from pivot #2                                                           |
| 20          | 9        | Delivery - Dynamic Delivery Domain | toshibaaccessories[.]com     | Indicator from pivot #2                                                           |
| 21          | 9        | Delivery - Dynamic Delivery Domain | space-amazons[.]com          | Indicator from pivot #2                                                           |
| 22          | 8, 13    | Delivery - Landing Masq            | notepad-plus-plus[.]run      | Notepad++ themed lure                                                             |
| 23          | 10       | Delivery - Landing Masq            | www-putty[.]com              | PuTTy themed lure from Pivot #3                                                   |
| 24          | 10, 11   | Delivery - Landing Masq            | putty[.]network              | PuTTy themed lure from Pivot #3                                                   |
| 25          | 10       | Delivery - Landing Masq            | putty[.]fyi                  | PuTTy themed lure from Pivot #3                                                   |
| 26          | 11       | Delivery - Landing Masq            | puttysystems[.]com<br>       |                                                                                   |
| 27          | 11       | Delivery - Landing Masq            | puttyy[.]com                 |                                                                                   |
| 28          | 11       | Delivery - Landing Masq            | putty[.]lat                  |                                                                                   |
| 29          | 11       | Delivery - Landing Masq            | putty[.]us[.]com             |                                                                                   |
| 30          | 11       | Delivery - Dynamic Delivery Domain | heartlandenergy[.]ai         |                                                                                   |
| 31          | 11       | Delivery - Dynamic Delivery Domain | ruben.findinit[.]com         |                                                                                   |
| 32          | 11       | Delivery - Dynamic Delivery Domain | ekeitoro.siteinwp[.]com      |                                                                                   |
| 33          | 11       | Delivery - Dynamic Delivery Domain | danielaurel[.]tv             |                                                                                   |
| 34          | 12       | Dynamic Delivery Domain            | cleancarcatalog[.]com        | Gleaned in section 06 - Actioning the AnyDesk Lure Intel                          |
| 35          | 12       | Dynamic Delivery Domain            | anydesknow[.]net             | 07 DEC 25 - It is a suspicious masq, but unable to validate that this is related. |
| 36          | 13       | Delivery - Landing Masq            | cisco-support-software.run   |                                                                                   |

## Summary

In this activity, we took the Proofpoint Checkin Suricata rules, and we searched for Any Run submissions that had hits on that rule. We observed there were hits for URL and file submissions. We updated our tables.









