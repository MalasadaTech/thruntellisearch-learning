## 06 - Use Proofpoint's Suricata Rules

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

(REFINE to filter for URLs only...)

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










