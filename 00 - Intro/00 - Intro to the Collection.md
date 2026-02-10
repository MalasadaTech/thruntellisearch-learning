## What is CTI?

Cyber Threat Intelligence (CTI) describes intelligence on internet bad guys ( the bad guys are commonly referred to as a "threat actors" or "adversaries"). Most CTI reports will discuss a specific incident. It could include stuff like the URL that a victim downloaded malware from, information on the malware like what it does when it's executed, and command and control (C2) activities. These lessons focus on tracking adversary infrastructure - that is, the domains, URLs, and IPs that are used to deliver and C2 malicious activities.

## Why do we need to search for additional adversary infrastructure?

When a Cyber Security professional reads CTI reports, they need to search their environment for the malicious activities. How do they do this? They may copy the indicators, and search for them in their security tools. Here's the problem - the indicators from the CTI report might not include all of the TA infrastructure. The Cyber Security professionals must perform additional tasks so they can search for ALL (ideally all) of the indicators for a given TA. The following list below is a basic guideline of the tasks we'll perform.

- Extract indicators from a given CTI report   
- Identify properties of the indicator that could be a pattern (pivot)
- Perform pivots 
- Action the additional indicators
	- For someone who does this for a living, they would perform an internal hunt (search their tools for related activity)
	- If you're in an enthusiast role, you can record it, and post about it
- Record the methods to monitor the threat actor activities
- Periodically perform external searches to find additional adversary infrastructure

The guide above is for intel-driven hunts (hunts that begin because you read someone else's report on something). There are also hypothesis-driven hunts. The hypothesis is basically an educated guess. These are hunts that start off with a hunch something like "Threat actors phish for login credentials for Bank A by creating fake websites that pretend to be Bank A, so there must be phishing sites that pretend to be Bank B". You can test this hypothesis and search for masquerading sites pretending to be Bank B.

## Tool Preference

I use many different tools. Some are free, some cost money. Some can be used without logging in, some require a login. Some let you use a free email address for signup, some require a non-free email address for signup. This collection of learning sections will prioritize tools that are free and can be used without authentication. My son and nephews are the target audience for this training collection. Using free and unauthenticated tools removes barriers to entry for my family, and for anyone else that may use this.

- There is a caveat with Any Run. 
	- When I first started working on this, you could search the Any Run submissions without being logged in.
	- At some point before February of 2026, Any Run changed it so you now need to be logged in (with at least a free account) to search the submissions.
	- I kept the Any Run content in because there's just too many parts that need it.
	- I don't know what the alternative is yet.

I recommend that everyone explore every tool that is available, even if I don't list it.
