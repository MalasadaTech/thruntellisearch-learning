# 15 - Favicon Pivots

## Intro

Favicon pivots are a common way to find additional adversary infrastructure. This section will dive into favicon pivots. We've been using the page title as the pivot (for the most part). Mikhail Kasimov shared a pivot on the favicon to find more thractor infrastructure here: https://x.com/500mk500/status/1998398735156384026. We will riff off of that and go exploring.

## Intel Lead

We will record Mikhail's post as the intel lead. Here's the Source Table row that will be added to the table.

| Reference # | Date      | Source                      | Title             | Comments           | URL                                               |
| ----------- | --------- | --------------------------- | ----------------- | ------------------ | ------------------------------------------------- |
| 22          | 09 DEC 25 | Mikhail Kasimov (@500mk500) | (Untitled X Post) | Favicon Pivot Lead | https://x.com/500mk500/status/1998398735156384026 |

## Work the Pivot

The hash that Mikhail provided appears to be an MD5, but we need the SHA256 for urlscan. We can get the SHA256. First, search urlscan for the lead domain `micro-saft-teams.live`. Here's the link: https://urlscan.io/search/#micro-saft-teams.live. 

Next, find a result that includes the `favicon.ico` resource. I'm using this result: https://urlscan.io/result/019aff95-6b44-77a8-97f5-ac9716bdea54/. Navigate to the `HTTP Transactions` tab. Scroll to the bottom where the `favicon.ico` request/response is. Click the magnifying glass to show the SHA256 is `e816ebd88b51b59af1f733f74d471476dbe163335ee06f6d46eddbf667b40318`. You can click the SHA256 link to view the search link here: https://urlscan.io/search/#hash%3Ae816ebd88b51b59af1f733f74d471476dbe163335ee06f6d46eddbf667b40318.

I've reviewed the results and I observe this appears to be a fairly high-fidelity pivot. It should be recorded.

## Record the Pivot

The rows below will be added to the tables.

| Pivot # | Description | Pivot Platform | Pivot                                                                 |
| ------- | ----------- | -------------- | --------------------------------------------------------------------- |
| 6       | Teams Masqs | urlscan        | hash:e816ebd88b51b59af1f733f74d471476dbe163335ee06f6d46eddbf667b40318 |

| Reference # | Date      | Source                        | Title                       | Comments                                                   | URL                                 |
| ----------- | --------- | ----------------------------- | --------------------------- | ---------------------------------------------------------- | ----------------------------------- |
| 23          | 03 JAN 26 | Mikhail Kasimov, MalasadaTech | (Pivot #6 from Pivot Table) | This is a urlscan adaptation from Mikhail Kasimov's pivot. | N/A; Pivot #6 from the Pivot Table. |

## Repeat the Process

You should repeat the process for each `Delivery - Landing Masq` indicator. We will repeat the process for a Google Meets masq, `google-meet-app[.]icu`, as an example. This will be an opportunity to show a non-standard implementation of the favicon.

## Analyze the Masq

Access the masq in urlscan. Search for the domain. You should be able to search urlscan by now, so I will not include a link. Find a successful result. I'm using this one: https://urlscan.io/result/019aa6b3-8529-7010-b668-6ea329f7f853/. Go to the `HTTP Transactions` tab, and `CTRL + F` `favicon`. You will not find it. 

Find the `Primary Request` at the top of the `HTTP Transactions` page. Click the `Show response` button. It will take you here: https://urlscan.io/responses/7127a82a1b75cca3e790e7c3c8b46b2318149a984fdeb3df9199c37925c3dece/. `CTRL + F` search for `shortcut`. You will see the line pasted below.

`<link href="./googleg_gradient_standard_20dp.png" rel="shortcut icon" type="image/png">`

The shortcut icon is normally saved as `favicon.ico`, but it doesn't need to be. In this example, we can see that it is saved as `googleg_gradient_standard_20dp.png`. Return to the `HTTP Transactions` page. Find the `googleg_gradient_standard_20dp.png` file. Extract the SHA256 hash. Search for it in urlscan. You should be very familiar with this process, so I will not provide instructions. You should be here: https://urlscan.io/search/#hash%3A8657bd13763477ea9d924f71b889634fd0d7abb51417d0628be34202ccd17b69

## Refine the Pivot

At the time of writing this, there are many false positives that are legitimate Google sites. We need to filter out the sites below.

```Legit-Google-Sites-to-Filter-Out

myaccount.google.com
workspace.google.com
support.google.com
www.google.com
```

We will take the base pivot, `hash:8657bd13763477ea9d924f71b889634fd0d7abb51417d0628be34202ccd17b69`, and add the filter ` AND NOT page.domain:("myaccount.google.com" OR "workspace.google.com" OR "support.google.com" OR "www.google.com")`. Before applying the filter, there are 8,570 results. After running the combined query there are 127 results. This is much better. 

Some results are not related. For example, https://urlscan.io/result/019b66b7-925c-745f-a38c-6e94d8461d14/ is a phishing result to phish for the Google confirmation code. That's cool to find, and we should keep this query to monitor for other threats, but we should continue refining for this activity. In order to focus on Google Meet masqs, we should add a filter so that the results must have `meet` in the page title. We need to add ` AND page.title:meet` to the query. This is the current query: `hash:8657bd13763477ea9d924f71b889634fd0d7abb51417d0628be34202ccd17b69 AND NOT page.domain:("myaccount.google.com" OR "workspace.google.com" OR "support.google.com" OR "www.google.com") AND page.title:meet`. Here's the link to the search: https://urlscan.io/search/#hash%3A8657bd13763477ea9d924f71b889634fd0d7abb51417d0628be34202ccd17b69%20AND%20NOT%20page.domain%3A(%22myaccount.google.com%22%20OR%20%22workspace.google.com%22%20OR%20%22support.google.com%22%20OR%20%22www.google.com%22)%20AND%20page.title%3Ameet. At the time of writing, we are now down to 22 results. 

The current query does include false positives. For example, https://urlscan.io/result/019b44ac-1bac-708b-92eb-c73d3fb51e5f/ is for the ClickFix site `meet.giooga[.]com`. It is unrelated, so we should continue refining. Review the page title for the ClickFix page and the others. Spot the difference. The results we're after also include the word `Workspace`. We need to add a filter so that the results contain this word. We need to modify the page title filter to this: ` AND page.title:(meet AND workspace)`. See the current query below.

`hash:8657bd13763477ea9d924f71b889634fd0d7abb51417d0628be34202ccd17b69 AND NOT page.domain:("myaccount.google.com" OR "workspace.google.com" OR "support.google.com" OR "www.google.com") AND page.title:(meet AND workspace)`

Here is the link to the query. 

https://urlscan.io/search/#hash%3A8657bd13763477ea9d924f71b889634fd0d7abb51417d0628be34202ccd17b69%20AND%20NOT%20page.domain%3A(%22myaccount.google.com%22%20OR%20%22workspace.google.com%22%20OR%20%22support.google.com%22%20OR%20%22www.google.com%22)%20AND%20page.title%3A(meet%20AND%20workspace). 

At the time of writing, we are now down to 14 results, and the results all appear to be related. I've pasted the adversary infrastructure below.

``` Adversary-Infrastructure-From-This-Pivot

google-meet-install[.]xyz
google-meet-install[.]icu
google-meet-app[.]run
google-meet-app[.]icu
```

## Update the Tables

The following updates will be added.

| Pivot # | Description       | Pivot Platform | Pivot                                                                                                                                                                                                                        |
| ------- | ----------------- | -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 7       | Google Meet Masqs | urlscan        | hash:8657bd13763477ea9d924f71b889634fd0d7abb51417d0628be34202ccd17b69 AND NOT page.domain:("myaccount.google.com" OR "workspace.google.com" OR "support.google.com" OR "www.google.com") AND page.title:(meet AND workspace) |

| Reference # | Date      | Source       | Title                       | Comments                                       | URL                                 |
| ----------- | --------- | ------------ | --------------------------- | ---------------------------------------------- | ----------------------------------- |
| 24          | 03 JAN 26 | MalasadaTech | (Pivot #7 from Pivot Table) | This is a urlscan pivot for Google Meet masqs. | N/A; Pivot #7 from the Pivot Table. |

| Indicator # | Source # | Phase Description       | Indicator                 | Notes                                                                |
| ----------- | -------- | ----------------------- | ------------------------- | -------------------------------------------------------------------- |
| 55          | 24       | Delivery - Landing Masq | google-meet-install[.]xyz | Google Meet masq gleaned from Pivot #7.                              |
| 56          | 24       | Delivery - Landing Masq | google-meet-install[.]icu | Google Meet masq gleaned from Pivot #7.                              |
| 57          | 24       | Delivery - Landing Masq | google-meet-app[.]run     | Google Meet masq gleaned from Pivot #7.                              |
| 48          | 18, 24   | Delivery - Landing Masq | google-meet-app[.]icu     | Google Meet lure gleaned from CyberProof, and gleaned from Pivot #7. |

## Current Tables

See below for the current versions of all the tables.

## Pivot Table

This is the current Pivot Table.

| Pivot # | Description                        | Pivot Platform | Pivot                                                                                                                                                                                                                        |
| ------- | ---------------------------------- | -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | Teams Masqs                        | urlscan        | page.title:"Download Microsoft Teams Desktop and Mobile Apps \| Microsoft Teams" AND filename:"download*"                                                                                                                    |
| 2       | Dynamic Delivery Domains (apiUrls) | urlscan        | page.title:"dream-me.com"                                                                                                                                                                                                    |
| 3       | PuTTy Masqs                        | urlscan        | page.title:"Download PuTTY - a free SSH and telnet client for Windows" AND filename:"download*"                                                                                                                              |
| 4       | Oyster C2                          | urlscan        | hash:4176caf548e995285c2f32701426289a0fefc21fd427a4c2c6164282fa04bba0                                                                                                                                                        |
| 5       | Teams Masqs                        | urlscan        | page.title:"Download Microsoft Teams Desktop and Mobile Apps \| Microsoft Teams"                                                                                                                                             |
| 6       | Teams Masqs                        | urlscan        | hash:e816ebd88b51b59af1f733f74d471476dbe163335ee06f6d46eddbf667b40318                                                                                                                                                        |
| 7       | Google Meet Masqs                  | urlscan        | hash:8657bd13763477ea9d924f71b889634fd0d7abb51417d0628be34202ccd17b69 AND NOT page.domain:("myaccount.google.com" OR "workspace.google.com" OR "support.google.com" OR "www.google.com") AND page.title:(meet AND workspace) |
## Source Table

This is the current Source Table.

| Reference # | Date      | Source                        | Title                                                                                            | Comments                                                                                        | URL                                                                                                                                 |
| ----------- | --------- | ----------------------------- | ------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| 1           | 25 SEP 25 | David Kasabji (@roo7cause)    | (Untitled X Post)                                                                                | Initial Lead                                                                                    | https://x.com/roo7cause/status/1971453273862176887                                                                                  |
| 2           | 27 OCT 25 | MalasadaTech                  | 01 - Oyster Malware via Teams FakeApp                                                            | Analysis on Reference #1 revealed Dynamic Delivery Mechanism                                    | N/A; Reference the titled training section.                                                                                         |
| 3           | 27 OCT 25 | MalasadaTech                  | (Pivot #1 from Pivot Table)                                                                      | Pivot to find additional Teams lures.                                                           | N/A; Pivot #1 from the Pivot Table.                                                                                                 |
| 4           | 27 SEP 25 | Bleeping Computer             | Fake Microsoft Teams installers push Oyster malware via malvertising                             | Bleeping Computer                                                                               | https://www.bleepingcomputer.com/news/security/fake-microsoft-teams-installers-push-oyster-malware-via-malvertising/                |
| 5           | 02 JUL 25 | Arctic Wolf Networks          | Malvertising Campaign Delivers Oyster/Broomstick Backdoor via SEO Poisoning and Trojanized Tools | Includes indicators for PuTTy fake apps. Mentions WinSCP masqs, but doesn't include indicators. | https://arcticwolf.com/resources/blog/malvertising-campaign-delivers-oyster-broomstick-backdoor-via-seo-poisoning-trojanized-tools/ |
| 6           | 26 SEP 25 | blackpoint                    | Malicious Teams Installers Drop Oyster Malware                                                   | Includes indicators for Teams and AnyDesk masqs.                                                | https://blackpointcyber.com/blog/malicious-teams-installers-drop-oyster-malware/                                                    |
| 7           | 17 JUN 25 | Rapid7                        | Malvertising Campaign Leads to Execution of Oyster Backdoor                                      | May be too aged for action, but good for situational awareness.                                 | https://www.rapid7.com/blog/post/2024/06/17/malvertising-campaign-leads-to-execution-of-oyster-backdoor/                            |
| 8           | 06 DEC 25 | MalasadaTech                  | 04 - Dynamic Delivery Domain Analysis                                                            | Analysis on the Dynamic Delivery Domains                                                        | N/A; Reference the titled training section.                                                                                         |
| 9           | 07 DEC 25 | MalasadaTech                  | (Pivot #2 from Pivot Table)                                                                      | Pivot to find Dynamic Delivery Domains                                                          | N/A; Pivot #2 from the Pivot Table.                                                                                                 |
| 10          | 07 DEC 25 | MalasadaTech                  | (Pivot #3 from Pivot Table)                                                                      | Pivot to find PuTTy lures.                                                                      | N/A; Pivot #3 from the Pivot Table.                                                                                                 |
| 11          | 23 AUG 25 | LevelBlue                     | Like PuTTY in Admin’s Hands                                                                      | Analysis on PuTTy lures delivering Oyster                                                       | https://levelblue.com/blogs/security-essentials/like-putty-in-admins-hands                                                          |
| 12          | 07 DEC 25 | MalasadaTech                  | 06 - Actioning the AnyDesk Lure Intel                                                            | Thruntellisearch section on AnyDesk lures.                                                      | N/A                                                                                                                                 |
| 13          | 09 DEC 25 | MalasadaTech                  | 07 - Using Proofpoint's Suricata Rules                                                           | Thruntellisearch section on using Proofpoint's Suricata Rules in Any Run to find new leads..    | N/A                                                                                                                                 |
| 14          | 09 DEC 25 | MalasadaTech                  | 08 - Use Any Run Tag to Identify More Indicators                                                 | Thruntellisearch section on using the Any Run Oyster tag to find new leads.                     | N/A                                                                                                                                 |
| 15          | 09 DEC 25 | MalasadaTech                  | 09 - Analyzing the C2                                                                            | Thruntellisearch section on analyzing the Oyster C2 to find new indicators.                     | N/A                                                                                                                                 |
| 16          | 09 DEC 25 | MalasadaTech                  | (Pivot #4 from Pivot Table)                                                                      | Pivot to find additional C2 indicators.                                                         | N/A; Pivot #4 from the Pivot Table.                                                                                                 |
| 17          | 02 JAN 26 | MalasadaTech                  | 10 - Actioning the C2                                                                            | Thruntellisearch section on actioning the Oyster C2 to find new indicators (rundll32 C2).       | N/A                                                                                                                                 |
| 18          | 02 JAN 26 | CyberProof Research Team      | Oyster Backdoor Resurfaces: Analyzing the Latest SEO Poisoning Attacks                           | CTI discussing Google Meets Lure.                                                               | https://www.cyberproof.com/blog/oyster-backdoor-resurfaces-analyzing-the-latest-seo-poisoning-attacks/?referrer=grok.com            |
| 19          | 02 JAN 26 | MalasadaTech                  | 12 - Actioning the rundll32 C2 Indicators                                                        | Section showing how to action the new rundll32 C2 Indicators.                                   | N/A                                                                                                                                 |
| 20          | 02 JAN 26 | MalasadaTech                  | (Pivot #5 from Pivot Table)                                                                      | Pivot to find additional Teams lures.                                                           | N/A; Pivot #5 from the Pivot Table.                                                                                                 |
| 21          | 02 DEC 25 | MalwareHunterTeam             | (X Post)                                                                                         | X post sharing microsaft-teams[.]life                                                           | https://x.com/malwrhunterteam/status/1996120025749750060                                                                            |
| 22          | 09 DEC 25 | Mikhail Kasimov (@500mk500)   | (Untitled X Post)                                                                                | Favicon Pivot Lead                                                                              | https://x.com/500mk500/status/1998398735156384026                                                                                   |
| 23          | 03 JAN 26 | Mikhail Kasimov, MalasadaTech | (Pivot #6 from Pivot Table)                                                                      | This is a urlscan adaptation from Mikhail Kasimov's pivot.                                      | N/A; Pivot #6 from the Pivot Table.                                                                                                 |
| 24          | 03 JAN 26 | MalasadaTech                  | (Pivot #7 from Pivot Table)                                                                      | This is a urlscan pivot for Google Meet masqs.                                                  | N/A; Pivot #7 from the Pivot Table.                                                                                                 |

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
| 48          | 18, 24   | Delivery - Landing Masq            | google-meet-app[.]icu        | Google Meet lure gleaned from CyberProof, and gleaned from Pivot #7.                 |
| 49          | 19       | Delivery - Landing Masq            | microsoft-teams[.]bet        | Teams masqs gleaned from actioning the rundll32 C2 Indicators.                       |
| 50          | 19       | Delivery - Landing Masq            | microsoft-teams[.]icu        | Teams masqs gleaned from actioning the rundll32 C2 Indicators.                       |
| 51          | 20       | Delivery - Landing Masq            | micro-saft-teams[.]live      | Teams masqs gleaned from Pivot #5                                                    |
| 52          | 20       | Delivery - Landing Masq            | teams-support-software[.]run | Teams masqs gleaned from Pivot #5                                                    |
| 53          | 20       | Delivery - Landing Masq            | teams-support-software[.]icu | Teams masqs gleaned from Pivot #5                                                    |
| 54          | 21       | Delivery - Landing Masq            | microsaft-teams[.]life       | Teams masq shared on X.                                                              |
| 55          | 24       | Delivery - Landing Masq            | google-meet-install[.]xyz    | Google Meet masq gleaned from Pivot #7.                                              |
| 56          | 24       | Delivery - Landing Masq            | google-meet-install[.]icu    | Google Meet masq gleaned from Pivot #7.                                              |
| 57          | 24       | Delivery - Landing Masq            | google-meet-app[.]run        | Google Meet masq gleaned from Pivot #7.                                              |

## Summary

In this section we took action on Mikhail Kasimov's pivot lead for the favicon hash for the Teams masqs. We adapted it to use the SHA256. We went over the process to extract the SHA256 hash for the Teams masqs. We also used the Google Meet masq as an example to extract the favicon by finding the `shortcut icon` in the HTML code. We enhanced our query by filtering out legitimate sites, and by adding unique page title keywords.