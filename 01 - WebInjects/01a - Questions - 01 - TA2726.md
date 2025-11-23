# Questions for 01 - TA2726

The answers are a bit below the queries.

Q1 - What is an intel source?

Q2 - What is an intel lead?

Q3 - In the TA2726 learning content, we use the VT comments of a user to perform external validation. What's that user's username?

Q4 - What are some other names that TA2726 is associated with?

Q5 - In VirusTotal, we reviewed the IP address that quietshalecompany[.]com used. Why did we do that?

Q6 - What is the gist of external validation?

Q7 - What is the gist of first-hand validation?

Q8 - What did we use to validate the TA2726 first-hand?

Q9 - What did we use as an intel lead for TA2726?

Q10 - Which tool did we use to review webscans of websites?

Q11 - Which VT tab shows you the IP addresses that are related to a given domain?

Q12 - Which VT tab shows you the community comments on a given indicator?

Q13 - What is the difference between the VT score 16/95 and -12?

Q14 - Which urlscan tab shows you the HTTP transactions from a scan task?


All answers below...
| (line spacers, so you don't view the answers on accident)
|
|
|
|
|
|
|
|
|

A1 - An intel source is an entity (a person, or group - like a security company) that can be used as a source for investigations or research.

A2 - An intel lead is a report or post provided by an intel source. It is a lead because the information can be used to perform an investigation. We discuss extracting indicators from intel leads, and performing pivots on the indicators to find additional adversary infrastructure.

A3 - JaffaCakes118

A4 - SocGholish, FAKEUPDATES, more (there could be more, but this is what we glazed over)

A5 - TA2726 domains use the same domain at a given time. You can perform a reverse lookup on the IP address to find other TA2726 domains.

A6 - It is comparing what other people say about a malicious domain. If they say stuff that agrees with your investigation findings, it's a good thing.

A7 - You take an observed behavior or pattern from one malicious TA2726 domain, and then we check if the additional domain has a matching behavior or pattern.

A8 - Tool was urlscan.io, and we used the inject URL's pattern of gobbledigoop.

A9 - Proofpoint's Emerging Threats Ruleset Update Summary

A10 - We used urlscan.io. We reviewed the scan tasks to find additional TA2726 domains.

A11 - The RELATIONS tab in VT shows you the IP addresses that are related to a given domain - in addition to other relations.

A12 - The COMMUNITY tab in VT shows the comments.

A13 - The 16/95 fraction shows how many vendors flagged the indicator as malicious, while the -12 is how many downvotes the indicator got. 

A14 - The HTTP tab shows the HTTP transactions from a scan task.

