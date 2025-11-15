# 03 - Key Terms Discussion

## Point in Time Disclaimer

This represents how things are in the current point in time. The info, patterns, and pivot techniques changed in the past, and will likely change in the future. Monitor threats for subtle changes.

## WebInjects

WebInjects describes the technique of injecting malicious code into a compromised site. It is a nice and generic term that can be combined with other descriptors.

## FAKEUPDATES

FAKEUPDATES describes the technique of tricking the victim into thinking they need to download and execute a malicious executable. SocGholish is probably the most famous one in this category.

## ClickFix

ClickFix describes the technique of tricking the victim into executing malicious code that was copied to the victims clipboard. The threat actor can present different dialogues to accomplish this. They may present a popup that says something is broken, and to fix it, the vicitim needs to execute the malicious code. They may also present a fake captcha popup that states the victim must verify they're a human by pasting and executing the malicious code that was copied to their clipboard.

## Threat Actor (TA)

The threat actor is the person or group that performs the bad activity. There are threat actors that compromise websites. There are threat actors that operate the TDSs. There are threat actors that develop malware.

## Exploit Kit (EK)

Exploit kits are specific kits. ZPHP is tracked as an EK. LandUpdate808 is also tracked as an EK. It's important to draw these distinctions. ZPHP is not a threat actor. For the compromised website, the ZPHP EK is the payload, but for the victim that visits the compromised site, the ZPHP EK is not the payload - it is the delivery method to deliver NetSupport Manager RAT. 

## Payload

TAs use EKs to get a malicious payload on the victim's computer. The payload can be custom malware. It could just be Remote Monitoring and Management (RMM) software. The TA could deliver multiple payloads. The TA can change the payload.

## How Mixing Terms Could Muddy the Water

It is important to highlight certain concepts at this point. You may have seen in the ZPHP/SmartApeSG snips that some ZPHP indicators on THREATfox are labeled as the FAKEUPDATES malware family, while some SmartApeSG indicators on THREATfox are labeled as the “NetSupportManager RAT” malware family. This can become confusing. It’s important to understand the concepts of a threat actor, a delivery method (or lure technique), a campaign, and the malware.

For ZPHP or SmartApeSG, there is no threat actor designation. 

The delivery method (or lure technique) is called FakeUpdates. It’s called fake updates because code is injected into compromised websites to load a page that tells the user their browser needs to be updated. The update file that is provided is malware.  Note that ZPHP now uses the ClickFix technique to trick the victim into executing a malicious command.

Proofpoint calls it ZPHP [[https://www.proofpoint.com/us/blog/threat-insight/are-you-sure-your-browser-date-current-landscape-fake-browser-updates](https://www.proofpoint.com/us/blog/threat-insight/are-you-sure-your-browser-date-current-landscape-fake-browser-updates)]. I couldn’t find the reasoning stated, but I assess that Proofpoint likely uses ZPHP because of the early resources that used a long string starting with a Z. For example, “/zwewmrqqgqnaww.php”. 

Jérôme Segura reports that Malwarebytes named it SmartApeSG by combining the AS, SmartApe, and SG (for SocGholish) [[https://www.threatdown.com/blog/smartapesg-06-11-2024/](https://www.threatdown.com/blog/smartapesg-06-11-2024/)]. 

Many vendors report the malware delivered is NetSupport RAT.

It is important to understand that threat actors can change the malware that’s delivered. For example, a threat actor can first deploy a stealer malware to steal cached credentials and crypto wallet info. Then, the threat actor may also deploy an RMM to maintain persistent access. At any given time, a threat actor could change to a different stealer, or a different RMM, or a totally different malware altogether. It’s important that we make the distinction so that it doesn’t “muddy the water” later.