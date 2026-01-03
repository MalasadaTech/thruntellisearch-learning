# 11 - Using AI to Enrich Indicators

## Intro

This will be a quick section. I don't think I've done any external validation in this Masquerades section group. You can perform a similar function, but instead of searching to validate your findings, you will be searching to enrich your findings.

## The Problem and Solution

When you initially begin your intel collections, you might not find everything. If you want to be thorough, you should enrich each indicator. That is - you should search for additional reports that includes any new indicators you find first-hand.

One way would be to use a search engine and search for the new indicator. AI is the rage nowadays, so we'll use that. I used Grok, but you can use any AI you'd like as long as it is able to search the internet (and you should experiment with multiple AI sources so that you find the one you like).

## The Prompt

I've pasted a quick prompt. I specify that I don't want a report on Oyster malware campaigns because I don't want to wait for it to tell me something I'm already tracking. Next, I specific that I want it to list the sources and include the published date, URL, report title, and a short summary. See below.

``` AI-Prompt

Find me cyber threat intel reports on tedbutz[.]com. It is a C2 domain for Oyster malware. Specifically, I don't want generic intel on recent oyster malware campaigns - I want cyber threat intel sources that lists tedbutz[.]com in the report's IOC section. I want the list of sources to only include the publish date, URL, report title, and a VERY succinct summary of the report.
```

## The Result

You can view the result via the link below.

https://grok.com/c/a7c66db7-1e88-4c6d-a9a7-1ad3cf86a8b2?rid=2d84a789-c5ea-4aad-9483-9dc316c8f5db

You could try this urlscan task below if the link above doesn't work.

https://urlscan.io/result/019b8164-b41c-756f-9e02-07f696a308f9/

You can view the first result below. Review the content, and make a note of the indicators listed at the end.

``` Example-Result

Publish Date: December 8, 2025 
URL:https://www.cyberproof.com/blog/oyster-backdoor-resurfaces-analyzing-the-latest-seo-poisoning-attacks/Report 
Title: Oyster Backdoor 
Resurfaces: Analyzing the Latest SEO Poisoning Attacks 
Summary: Details resurgence of Oyster backdoor via SEO poisoning and malvertising since mid-November 2025, using fake installers to drop persistent DLL, with new infrastructure and ransomware ties.
```


## Table Additions

Now that we've got some new indicators, we need to update the tables. See the additions below that will be applied to the Source Table and the Indicator Table.

| Reference # | Date      | Source                   | Title                                                                  | Comments                          | URL                                                                                                                      |
| ----------- | --------- | ------------------------ | ---------------------------------------------------------------------- | --------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| 18          | 02 JAN 26 | CyberProof Research Team | Oyster Backdoor Resurfaces: Analyzing the Latest SEO Poisoning Attacks | CTI discussing Google Meets Lure. | https://www.cyberproof.com/blog/oyster-backdoor-resurfaces-analyzing-the-latest-seo-poisoning-attacks/?referrer=grok.com |

| Indicator # | Source # | Phase Description       | Indicator             | Notes                                                     |
| ----------- | -------- | ----------------------- | --------------------- | --------------------------------------------------------- |
| 40          | 16, 18   | C2 - Initial C2         | tedbutz[.]com         | C2 indicator gleaned from Pivot #4., and also CyberProof. |
| 47          | 18       | C2 - rundll32 C2        | nucleusgate[.]com     | Gleaned from CyberProof.                                  |
| 48          | 18       | Delivery - Landing Masq | google-meet-app[.]icu | Google Meet lure gleaned from CyberProof.                 |

## Rinse and Repeat

You **could** repeat this step for each indicator you find. I just wanted to briefly discuss it. If I did it for each indicator, the tables would probably become insanely large. It would be too large for training-sake.

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
| 18          | 02 JAN 26 | CyberProof Research Team   | Oyster Backdoor Resurfaces: Analyzing the Latest SEO Poisoning Attacks                           | CTI discussing Google Meets Lure.                                                               | https://www.cyberproof.com/blog/oyster-backdoor-resurfaces-analyzing-the-latest-seo-poisoning-attacks/?referrer=grok.com            |

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
| 34          | 12       | Delivery - Dynamic Delivery Domain | cleancarcatalog[.]com        | Gleaned in section 06 - Actioning the AnyDesk Lure Intel                             |
| 35          | 12       | Delivery - Dynamic Delivery Domain | anydesknow[.]net             | 07 DEC 25 - It is a suspicious masq, but unable to validate that this is related.    |
| 36          | 13       | Delivery - Landing Masq            | cisco-support-software.run   |                                                                                      |
| 37          | 14       | Delivery - Landing Masq            | zoom-install[.]us            | Zoom-themed lure gleaned in section 08 - Use Any Run Tag to Identify More Indicators |
| 38          | 14       | Delivery - Dynamic Delivery Domain | mce-associates[.]com         | Gleaned in section 08 - Use Any Run Tag to Identify More Indicators                  |
| 39          | 15       | C2 - Initial C2                    | lorrieobrien[.]com           | C2 indicator gleaned from section 09 - Analyzing the C2                              |
| 40          | 16, 18   | C2 - Initial C2                    | tedbutz[.]com                | C2 indicator gleaned from Pivot #4., and also CyberProof.                            |
| 41          | 16       | C2 - Initial C2                    | scs-techresources[.]com      | C2 indicator gleaned from Pivot #4.                                                  |
| 42          | 16       | C2 - Initial C2                    | macsimizers[.]com            | C2 indicator gleaned from Pivot #4.                                                  |
| 43          | 16       | C2 - Initial C2                    | pont-express[.]com           | C2 indicator gleaned from Pivot #4.                                                  |
| 44          | 16       | C2 - Initial C2                    | nickbush24[.]com             | C2 indicator gleaned from Pivot #4.                                                  |
| 45          | 17       | C2 - rundll32 C2                   | coretether[.]com             | rundll32 C2 gleaned from section 10 - Actioning the C2.                              |
| 46          | 17       | C2 - rundll32 C2                   | registrywave[.]com           | rundll32 C2 gleaned from section 10 - Actioning the C2.                              |
| 47          | 18       | C2 - rundll32 C2                   | nucleusgate[.]com            | Gleaned from CyberProof.                                                             |
| 48          | 18       | Delivery - Landing Masq            | google-meet-app[.]icu        | Google Meet lure gleaned from CyberProof.                                            |

## Summary

This was a quick section to show how AI can be used to enrich the indicators. As you find indicators, you should run an AI prompt to find additional CTI reports that include the indicator you just found.
