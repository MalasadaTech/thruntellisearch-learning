Expand on Proofpoint's intel leads. We used an x post as an intel lead. Then, we used Grok as an external validation, but we also used one of the validation sources as an intel lead. From that intel lead in section 02 - 03, we used Proofpoint as an external validation. Because we see that Proofpoint had the www-putty domain, you should ask yourself - should I search Proofpoint for their most current Oyster indicator?

Search here:

https://community.emergingthreats.net/search?q=oyster%20order%3Alatest

Newest is here:

https://community.emergingthreats.net/t/ruleset-update-summary-2025-10-03-v11031/3073

They're not indicators, they're C2 checkin rules, as pasted below:

- 2065047 - ET MALWARE Oyster Backdoor CnC Checkin M5 (malware.rules)
- 2065048 - ET MALWARE Oyster Backdoor CnC Checkin M6 (malware.rules)

We can use this. The SIDs are 2065047 and 2065048. Take those and search app.any.run/submissions

The most recent submission is here: https://app.any.run/tasks/9f3574bc-9bbf-423d-a052-86ae19778125. by the filename, we can glean they are using a Rufus-themed lure. We might be able to use that later.

The submission right before that is for the url cisco-support-software[.]run. https://app.any.run/tasks/85c7e2d1-abe5-4ab4-8552-c448ffc66979

We see it masquerades as a Cisco AnyConnect-themed lure.

search it in urlscan: https://urlscan.io/search/#cisco-support-software.run

Take the most recent scan task with a 200 response: https://urlscan.io/result/019a97eb-bc86-733a-8038-06f5589ebc9a/

Analyze the responses for pattern matches.

https://urlscan.io/result/019a97eb-bc86-733a-8038-06f5589ebc9a/#transactions

It has market12.js... https://urlscan.io/responses/67d6082327e5e9f056da5fd60495a4f542e602f6bd53e2496e6635e7bea98aaf/






FOR THE NEXT SECTIONS, explore the Rufus lures, and any other that can be gleaned from the Oyster checkin rule... 

Can do Winrar/downloads...
Can do notepad-plus-plus[.]run



Consider adding a C2 section... using C2 posts on X, and the checkin rules form Proofpoint... use those rules and find matches in any run........ that is the C2 domains from the download-script.js file...

-------------------------

Zoom...
https://app.any.run/submissions# oyster
==>
https://app.any.run/tasks/d4852e06-f90c-485d-a59c-475f58d7d47a
==>
https://urlscan.io/search/#zoom-install.us
https://urlscan.io/result/0199bd10-430a-762f-8b81-c9a6e8026366/
https://urlscan.io/result/0199bd10-430a-762f-8b81-c9a6e8026366/#transactions
https://urlscan.io/responses/0bb9d0a51afae7eea8fa2a4dbe2f414f013ba862cfe135b4bab0b93880c120ed/

^ continues to a pivot on the C2...

https://app.any.run/tasks/d4852e06-f90c-485d-a59c-475f58d7d47a
==>
C2: lorrieobrien[.]com
==>
https://urlscan.io/search/#lorrieobrien.com
https://urlscan.io/result/0199ab40-315b-734e-96fc-2de3076fa488/
https://urlscan.io/result/0199ab40-315b-734e-96fc-2de3076fa488/#transactions
https://urlscan.io/search/#hash%3A4176caf548e995285c2f32701426289a0fefc21fd427a4c2c6164282fa04bba0
... take the domain indicator from the results...
... search it in Any Run.... take tedbutz[.]com for example. It reveals other  indicators...




-------------

introduce searching in github.... =( nm... can't search the code without signing in...




------------------------

What's this? Does this reveal anything about the thractor's infra?

https://urlscan.io/result/019aaecb-d04b-7510-b937-93f99aaf510c#summary

^garbage, unrelated...



From: 10 - Actioning the C2 Indicators, the Rufus hash: efaae1104c2a532bfaaa2fd11f6345ee321cf0119eeb619526df4f2940795750, if you search it in Any Run, you'll find additional lure domains... This should be before the section below... make the connection that even though https://app.any.run/tasks/dbcc1128-2fba-4ceb-beb1-f0b5b1dc655e shows the executable wasn't allowed to execute, we can glean that `teams-support-software[.]icu` is serving Oyster malware because we confirmed the hash elsewhere, and the any run session shows it serving it....



below from 02JAN25 section 11 notes...
-----------------------------------------------------


Revisit....... ***OR just work off of the .bet and .icu in the indicator's table... First show the .bet, and highlight how they now redirect to google, then show the .icu and show how they no longer use the download or market.js files any more...***

https://urlscan.io/search/#page.title%3A%22Download%20Microsoft%20Teams%20Desktop%20and%20Mobile%20Apps%20%7C%20Microsoft%20Teams%22%20

https://urlscan.io/result/019ac2d5-dbfd-728d-8b0a-32b8f9d7e679/

Observe the same lure; without download/market.js

https://urlscan.io/result/019ac2d5-dbfd-728d-8b0a-32b8f9d7e679/dom/
CTRL + F .exe; they are using a direct download...

https://urlscan.io/search/#page.domain%3Amicrosoft-teams.icu

https://urlscan.io/result/019ac359-cab7-7618-ac4e-682fa7655329/

Copy the hash; 
b5f86a350a6ceb3647f6c35dd276986a7cbfd72e97dcffd57311225e092a8126


search it in Any Run

https://app.any.run/tasks/fea125ae-7d22-46c7-bf8b-59d66dbd5a34

It connects to scs-techresources[.]com ***HIGHLIGHT HOW IT ADDS VALUE TO MONITOR INDICATORS AT ALL ATTACK PHASES***

This is a match. They no longer use the download or market JS naming pattern.


Highlight how you can track the thractor using the different indicators throughout their delivery and C2

!!! AT SOME POINT, NEED TO HIGHLIGHT THE SCHEDULED TASK BEHAVIOR, SO THAT IT CAN BE USED FOR PATTERN IDENTIFICAITON LATER IN OTHER SECTIONS !!!



***Possible continuation if we don't revisit the pivot... we can ***
https://urlscan.io/search/#page.title%3A%22Download%20Microsoft%20Teams%20Desktop%20and%20Mobile%20Apps%20%7C%20Microsoft%20Teams%22%20

https://urlscan.io/search/#micro-saft-teams.live
Observe they're forwarding to Google

The file download: https://urlscan.io/result/019aecfa-a8d0-769c-9f0f-6564a99229c9/
is the legit MS Teams: https://www.virustotal.com/gui/file/52ab9768aeed9e5e99636cdc61be377566a8489897724228a21cd057f1c65147/details

