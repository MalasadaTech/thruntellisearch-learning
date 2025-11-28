# Thruntellisearch Template

Copy this and use it as a template to practice the concepts. Use it as a "file in the blanks" worksheet.

## Intel Lead

Source entity:
(Example: Proofpoint)


Source URL:
(Example: https://community.emergingthreats.net/t/ruleset-update-summary-2025-09-30-v11027/3066)


Source Description:
(Example: Proofpoint's Ruleset Update Summary)


Indicator:
(Example: quietshalecompany[.]com)


## Inject Pattern 

Description:
(Example: The URI path is gobble-di-goop for TA2726)


Sample URL to use as a source:
(Example: The following scan task can be used to validate quiestshalecompany[.]com's inject pattern is gobbledigoop: https://urlscan.io/result/0199d50e-e224-7546-9b97-168d22c41a22/#transactions)


## Infrastructure (or template) Pattern (for the pivot)

Description:
(Example: TA2726 domains resolve to the same IP address at a given time. If you find one domain, and do a reverse lookup on the IP address, you'll identify additional domain indicators.)

Sample URL to use as a reference:
(Example: You can perform a reverse lookup using VT via this link - and you can observe the additional domains: https://www.virustotal.com/gui/ip-address/144.31.193.106/relations)


## Additional Indicator

List the additional indicator(s) you found:
(Example: javascriptbasics[.]com)

## External Validation Method

Description: 
(Example: You can use VT's comments in the community tab to validate via external validation. The comments in the following link shows that there is reporting on THREATfox that assesses javascriptbasics[.]com is a TA2726 domain: https://www.virustotal.com/gui/domain/javascriptbasics.com/community)

## Internal Validation

Link to show validation proof:
(Example: The following link shows that javascriptbasics[.]com uses the same WebInject pattern: https://urlscan.io/result/0199d4c1-a59b-754d-97a3-97de08b1f9d2/#transactions)