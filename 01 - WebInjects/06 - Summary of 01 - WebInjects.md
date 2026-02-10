# Summary of 01 - WebInjects

## Video Resources

- A collection of "shorts" is here: 
	- https://odysee.com/@MalasadaTech:8/Thruntellisearch-01-WebInjects-06-Summary:d
	- I will have a long form video up soon

## Summary

We've used TA2726, ZPHP, and LandUpdate808 to learn the concepts below.

## Point in Time Disclaimer

We discussed how the sections represent how things are in the current point in time. The info, patterns, and pivot techniques changed in the past, and will likely change in the future. Monitor threats for subtle changes.

## Intel sources

To learn about things, we need intel sources. We've learned how we can use Proofpoint and THREATfox as intel sources. We use their reporting and submissions as intel leads for indicators and named "things" such as TA2726, ZPHP, and LandUpdate808.

## Pivot Platforms

We used urlscan and VirusTotal to perform basic pivots. These are platforms that can be used to find additional adversary infrastructure. Explore the tools. Learn as much as you can about them. Master your tools. 

## Inject Patterns

We've learned that the code injected into compromised websites have patterns. Specifically, we've learned the URI patterns such as a long weird string can be used to identify TA2726 injects, “/work/original.js” can be used to identify ZPHP, and "#X#X.js" can be used to identify LandUpdate808 injects.

## Infrastructure Templates

We've learned how ZPHP uses a fitness-themed template, and how LandUpdate808 uses a template that renders the string "It works.".

## Pivots

We've performed pivots on the initial indicators to find additional adversary infrastructure. We used the IP for TA2726. The TA2726 domains will use the same IP at a given point in time. We used the page title and ASN for ZPHP. The ZPHP will use the same template, and they will be hosted on the same AS. We used the "It Works." response hash to find additional LandUpdate808 infrastructure.

## External Validation

External validation is using external assessments to validate your findings.
Intel sources can be used for external validation. You can use Proofpoint and THREATfox. You can also use VirusTotal community comments.

## First-hand Validation

First-hand validation is verifying the pattern yourself. It should hold a higher value than external validation because it is what you "witness", but it should still be used in addition to external validation when possible. urlscan.io can be used to perform first-hand validation.

## Different Object Types

We discussed the distinction, and the importance of the distinction, between different things. We discussed the WebInjects, FAKEUPDATES, and ClickFix techniques. We discussed the differences between a threat actor (TA), exploit kits (EKs), and payloads.

## Aliases

You need to know what aliases are. All the different CTI sources may use different names for the same thing. You need to make sure you're not missing anything, so you need to know the aliases. ZPHP is also known as SmartApeSG or just SmartApe. LandUpdate808 is also known as and has overlap with KongTuke, TAG-124, Chaya_002, DarkEngine. 

## The Process

- Ingest intel
- Identify the pattern that can be used to identify additional infrastructure
- Identify the unique property that can be used for validation
- Perform the pivot
- Validate the additional indicator
- Find an external validation

## The Way Forward

You can move forward to the next section, or you can practice with the guidance in section 01 - 05.

## Closing Remarks

Hope you've been enjoying the process. Let me know if anything should be clarified better.
