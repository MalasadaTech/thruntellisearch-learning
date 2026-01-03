# 14 - Revisit Pivot #1

## Intro

Some time has passed since Pivot #1 was initially recorded. Given that we observed new behaviors in Section 13, we should revisit Pivot #1 to show the process.

## The Pivot

Pivot #1 is pasted below. We know that it is outdated because we observed the thractor no longer using the `download*` filename pattern with the `apiUrls`.

`page.title:"Download Microsoft Teams Desktop and Mobile Apps | Microsoft Teams" AND filename:"download*"`

An updated pivot is below. It simply removes the filename part.

`page.title:"Download Microsoft Teams Desktop and Mobile Apps | Microsoft Teams"`

You can view the search here: https://urlscan.io/search/#page.title%3A%22Download%20Microsoft%20Teams%20Desktop%20and%20Mobile%20Apps%20%7C%20Microsoft%20Teams%22.

I see a few new Teams Masqs.

``` New-Teams-Masqs
micro-saft-teams[.]live
teams-support-software[.]run
teams-support-software[.]icu
```

## PAI Reporting on micro-saft-teams[.]live

Previously, I found `micro-saft-teams[.]live` while reviewing the pivot. At the time, I couldn't get it to serve me the malware. I posted about it here: https://x.com/MalasadaTech/status/1998388923203240138. 

Mikhail Kasimov: (https://x.com/500mk500/status/1998395359844786181) referenced @malwrhunterteam's post here: https://x.com/malwrhunterteam/status/1996120025749750060 sharing `microsaft-teams[.]life`. Additionally, Mikhail shared a pivot on the favicon to find more thractor infrastructure here: https://x.com/500mk500/status/1998398735156384026.

@SquiblydooBlog also helped here: https://x.com/SquiblydooBlog/status/1998391116190917013, stating that the domain was serving the Oyster malware the week prior, but at the time of writing it was serving the legitimate MS Teams software.

On a side note: The community is awesome. I think it's cool to be able to get help from folks I haven't met in real live. Thanks!
## Actioning micro-saft-teams[.]live

We can search for the indicator in urlscan here: https://urlscan.io/search/#micro-saft-teams.live. I observe some results are redirecting to Google (as we've previously observed with the other Teams Masqs). I also observe this scan task below was served a file.

https://urlscan.io/result/019b035b-65ac-757d-b343-846194854cb9/

Review the scan task, get the SHA256 hash, and search for it in VT.

You can view it here: https://www.virustotal.com/gui/file/52ab9768aeed9e5e99636cdc61be377566a8489897724228a21cd057f1c65147/details. We can see 0/72 security vendors flagged the file as malicious. We can also see in the `Details` tab that it signed by a legitimate MS cert. This is an example of the legit MS Teams file that @SquiblydooBlog mentioned.

## Actioning teams-support-software[.]icu

We skipped `teams-support-software[.]run` - I couldn't find anything on it other than the fact that it's a masq. Search for `teams-support-software[.]run` in Any Run. I'm using this Submission to analyze: https://app.any.run/tasks/5d9ce76e-a818-459f-833d-a39c30f7f486. The analyst downloaded the malware, but they didn't run it. Go to the `Files` tab, filter for `exe`, and review the details for `C:\Users\admin\Downloads\MSTeamsSetup.exe`. We can see that the SHA256 is `efaae1104c2a532bfaaa2fd11f6345ee321cf0119eeb619526df4f2940795750`.

Take `efaae1104c2a532bfaaa2fd11f6345ee321cf0119eeb619526df4f2940795750` and search for it in VT. You can view it here: https://www.virustotal.com/gui/file/efaae1104c2a532bfaaa2fd11f6345ee321cf0119eeb619526df4f2940795750. This is not tagged as `Oyster`; it is tagged as `ShellcodeRunner`.

Review the Behavior tab here: https://www.virustotal.com/gui/file/efaae1104c2a532bfaaa2fd11f6345ee321cf0119eeb619526df4f2940795750/behavior. Review the `Process Tree` section and observe `PID: 3580` has the known command line: `C:\Windows\System32\schtasks.exe /Create /SC MINUTE /MO 18 /TN EdgeAgentRun /TR C:\Windows\System32\rundll32.exe C:\Users\<USER>\AppData\Roaming\csjmcjXdiFv9vf8\EdgeAgentRun.dll RTKBootStrv`. This confirms this is what we're tracking as Oyster.

## Table Additions

Now that we've got some new indicators, we need to update the tables. See the additions below that will be applied to the Source Table and the Indicator Table. Note that we are adding Pivot #5 as separate from Pivot #1.

| Pivot # | Description | Pivot Platform | Pivot                                                                            |
| ------- | ----------- | -------------- | -------------------------------------------------------------------------------- |
| 5       | Teams Masqs | urlscan        | page.title:"Download Microsoft Teams Desktop and Mobile Apps \| Microsoft Teams" |

| Reference # | Date      | Source            | Title                       | Comments                              | URL                                                      |
| ----------- | --------- | ----------------- | --------------------------- | ------------------------------------- | -------------------------------------------------------- |
| 20          | 02 JAN 26 | MalasadaTech      | (Pivot #5 from Pivot Table) | Pivot to find additional Teams lures. | N/A; Pivot #5 from the Pivot Table.                      |
| 21          | 02 DEC 25 | MalwareHunterTeam | (X Post)                    | X post sharing microsaft-teams[.]life | https://x.com/malwrhunterteam/status/1996120025749750060 |

| Indicator # | Source # | Phase Description       | Indicator                    | Notes                             |
| ----------- | -------- | ----------------------- | ---------------------------- | --------------------------------- |
| 51          | 20       | Delivery - Landing Masq | micro-saft-teams[.]live      | Teams masqs gleaned from Pivot #5 |
| 52          | 20       | Delivery - Landing Masq | teams-support-software[.]run | Teams masqs gleaned from Pivot #5 |
| 53          | 20       | Delivery - Landing Masq | teams-support-software[.]icu | Teams masqs gleaned from Pivot #5 |
| 54          | 21       | Delivery - Landing Masq | microsaft-teams[.]life       | Teams masq shared on X.           |

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
| 5       | Teams Masqs                        | urlscan        | page.title:"Download Microsoft Teams Desktop and Mobile Apps \| Microsoft Teams"                          |
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
| 19          | 02 JAN 26 | MalasadaTech               | 12 - Actioning the rundll32 C2 Indicators                                                        | Section showing how to action the new rundll32 C2 Indicators.                                   | N/A                                                                                                                                 |
| 20          | 02 JAN 26 | MalasadaTech               | (Pivot #5 from Pivot Table)                                                                      | Pivot to find additional Teams lures.                                                           | N/A; Pivot #5 from the Pivot Table.                                                                                                 |
| 21          | 02 DEC 25 | MalwareHunterTeam          | (X Post)                                                                                         | X post sharing microsaft-teams[.]life                                                           | https://x.com/malwrhunterteam/status/1996120025749750060                                                                            |

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
| 49          | 19       | Delivery - Landing Masq            | microsoft-teams[.]bet        | Teams masqs gleaned from actioning the rundll32 C2 Indicators.                       |
| 50          | 19       | Delivery - Landing Masq            | microsoft-teams[.]icu        | Teams masqs gleaned from actioning the rundll32 C2 Indicators.                       |
| 51          | 20       | Delivery - Landing Masq            | micro-saft-teams[.]live      | Teams masqs gleaned from Pivot #5                                                    |
| 52          | 20       | Delivery - Landing Masq            | teams-support-software[.]run | Teams masqs gleaned from Pivot #5                                                    |
| 53          | 20       | Delivery - Landing Masq            | teams-support-software[.]icu | Teams masqs gleaned from Pivot #5                                                    |
| 54          | 21       | Delivery - Landing Masq            | microsaft-teams[.]life       | Teams masq shared on X.                                                              |

## Summary

In this section we revisited Pivot #1. We updated it as Pivot #5. We learned that the thractor is also serving the legitimate Teams file. We increased the indicators by four.