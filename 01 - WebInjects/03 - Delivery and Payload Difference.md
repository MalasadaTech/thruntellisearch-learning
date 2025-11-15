(REVISE: Need to add in TA and EK. It should list TA, Delivery (FAKEUPDATE, ClickFix, WebInject), EK specific (ZPHP, LandUpdate808, KeitaroTDS), Payload (Malware))

## Point in Time Disclaimer

This represents how things are in the current point in time. The info, patterns, and pivot techniques changed in the past, and will likely change in the future. Monitor threats for subtle changes.

It is important to highlight certain concepts at this point. You may have seen in the ZPHP/SmartApeSG snips that some ZPHP indicators on THREATfox are labeled as the FAKEUPDATES malware family, while some SmartApeSG indicators on THREATfox are labeled as the “NetSupportManager RAT” malware family. This can become confusing. It’s important to understand the concepts of a threat actor, a delivery method (or lure technique), a campaign, and the malware.

For ZPHP or SmartApeSG, there is no threat actor designation. 

The delivery method (or lure technique) is called FakeUpdates. It’s called fake updates because code is injected into compromised websites to load a page that tells the user their browser needs to be updated. The update file that is provided is malware.  Note that ZPHP now uses the ClickFix technique to trick the victim into executing a malicious command.

I consider ZPHP or SmartApeSG to be a campaign designation. Proofpoint calls it ZPHP [[https://www.proofpoint.com/us/blog/threat-insight/are-you-sure-your-browser-date-current-landscape-fake-browser-updates](https://www.proofpoint.com/us/blog/threat-insight/are-you-sure-your-browser-date-current-landscape-fake-browser-updates)]. I couldn’t find the reasoning stated, but I assess that Proofpoint likely uses ZPHP because of the early resources that used a long string starting with a Z. For example, “/zwewmrqqgqnaww.php”. 

Jérôme Segura reports that Malwarebytes named it SmartApeSG by combining the AS, SmartApe, and SG (for SocGholish) [[https://www.threatdown.com/blog/smartapesg-06-11-2024/](https://www.threatdown.com/blog/smartapesg-06-11-2024/)]. 

Many vendors report the malware delivered is NetSupport RAT.

It is important to understand that threat actors can change the malware that’s delivered. For example, a threat actor can first deploy a stealer malware to steal cached credentials and crypto wallet info. Then, the threat actor may also deploy an RMM (Remote Monitoring and Management) to maintain persistent access. At any given time, a threat actor could change to a different stealer, or a different RMM, or a totally different malware altogether. It’s important that we make the distinction so that it doesn’t “muddy the water” later.