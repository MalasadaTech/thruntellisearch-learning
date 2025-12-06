# 03 - Intel Collections

In section 01 - WebInjects, we introduced the intel lead concept. The examples we used were fairly trivial for analyzing the delivery. We were able to simply take an intel lead from Proofpoint and action it. For large-scale operations like that, it may be simple. Smaller scale thractor campaigns can be more dynamic. That is, the thractors can change their lures more often. When the thractor changes often, or employs multiple lures - for example, you will need a wider intel collection.

## Intel Collections Concept

Generally, to perform intel collections, you will repeat a set of steps in cycles. We've done some parts of it already. It first starts with an intel lead. From there, we identify patterns to find additional adversary infrastructure. We would then need to search publicly available information (PAI) for reporting on those indicators. We would repeat the step for any newly observed reporting. As we continue through the cycles, we would combine all the insights gleaned from the reporting we ingest. In a sense, we would become an aggregator.

## Taking Action

To continue the intel collections process, we will use the sources below that Bleeping Computer referenced. 

 https://arcticwolf.com/resources/blog/malvertising-campaign-delivers-oyster-broomstick-backdoor-via-seo-poisoning-trojanized-tools/
 
https://blackpointcyber.com/blog/malicious-teams-installers-drop-oyster-malware/

https://www.rapid7.com/blog/post/2024/06/17/malvertising-campaign-leads-to-execution-of-oyster-backdoor/

## Collections Topic

The Arctic Wolf report discusses PuTTy lures. Because the sources aren't limited to the Teams lure, we need to change our topic. In intel collections, the topic is the main thing that you want to collect intel on. It can be a specific campaign, a malware, or a specific threat actor. At this point, I think it'll be a good idea to change the topic to "Malvertising Fake Apps to Deliver Oyster Malware". With this topic, it'll cover the other Fake Apps too.
## Organization

We are about to begin a journey that may result in many intel sources, and a lot of additional adversary infrastructure. We will need a method to cleanly organize the intel collections. The first thing we'll need to do is create a few tables to store the data. In the first table, the sources table, will number the sources. This will simplify the other tables, so that you don't have to include the long article URL multiple times. The next table will include the indicators. You will record the indicators. At first, we'll just focus on the delivery domains, and maybe later we'll dive into the C2 domains. You should include all of the indicators from the start, but for simplicity, we'll action the delivery domain indicators first. 

## Source Table

The table below is the source table. 

| Reference # | Date      | Source               | Title                                                                                            | Comments                                                                                        | URL                                                                                                                                 |
| ----------- | --------- | -------------------- | ------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| 1           | 02 JUL 25 | Arctic Wolf Networks | Malvertising Campaign Delivers Oyster/Broomstick Backdoor via SEO Poisoning and Trojanized Tools | Includes indicators for PuTTy fake apps. Mentions WinSCP masqs, but doesn't include indicators. | https://arcticwolf.com/resources/blog/malvertising-campaign-delivers-oyster-broomstick-backdoor-via-seo-poisoning-trojanized-tools/ |
| 2           | 26 SEP 25 | blackpoint           | Malicious Teams Installers Drop Oyster Malware                                                   | Includes indicators for Teams and AnyDesk masqs.                                                | https://blackpointcyber.com/blog/malicious-teams-installers-drop-oyster-malware/                                                    |
| 3           | 17 JUN 25 | Rapid7               | Malvertising Campaign Leads to Execution of Oyster Backdoor                                      | May be too aged for action, but good for situational awareness.                                 | https://www.rapid7.com/blog/post/2024/06/17/malvertising-campaign-leads-to-execution-of-oyster-backdoor/                            |

## Indicator Table

Now that we've got the source table, we can create the indicator table, that references the source numbers so that we know which intel source the indicator is from.

| Indicator # | Source # | Phase Description       | Indicator             | Notes                                               |
| ----------- | -------- | ----------------------- | --------------------- | --------------------------------------------------- |
| 1           | 1        | Delivery - Landing Masq | updaterputty[.]com    |                                                     |
| 2           | 1        | Delivery - Landing Masq | zephyrhype[.]com      | First glance, unable to determine if it's malicious |
| 3           | 1        | Delivery - Landing Masq | putty[.]run           |                                                     |
| 4           | 1        | Delivery - Landing Masq | putty[.]bet           |                                                     |
| 5           | 1        | Delivery - Landing Masq | puttyy[.]org          |                                                     |
| 6           | 2        | Delivery - Landing Masq | team[.]frywow[.]com   |                                                     |
| 7           | 2        | Delivery - Landing Masq | teams-install[.]icu   |                                                     |
| 8           | 2        | Delivery - Landing Masq | teams-install[.]top   |                                                     |
| 9           | 2        | Delivery - Landing Masq | anydesksoftware[.]net |                                                     |

## PIVOT TABLE

Now we need to record the pivots. It will be used as a source, so that it can be referenced.

| Pivot # | Description | Pivot Platform | Pivot                                                                                                     |
| ------- | ----------- | -------------- | --------------------------------------------------------------------------------------------------------- |
| 1       | Teams Masqs | urlscan        | page.title:"Download Microsoft Teams Desktop and Mobile Apps \| Microsoft Teams" AND filename:"download*" |

## Updated Source Table

Now that we've recorded the pivot. We need to update the source table to include the pivot as a source. See below for the new reference - Reference #4.

| Reference # | Date      | Source               | Title                                                                                            | Comments                                                                                        | URL                                                                                                                                 |
| ----------- | --------- | -------------------- | ------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| 1           | 02 JUL 25 | Arctic Wolf Networks | Malvertising Campaign Delivers Oyster/Broomstick Backdoor via SEO Poisoning and Trojanized Tools | Includes indicators for putty fake apps. Mentions WinSCP masqs, but doesn't include indicators. | https://arcticwolf.com/resources/blog/malvertising-campaign-delivers-oyster-broomstick-backdoor-via-seo-poisoning-trojanized-tools/ |
| 2           | 26 SEP 25 | blackpoint           | Malicious Teams Installers Drop Oyster Malware                                                   | Includes indicators for Teams and AnyDesk masqs.                                                | https://blackpointcyber.com/blog/malicious-teams-installers-drop-oyster-malware/                                                    |
| 3           | 17 JUN 25 | Rapid7               | Malvertising Campaign Leads to Execution of Oyster Backdoor                                      | May be too aged for action, but good for situational awareness.                                 | https://www.rapid7.com/blog/post/2024/06/17/malvertising-campaign-leads-to-execution-of-oyster-backdoor/                            |
| 4           | 30 NOV 25 | Pivot                | Teams Pivot                                                                                      | Results from a urlscan pivot.                                                                   | Pivot table - pivot #1.                                                                                                             |

(UPDATE THE INDICATOR TABLE!)
## Updated Indicator Table


(BEFORE CONTINUING, MAKE SURE TO ADD THE INITIAL LEAD, AND THEN THE PROOFPOINT SOURCE)

## Take Action!

We will take action on the newly gained intel into the existing knowledge, and use that to continue thruntellisearching. This will continue in section 04.


