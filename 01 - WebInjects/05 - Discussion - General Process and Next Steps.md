
# 05 - Discussion - General Process and Next Steps

This section probably could've been discussed earlier in the first section. I wanted this design this to be something that you "jump in head first" into. That is, I didn't want to throw an excessive amount of concepts at you before you start performing tasks. I figure it would be easier and more interesting to begin defining patterns and producing results at the start. That is why this discussion is at the end of the section and not in the beginning.

The general steps that we've taken so far can be summarized with the bullet points below.

- Ingest intel
- Identify the pattern that can be used to identify additional infrastructure (the pivot)
- Identify the unique property that can be used for validation
- Perform the pivot
- Validate the additional indicator
- Find an external validation

## Ingest intel

Search the intel source for a given named threat. We used Proofpoint's Emerging Threat Ruleset Update Summary as the intel source, but you can also you other sources like THREATfox. In the next section, we'll use an X post as an intel source. You can use any social media source as an intel source. You could also monitor cyber security vendor blogs for intel leads. Take the intel lead and extract the indicator.  

## Identify the pattern that can be used to identify additional infrastructure

This part finds the property of the object that you can perform pivots on. You will use this property to find additional infrastructure. It must be a property that you can use to search on a platform like urlscan or VT (or any other available platforms). This is the "pivot".
- TA2726: Reverse IP
- ZPHP: Gym template page title
- LandUpdate808: "It works!"
## Identify the unique property that can be used for validation

This part finds the property that you will use to confirm the success of your pivot. It is the proof that you could use when you ask yourself "How do I know this additional indicator is used for this threat?". For WebInjects, the URI pattern of the inject can normally be used.
- TA2726: Long odd string
- ZPHP: “/work/original.js”
- LandUpdate808: "#X#X.js"

## Perform the Pivot

Take the pivot, and action it. Search for other domains that use the same IP if it's TA2726. Search for other domains that use the same gym template if it's ZPHP. Search for other domains that return "It works!" if you're searching for LandUpdate808.

## Validate the additional indicator

Take the unique property and validate it. We've used VT and urlscan.io to validate the additional indicator.
## Find an external validation

We've used VT and THREATfox, but we could also use Proofpoint's Emerging Threats rule as another external validation source
## Practice Tasks

These are tasks that you should do to continue to improve.

Explore other TAs and EKs. Are you able to observe inject patterns and infrastructure patterns? Are you able to find any unreported infrastructure?
## Continuously Monitor

If you haven’t already used the process to find additional adversary infrastructure, try it now. You will need to monitor the adversary over time. You will need to periodically check up on them for changes - changes in infrastructure and changes in behavior. Did SmartApeSG adopt a new template? Are they using a new AS? Does LandUpdate808 use a new default response instead of “It works.”? Consider the point in time disclaimer and how it applies.

Record your findings. Document the new indicators when you find them. Document the new patterns when you find them.