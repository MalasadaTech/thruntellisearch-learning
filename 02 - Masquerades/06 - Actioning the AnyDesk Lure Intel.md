# 06 - Actioning the AnyDesk Lure Intel

## Intro
Continuing down the Indicator Table, the next unique indicator to action is Indicator #12 - the AnyDesk lure domain `anydesksoftware[.]net`. See below for the current tables.
  
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

## Check for the Existing Pattern

Search for the domain in urlscan. The link below will take you to the search.

https://urlscan.io/search/#anydesksoftware.net

I chose the oldest scan task. It's the task at the bottom of the list. The link below takes you to the scan result.

https://urlscan.io/result/019a3b54-2446-73b7-8f49-14e82b03004a/

Observe that the page title is `Remote Desktop Software for Windows | AnyDesk`. We will use the page title just like we did with the other pivots. Check the HTTP transactions tab for the download script. The link below takes you to the transactions tab.

https://urlscan.io/result/019a3b54-2446-73b7-8f49-14e82b03004a/#transactions

In the transactions tab, we can see that it matches the download pattern. It is using `download5.js. 

## Extract the Dynamic Delivery Domain

You can view the HTTP response by clicking the "Show response" button, or follow the link below.

https://urlscan.io/responses/fdaee91a7c31a52a38dded4ac752dc224145f8dd60226d127cc28c3d3d02ddde/

In the HTTP response, we can see the script matches the pattern by configuring the apiUrls at the top. It is using the Dynamic Delivery Domain `cleancarcatalog[.]com`. 

## Update Tables

We will need to this section to the source table, and then add the indicator.

We will need to add this following row to the Source Table.

| Reference # | Date      | Source       | Title                                 | Comments                                   | URL |
| ----------- | --------- | ------------ | ------------------------------------- | ------------------------------------------ | --- |
| 12          | 07 DEC 25 | MalasadaTech | 06 - Actioning the AnyDesk Lure Intel | Thruntellisearch section on AnyDesk lures. | N/A |

We will need to add this following row to the Indicator Table.

| Indicator # | Source # | Phase Description       | Indicator             | Notes                                                    |
| ----------- | -------- | ----------------------- | --------------------- | -------------------------------------------------------- |
| 34          | 12       | Dynamic Delivery Domain | cleancarcatalog[.]com | Gleaned in section 06 - Actioning the AnyDesk Lure Intel |

## Perform the Pivot

We can perform the pivot just like the other pivots. The urlscan query is pasted below.

`page.title:"Remote Desktop Software for Windows | AnyDesk" AND filename:"download*"`

You can run that query or click the link below to go straight to it.

https://urlscan.io/search/#page.title%3A%22Remote%20Desktop%20Software%20for%20Windows%20%7C%20AnyDesk%22%20AND%20filename%3A%22download*%22

I don't like how the legitimate AnyDesk domain shows up in the results. I filter them out by adding ` AND NOT anydesk.com` to the end of the query. Here's the new link to the search.

https://urlscan.io/search/#page.title%3A%22Remote%20Desktop%20Software%20for%20Windows%20%7C%20AnyDesk%22%20AND%20filename%3A%22download*%22%20AND%20NOT%20anydesk.com

## Review the Results and Validate

At the time of creating this content, the result for `anydesknow[.]net` is the most recent scan. It is also the only additional domain within the year. The scan result link is pasted below.

https://urlscan.io/result/019a3be7-9db0-73f0-bf46-93daf8e0dc4b/

Review it, then take a look at the HTTP Transactions tab and search for the `download.js` file, and confirm it has the apiUrls at the top of the script. The link below goes to the HTTP Transactions tab.

https://urlscan.io/result/019a3be7-9db0-73f0-bf46-93daf8e0dc4b/#transactions

If you've reviewed the transactions and you can't find it, you're not alone. Without that, we can't confirm it's related. 

## Check for Other Validation Sources

Check Any Run Submissions via the link below. You'll have to add the domain to the search.

https://app.any.run/submissions#

You can check the following unfruitful results.

THREATfox: No results.

https://threatfox.abuse.ch/browse.php?search=ioc%3Aanydesknow.net

VT: Nothing useful.

https://www.virustotal.com/gui/domain/anydesknow.net

Proofpoint: No results.

https://community.emergingthreats.net/search?q=anydesknow%20order%3Alatest

AlienVault: Nothing useful.

https://otx.alienvault.com/indicator/domain/anydesknow.net

## Why Did We Spend Time On This?

Why do we have this section, if our efforts don't produce results? In every section, as far as I can recall, it's been all wins. We go over something, and I show the results that work. I show the patterns that I've already found. I show the pivots that I've already confirmed worked. As I'm thruntellisearching for this content, there's a lot of stuff that I filter out for simplicity. As I, and I'm sure this applies to everyone else, thruntellisearch for stuff - not everything is an win. Behind every post, there could be many hours researching other stuff that didn't result in anything fruitful. A lot of time is just spent trying new things. This is a long-winded paragraph to say we will add the indicator to the Indicator Table, but we will add a note that states we couldn't validate this is related.

## Add the Indicators

The row below will need to be added to the Indicator Table.

| Indicator # | Source # | Phase Description       | Indicator        | Notes                                                |
| ----------- | -------- | ----------------------- | ---------------- | ---------------------------------------------------- |
| 35          | 12       | Dynamic Delivery Domain | anydesknow[.]net | 07 DEC 25 - Unable to validate that this is related. |

## Current Tables

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

## Indicator Table

This is the current Indicator Table. Note that I've added a note for Indicator #12 stating that I couldn't validate the pivot.

| Indicator # | Source # | Phase Description                  | Indicator                    | Notes                                                                             |
| ----------- | -------- | ---------------------------------- | ---------------------------- | --------------------------------------------------------------------------------- |
| 1           | 1, 6     | Delivery - Landing Masq            | teams-install[.]icu          | Initial lead indicator                                                            |
| 2           | 2        | Delivery - Dynamic Delivery Domain | witherspoon-law[.]com        | Gleaned from analysis of Source #1                                                |
| 3           | 3        | Delivery - Landing Masq            | teams-app[.]bet              | Indicator from pivot #1                                                           |
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
| 22          | 8        | Delivery - Landing Masq            | notepad-plus-plus[.]run      | Notepad++ themed lure                                                             |
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

## Summary

This was an unsuccessful pivot. We were unable to identify any other additional indicators. We added the indicator to the Indicator Table. We added a note stating we were unable to validate it as related. We will continue thruntellisearching.