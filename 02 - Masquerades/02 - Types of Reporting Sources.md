## Types of Reporting Sources

In section 02 - Masquerades  unit 01 - Oyster Malware via Teams FakeApp, we found a new intel lead while performing external validation. We found the following Bleeping Computer article: https://www.bleepingcomputer.com/news/security/fake-microsoft-teams-installers-push-oyster-malware-via-malvertising/. This is a good point to discuss some concepts like news aggregators, first-hand reporting, the difference between the aggregator and the first-hand reporting, drilling down to review sources, and the intel-loop.

Generally, news aggregators will perform little to no first hand technical research, while cyber security product and service providers will perform only or mostly first hand technical research.

Their Goals

The two sources share a similar goal of spreading awareness, but they have different primary goal - the aggregator will likely have a goal of increasing website visitors for ad revenue, while the intrusion reporting would normally highlight driving product sales (their cyber security product or service). 

Visibility/Telemetry

The intrusion reporting will focus on the specific intrusion event. Their reporting will likely be limited to the vendor's visibility. Most vendors will have a visibility gap. A firewall vendor will have very good network telemetry, but maybe not so much endpoint telemetry. An email security appliance (spam/phishing/malspam) vendor will have great visibility into the email telemetry, but maybe not so great network or endpoint telemetry.

The news aggregator will combine or fuze multiple news sources. They can fuse the reporting into a better informed report. They can take the phishing or malvertizing reporting and show how that's used for the initial attack vector. They can take the AV or EDR/XDR reporting and highlight the malware's behavior on the host. They can take the reporting from the thrunting platform and show how the thrunting platform was able to find additional adversary infrastructure.

Granularity

The aggregator will normally focus on the high level details while the vendor reporting might be more granular. The security vendor's reporting needs to impress the readers, and drive them to purchase their products or services, or it needs to drive the reader into remaining an existing customer. Because of that, the security vendor's reporting might be much more granular. The security vendor would most likely highlight things like the defensive measures (such as obfuscating), persistence, data exfiltration techniques, or C2 details. The security vendor reporting will most likely include a list of indicators, TTP mapping, and any open detection rules (like SIGMA, YARA, or Suricata rules).

While the security vendor's reporting might be very detailed, the aggregator might summarize the reporting from one vendor's report in a paragraph or two. Because of that, it will most likely only include the high-level points.

Analyze Value Added

Not all aggregators are the same. As you review aggregators, analyze how much value the reporting adds from the original source. Do they fuze reporting together from multiple sources? Does it add a historical report that shows changes over time? Is it just a re-worded summary of someone else's work? Is it just a verbatim copy (they exist). There are other best-practice things to ask yourself. For now, just focus on asking yourself how much extra value the aggregation reporting adds to the first-hand reporting.

Review the Sources

In addition to analyzing the value added, review the sources that are cited. Perform the same analysis. Does the source add value? Is it first hand reporting? I enjoy reading articles from news aggregators because they provide a high-level overview, and they introduce sources that I might not have been aware of otherwise. In the Bleeping Computer article that I mentioned above, they referenced multiple articles. I list them below. We will action the Arctic Wolf Networks' report, the blackpoint report. We will not action the Rapid7 report because I think it might be too stale. The Rapid7 report is good to understand historical data, but maybe not for action.
 https://arcticwolf.com/resources/blog/malvertising-campaign-delivers-oyster-broomstick-backdoor-via-seo-poisoning-trojanized-tools/
 
https://blackpointcyber.com/blog/malicious-teams-installers-drop-oyster-malware/

https://www.rapid7.com/blog/post/2024/06/17/malvertising-campaign-leads-to-execution-of-oyster-backdoor/
