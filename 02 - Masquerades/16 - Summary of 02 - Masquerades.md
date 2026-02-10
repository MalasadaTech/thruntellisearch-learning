# 16 - Summary

## Initial Summary Thoughts

The `02 - Masquerades` section group packed a lot of info and techniques that you can use in your thruntellisearch endeavors. I hope you find future scenarios that you can apply this knowledge to. I hope this inspires you to master the tools that you have access to. I hope you become the world's greatest analyst.

## Highlights

This section contains the highlights of the key concepts learned. The key concepts include the following:
- How you can take an intel lead and build off of it.
- How you can take an indicator from intel reporting, find patterns, action the patterns, and find additional adversary infrastructure.
- How we can analyze the delivery techniques to uncover the domains used for dynamic delivery.
- How we can use the unique filename patterns to enhance pivot queries.
- How we can identify and pivot on patterns that the dynamic delivery domains use.
- How to perform intel collections - 
	- using a pivot table, a source table, and an indicator table.
	- investigating each indicator (simulated - I showed examples to follow; you should do them all).
- How you can use Proofpoint's Suricata rules in Any Run to find more thractor activity.
- How you can use the Any Run tags to identify more activity.
- How you can analyze Any Run sessions to identify the different C2 activities.
- How you can perform pivots on the indicators at the different attack phases to identify additional thractor infrastructure.
- How we can use AI to find intel reporting on each new indicator.
- How we can analyze the scheduled task creation in Any Run and VT.
- How we need to monitor and update pivots as the thractor updates their TTPs.
- How we need to monitor for thractor upgrades such as redirecting to Google or serving legitimate software instead of malware.
- How we can perform pivots using the `shortcut icon` (favicon).

## Section Details

The following paragraphs will have more details per section. It is much more verbose. Good luck!

## Section 01 - Oyster Malware via Teams FakeApp

In Section `01 - Oyster Malware via Teams FakeApp`, we used an X post as intel lead. We extracted the malicious domain `teams-install[.]icu`. We searched urlscan for patterns. We pivoted with the query `page.title:"Download Microsoft Teams Desktop and Mobile Apps | Microsoft Teams" AND filename:"download*"`. We validated the `download-script##.js` file pattern. We found the thractor used dynamic delivery domains in `apiUrls`, like `witherspoon-law[.]com` and `compaq-computers[.]com`. We used Grok for external validation. We checked its references. We saw Grok was not fully accurate. We learned to always verify references.

## Section 02 - Types of Reporting Sources

In Section `02 - Types of Reporting Sources`, we discuss the differences between cybersecurity news aggregators and first-hand vendor reporting. BleepingComputer is a news aggregator. Arctic Wolf and Blackpoint Cyber provide first-hand reporting. We note that aggregators provide high-level overviews, fuse multiple sources for broader context, and their goal is to increase traffic to their websites for ad revenue. We note that security vendors provide more detailed analysis and their goal is to promote their products and services. We evaluate aggregator value added, such as fusing reports or adding historical context, and we evaluate and avoid sources that simply reword other's works. We drill down into cited sources. We assess their recency and relevance.

## Section 03 - Intel Collections

In Section `03 - Intel Collections`, we expand on intel leads for dynamic thractor campaigns by cycling through steps: starting with intel leads, identifying patterns, searching PAI for reporting, and aggregating insights. We action the sources from the BleepingComputer article. Arctic Wolf provieds CTI on the PuTTy masqs. Blackpoint provides the CTI on the Teams and AnyDesk masqs. We use Rapid7 for historical context; we don't action their intel. We broaden the topic to "Malvertising Fake Apps to Deliver Oyster Malware" to include varied lures. We organize intel via tables. The Source Table lists references like X posts, training sections, and articles with dates, titles, comments, URLs. The Pivot Table lists the pivots; it specifies the platform and the pivot query. The Indicator Table lists the indicators that we glean from pivots and PAI. It includes a column for the attack phase so that we can track if it is falls in the delivery or C2 phases. The indicators also include notes and sources for traceability.

## Section 04 - Dynamic Delivery Domains (apiUrls)

In Section `04 - Dynamic Delivery Domains (apiUrls)`, we analyzed the dynamic delivery domains from previous sections. These included `witherspoon-law[.]com` and `compaq-computers[.]com`. The domains were stored in the `apiUrls` array inside the `download*.js` files. The domains were only requested when the user clicked the download button. We searched these domains in urlscan. We looked for patterns like blank screenshots and unrelated page titles. One pattern used `dream-me.com`. We then pivoted to Any Run submissions to confirm malicious use. This uncovered new lures. We found a WinSCP-themed lure at `winscp[.]id`. We found a Notepad++-themed lure at `notepad-plus-plus[.]run`. We extracted more dynamic domains from these sessions. New domains included `msaonl[.]com`, `ncvalor[.]com`, `doctorreportcard[.]com`, `toshibaaccessories[.]com`, and `space-amazons[.]com`. We updated the tables. We added Source #8 for this analysis. We added Source #9 for the new pivot query `page.title:"dream-me.com"`. We added Indicators #13 - #22 for the new landing masqs and dynamic domains. We included notes on themes and sources for traceability. Multiple lures shared the same dynamic domains. This helped us find more infrastructure by searching Any Run.

## Section 05 - Actioning the PuTTy Lure Intel

In Section `05 - Actioning the PuTTy Lure Intel`, we actioned the PuTTy-themed lures from prior indicators. We skipped Indicator #5 since it was a Teams lure. We started with Indicator #6, `updaterputty[.]com`. We searched it in urlscan. We analyzed the oldest scan. We noted the page title: `Download PuTTY - a free SSH and telnet client for Windows`. We adapted the previous query to this title plus `filename:"download*"`. We validated the pivot internally by checking matching `download-script*.js` files with `apiUrls`. We validated externally using Proofpoint rules. We added Pivot #3 for PuTTy masqs to the Pivot Table. We added Source #10 for this pivot to the Source Table. We added Indicators #23 - #25 for new PuTTy lures like `www-putty[.]com`, `putty[.]network`, and `putty[.]fyi`. We found an additional lead in VT comments linking to a LevelBlue report. We added Source #11 for the LevelBlue PuTTy analysis. We merged new indicators from it, adding #26 - #33 for more PuTTy lures and dynamic domains like `heartlandenergy[.]ai` and `ruben.findinit[.]com`, updating existing rows where duplicates existed. We updated table comments for clarity. We identified more lures in this cycle. We used Proofpoint for external validation.

## Section 06 - Actioning the AnyDesk Lure Intel

In Section `06 - Actioning the AnyDesk Lure Intel`, we actioned Indicator #12, the AnyDesk lure `anydesksoftware[.]net`. We searched it in urlscan. We observed the page title `Remote Desktop Software for Windows | AnyDesk`. We validated it matched the download pattern with `download5.js`. We extracted the dynamic delivery domain `cleancarcatalog[.]com` from the script's `apiUrls`. We performed a pivot using the page title query with `filename:"download*"` and filtered out `anydesk[.]com`. We found `anydesknow[.]net` as a result. We could not find the download script for it. We checked Any Run, THREATfox, VT, Proofpoint, and AlienVault for validation. There were no useful results. We added a row to the Indicator Table for the suspicious domain with a note unable to validate. This section showed that not every effort yields results.

## Section 07 - Use Proofpoint's Suricata Rules

In Section `07 - Use Proofpoint's Suricata Rules`, we introduced a new Thruntellisearch method. We searched Proofpoint for "oyster". We found Checkin rules with SIDs `2065047` and `2065048`. We searched Any Run submissions for these SIDs. We found a recent submission with a Rufus-themed lure. We focused on the URL submission for `cisco-support-software[.]run`. It masqueraded as Cisco AnyConnect. We analyzed it in urlscan. We found `market12.js` instead of `download*.js`. This showed a change in threat actor behavior.

## Section 08 - Use Any Run Tag to Identify More Indicators

In Section `08 - Use Any Run Tag to Identify More Indicators`, we searched Any Run for "oyster" tag with the `Runtype` `URL`. We found `zoom-install[.]us`. We verified it in urlscan. It used "download-script.js". We extracted `mce-associates[.]com` from `apiUrls`.

## Section 09 - Analyzing the C2

In Section `09 - Analyzing the C2`, we analyzed the Any Run session for `zoom-install[.]us`. We identified the C2 domain `lorrieobrien[.]com` from connections. We searched it in urlscan. We found a unique response hash. We pivoted on the hash. We found additional C2 domains: `tedbutz[.]com`, `scs-techresources[.]com`, `macsimizers[.]com`, `pont-express[.]com`, and `nickbush24[.]com`.

## Section 10 - Actioning the Initial C2 Indicators

In Section `10 - Actioning the Initial C2 Indicators`, we actioned new C2 indicators. We searched Any Run for `tedbutz[.]com`. We found lures for Rufus, Google Meet, and Cisco AnyConnect. We analyzed a Rufus submission. We reviewed the scheduled task. It used `rundll32.exe` to execute a DLL function. We checked connections for `rundll32.exe`. It connected to an IP resolving to `coretether[.]com`. We labeled this as rundll32 C2. We analyzed a Google Meet submission. We found `registrywave[.]com` as another rundll32 C2. We distinguished between Initial C2 and rundll32 C2.

## Section 11 - Using AI to Enrich Indicators

In Section `11 - Using AI to Enrich Indicators`, we used AI to enrich indicators. We searched for CTI reports on `tedbutz[.]com`. We specified no generic Oyster info. We wanted sources with date, URL, title, and succinct summary. We found a CyberProof report. It discussed Google Meet lures. We added new indicators: `nucleusgate[.]com` and `google-meet-app[.]icu`. We noted to repeat for each indicator.

## Section 12 - Actioning the rundll32 C2 Indicators

In Section `12 - Actioning the rundll32 C2 Indicators`, we actioned three rundll32 C2 indicators: `coretether[.]com`, `registrywave[.]com`, and `nucleusgate[.]com`. We searched them in Any Run. We found two Teams masqs: `microsoft-teams[.]bet` and `microsoft-teams[.]icu`.

## Section 13 - Actioning New Masq Indicators

In Section `13 - Actioning New Masq Indicators`, we actioned two new Teams masqs: `microsoft-teams[.]bet` and `microsoft-teams[.]icu`. We searched them in urlscan. We found some scans redirected to Google. This showed the thractor is now filtering out unwanted traffic. We observed malware hosted directly on the masq domain. We no longer saw `download*` or `market*` JS patterns. We found the Download button linked directly to the EXE file. We analyzed a downloaded file in VT. It confirmed malicious behavior. It resolved known C2 domains: `coretether[.]com`, `scs-techresources[.]com`, and `registrywave[.]com`. It used the same scheduled task with `rundll32.exe`. We noted the threat actor stopped using `apiUrls`.

## Section 14 - Revisit Pivot #1

In Section `14 - Revisit Pivot #1`, we revisited Pivot #1 because of the recently observed behaviors. We updated it to Pivot #5 by removing the filename filter. We found new Teams masqs: `micro-saft-teams[.]live`, `teams-support-software[.]run`, and `teams-support-software[.]icu`. We checked PAI on `micro-saft-teams[.]live` from X posts. It sometimes served legit MS Teams file. We actioned `teams-support-software[.]icu`. We found malware in Any Run. We analyzed in VT. It was tagged ShellcodeRunner but confirmed Oyster via behavior. We added Pivot #5. We added sources for the pivot and an X post. We added four new indicators.

## Section 15 - Favicon Pivots

In Section `15 - Favicon Pivots`, we used Mikhail Kasimov's X post as intel lead for favicon pivot. We adapted the MD5 to SHA256 hash for urlscan. We extracted the hash from the Teams masq scan. We repeated for Google Meet masq `google-meet-app[.]icu`. We found a non-standard favicon in HTML using a PNG file. We refined the pivot by filtering legit Google sites and adding title keywords "meet" and "workspace". We found new masqs: `google-meet-install[.]xyz`, `google-meet-install[.]icu`, and `google-meet-app[.]run`.

## Malahoz

Thanks for making it this far! See you in the next one!
