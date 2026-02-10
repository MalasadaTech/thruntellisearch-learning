# 03 - Discussion - Key Terms

| [Previous](02%20-%20ZPHP%20(SmartApeSG).md) | [Home](../links.md) | [Next](04%20-%20LandUpdate808.md) |
| :------------------------------------------- | :-----------------: | ---------------------------------: |



## Video Resources

- A collection of "shorts" is here: 
	- https://odysee.com/@MalasadaTech:8/Thruntellisearch-01-WebInjects-03-KeyTerms:6
	- I will have a long form video up soon

## Point in Time Disclaimer

This represents how things are in the current point in time. The info, patterns, and pivot techniques changed in the past, and will likely change in the future. Monitor threats for subtle changes.

## Intro

This section will cover high-level overviews of different object types and objects. It'll cover techniques such as WebInjects, FAKEUPDATES, and ClickFix. It'll discuss specific objects such as TA2726, ZPHP, and LandUpdate808.
## WebInjects

WebInjects describes the technique of injecting malicious code into a compromised site. It is a nice and generic term that can be combined with other descriptors.

## FAKEUPDATES

FAKEUPDATES describes the technique of tricking the victim into thinking they need to download and execute a malicious executable. SocGholish is probably the most famous one in this category.

## ClickFix

ClickFix describes the technique of tricking the victim into executing malicious code that was copied to the victims clipboard. The threat actor can present different dialogues to accomplish this. They may present a popup that says something is broken, and to fix it, the vicitim needs to execute the malicious code. They may also present a fake captcha popup that states the victim must verify they're a human by pasting and executing the malicious code that was copied to their clipboard.

## Threat Actor (TA)

The threat actor is the person or group that performs the bad activity. There are threat actors that compromise websites. There are threat actors that operate the TDSs. There are threat actors that develop malware.

## Exploit Kit (EK)

Exploit kits are specific kits. ZPHP is tracked as an EK. LandUpdate808 is also tracked as an EK. It's important to draw these distinctions. ZPHP is not a threat actor. For the compromised website, the ZPHP EK is the payload, but for the victim that visits the compromised site, the ZPHP EK is not the payload - it is the delivery method to deliver NetSupport Manager RAT (NSR). 

## Payload

TAs use EKs to get a malicious payload on the victim's computer. The payload can be custom malware. It could just be Remote Monitoring and Management (RMM) software. The TA could deliver multiple payloads. The TA can change the payload.

## Do

Do make an effort to actively consider the given object type. Is it a technique, a threat actor, an exploit kit, or a payload?

## Summary

This section covered high-level overviews of different object types and objects. It covered techniques such as WebInjects, FAKEUPDATES, and ClickFix. WebInjects is the technique of injecting malicious code into compromised websites. FAKEUPDATES describe the technique of tricking the victim into executing malware disguised as an update. ClickFix describes the technique of tricking the victim into pasting and executing malicious code. A Threat Actor (TA) is the entity that performs the bad activity (the person or group). An Exploit Kit (EK) describes specific kits used by TAs to deliver their payloads. The payload is the software that TAs seek to execute on victim computers. It covered specific objects such as TA2726, ZPHP, and LandUpdate808.

| [Previous](02%20-%20ZPHP%20(SmartApeSG).md) | [Home](../links.md) | [Next](04%20-%20LandUpdate808.md) |
| :------------------------------------------- | :-----------------: | ---------------------------------: |