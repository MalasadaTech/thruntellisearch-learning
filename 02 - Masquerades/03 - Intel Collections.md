# 03 - Intel Collections

| [Previous](02%20-%20Types%20of%20Reporting%20Sources.md) | [Home](../links.md) | [Next](04%20-%20Dynamic%20Delivery%20Domains%20(apiUrls).md) |
| :------------------------------------------------------- | :-----------------: | -----------------------------------------------------------: |



In Section `01 - WebInjects`, we introduced the intel lead concept. The examples we used were fairly trivial for analyzing the delivery. We were able to simply take an intel lead from Proofpoint and action it. For large-scale operations like that, it may be simple. Smaller scale thractor campaigns can be more dynamic. That is, the thractors can change their lures more often. When the thractor changes often, or employs multiple lures - for example, you will need a wider intel collection.

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

We are about to begin a journey that may result in many intel sources, and a lot of additional adversary infrastructure. We will need a method to cleanly organize the intel collections. The first thing we'll need to do is create a few tables to store the data. In the first table, the Source Table, will number the sources. This will simplify the other tables, so that you don't have to include the long article URL multiple times. The next table is the Pivot Table. It is similar to a Source Table because we can glean indicators from both tables. The final table is the Indicator Table. You will record the indicators. At first, we'll just focus on the delivery domains, and maybe later we'll dive into the C2 domains. You should include all of the indicators from the start, but for simplicity, we'll action the delivery domain indicators first.

## Source Table

The table below is the Source Table. Note that it includes the existing sources that we would've added if we created this from the start. I like to maintain the sources in the order that I find them. 

Note that Reference #2 refers to the training section "01 - Oyster Malware via Teams FakeApp". We need to add this as a reference because we identified the Dynamic Delivery Mechanism. It was revealed during analysis, and it was not explicitly listed in Reference #1, so it must be its own source. 

Note that Reference #3 refers to the Pivot Table that is listed right below the Source Table.

| Reference # | Date      | Source                     | Title                                                                                            | Comments                                                                                        | URL                                                                                                                                 |
| ----------- | --------- | -------------------------- | ------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| 1           | 25 SEP 25 | David Kasabji (@roo7cause) | (Untitled X Post)                                                                                | Initial Lead                                                                                    | https://x.com/roo7cause/status/1971453273862176887                                                                                  |
| 2           | 27 OCT 25 | MalasadaTech               | 01 - Oyster Malware via Teams FakeApp                                                            | Analysis on Reference #1 revealed Dynamic Delivery Mechanism                                    | N/A; Reference the titled training section.                                                                                         |
| 3           | 27 OCT 25 | MalasadaTech               | (Pivot #1 from Pivot Table)                                                                      | Pivot. Date is the general date for the Thruntellisearch content                                | N/A; Pivot #1 from the Pivot Table.                                                                                                 |
| 4           | 27 SEP 25 | Bleeping Computer          | Fake Microsoft Teams installers push Oyster malware via malvertising                             | Bleeping Computer                                                                               | https://www.bleepingcomputer.com/news/security/fake-microsoft-teams-installers-push-oyster-malware-via-malvertising/                |
| 5           | 02 JUL 25 | Arctic Wolf Networks       | Malvertising Campaign Delivers Oyster/Broomstick Backdoor via SEO Poisoning and Trojanized Tools | Includes indicators for PuTTy fake apps. Mentions WinSCP masqs, but doesn't include indicators. | https://arcticwolf.com/resources/blog/malvertising-campaign-delivers-oyster-broomstick-backdoor-via-seo-poisoning-trojanized-tools/ |
| 6           | 26 SEP 25 | blackpoint                 | Malicious Teams Installers Drop Oyster Malware                                                   | Includes indicators for Teams and AnyDesk masqs.                                                | https://blackpointcyber.com/blog/malicious-teams-installers-drop-oyster-malware/                                                    |
| 7           | 17 JUN 25 | Rapid7                     | Malvertising Campaign Leads to Execution of Oyster Backdoor                                      | May be too aged for action, but good for situational awareness.                                 | https://www.rapid7.com/blog/post/2024/06/17/malvertising-campaign-leads-to-execution-of-oyster-backdoor/                            |

## Pivot Table

Now we need to record the pivots. It will be used as a source, so that it can be referenced.

| Pivot # | Description | Pivot Platform | Pivot                                                                                                     |
| ------- | ----------- | -------------- | --------------------------------------------------------------------------------------------------------- |
| 1       | Teams Masqs | urlscan        | page.title:"Download Microsoft Teams Desktop and Mobile Apps \| Microsoft Teams" AND filename:"download*" |

## Indicator Table

Now that we've got the Source Table, we can create the Indicator Table. It references the source numbers so that we know which intel source the indicator is from. Note that Indicators #1 and #3 have two sources. When you find a source reporting indicators that you already have in the Indicator Table, add the Source # to the existing row. Don't create a duplicate indicator row.
Note that the Phase Description 

| Indicator # | Source # | Phase Description                  | Indicator              | Notes                                               |
| ----------- | -------- | ---------------------------------- | ---------------------- | --------------------------------------------------- |
| 1           | 1, 6     | Delivery - Landing Masq            | teams-install[.]icu    | Initial lead indicator                              |
| 2           | 2        | Delivery - Dynamic Delivery Domain | witherspoon-law[.]com  | Gleaned from analysis of Source #1                  |
| 3           | 3        | Delivery - Landing Masq            | teams-app[.]bet        | Indicator from pivot                                |
| 4           | 3        | Delivery - Dynamic Delivery Domain | compaq-computers[.]com | Gleaned from analysis of Indicator #3               |
| 5           | 4, 6     | Delivery - Landing Masq            | teams-install[.]top    |                                                     |
| 6           | 5        | Delivery - Landing Masq            | updaterputty[.]com     |                                                     |
| 7           | 5        | Delivery - Landing Masq            | zephyrhype[.]com       | First glance, unable to determine if it's malicious |
| 8           | 5        | Delivery - Landing Masq            | putty[.]run            |                                                     |
| 9           | 5        | Delivery - Landing Masq            | putty[.]bet            |                                                     |
| 10          | 5        | Delivery - Landing Masq            | puttyy[.]org           |                                                     |
| 11          | 6        | Delivery - Landing Masq            | team[.]frywow[.]com    |                                                     |
| 12          | 6        | Delivery - Landing Masq            | anydesksoftware[.]net  |                                                     |

## Take Action!

We will continue to take action by analyzing the Dynamic Delivery Domains before moving on to the newly gained intel into the existing knowledge, and use that to continue thruntellisearching. This will continue in Section 04.

| [Previous](02%20-%20Types%20of%20Reporting%20Sources.md) | [Home](../links.md) | [Next](04%20-%20Dynamic%20Delivery%20Domains%20(apiUrls).md) |
| :------------------------------------------------------- | :-----------------: | -----------------------------------------------------------: |


