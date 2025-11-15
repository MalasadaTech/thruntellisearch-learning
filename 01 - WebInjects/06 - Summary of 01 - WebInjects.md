# Summary of 01 - WebInjects

## Summary

We've used TA2726, ZPHP, and LandUpdate808 to learn the concepts below.

## Point in Time Disclaimer

This represents how things are in the current point in time. The info, patterns, and pivot techniques changed in the past, and will likely change in the future. Monitor threats for subtle changes.

## Intel sources

To learn about things, we need intel sources. We've learned how we can use Proofpoint and THREATfox as intel sourcesleads. We use their reporting and submissions as intel leads for indicators and named "things" such as TA2726, ZPHP, and LandUpdate808.

## Inject Patterns

We've learned that the code injected into compromised websites have patterns. Specifically, we've learned the URI patterns such as a long weird string can be used to identify TA2726 injects, “/work/original.js” can be used to identify ZPHP, and "#X#X.js" can be used to identify LandUpdate808 injects.
## Infrastructure Templates


## Pivots

IP for TA2726, Page title and ASN for ZPHP, "It Works." hash for LandUpdate808.

## External Validation

External validation is -...using other's assessments to validate your findings.
Intel sources can be used for external validation. Proofpoint and THREATfox. You can also use VirusTotal.

## First-hand Validation

First-hand validation is... verifying the pattern yourself. It should hold a higher value than external validation because it is what you "witness".
urlscan.io as the validation source.

## Different Attribution Types

Threat actor, delivery technique, campaign, malware

FAKEUPDATES, ClickFix, SocGholish, TA2726, LandUpdate

## Aliases

Need to know what aliases are

