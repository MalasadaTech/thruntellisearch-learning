# 08 -  Actioning Oyster C2 via Any Run Tag

PIVOT ON THE MALWARE C2 PATTERN!

IT MUST LIST THE SRS-TECH>....

------------------

In the previous section, we used Proofpoint's Suricata Rules to identify additional adversary infrastructure. In this section, we will use Any Run's Oyster tag to identify more adversary infrastructure.

Zoom...

Go to the Any Run Reports page. Click the link below to go there directly.

https://app.any.run/submissions# 

Search for the tag "oyster ", and set the Runtype to URL.

At the time of creating this content, the result on the top is for a URL submission to zoom-install[.]us. It is linked below.

https://app.any.run/tasks/d4852e06-f90c-485d-a59c-475f58d7d47a

Let's see if it uses the download*.js filename or if it's something different. Search for the domain in urlscan. Click the link below to go directly to the search.

https://urlscan.io/search/#zoom-install.us

The link below is the result on the top - at the time of making the content.

https://urlscan.io/result/0199bd10-430a-762f-8b81-c9a6e8026366/

Review the HTTP transactions and check for the filename pattern.

https://urlscan.io/result/0199bd10-430a-762f-8b81-c9a6e8026366/#transactions

Cool, it uses the filename "download-script.js". Click the link below to confirm it has the apiUrls const at the top of the file.

https://urlscan.io/responses/0bb9d0a51afae7eea8fa2a4dbe2f414f013ba862cfe135b4bab0b93880c120ed/

## Identify the C2 Domain

Let's go back to the initial Any Run session. For simplicity, I've pasted the submission session link below.

https://app.any.run/tasks/d4852e06-f90c-485d-a59c-475f58d7d47a

We need to identify the C2. Click the Connections tab near the bottom of the VM viewport. Next, filter for "Zoom". We can guess that the Oyster file is a file with "zoom" in the name. Observe that it connects to the domain lorrieobrien[.]com.

## Analyze the C2 Domain

Let's repeat what we've done many times already. Search for the domain in urlscan. The link to the search is pasted below.

https://urlscan.io/search/#lorrieobrien.com

I selected the scan result below for analysis.

https://urlscan.io/result/0199ab40-315b-734e-96fc-2de3076fa488/

View the HTTP Transactions tab. The link is below.

https://urlscan.io/result/0199ab40-315b-734e-96fc-2de3076fa488/#transactions

Spoiler alert, this is a unique response that appears to be only used with this infrastructure. 

## Pivot on the Pattern

We can search for this pattern by searching for the hash. The link is below.

https://urlscan.io/search/#hash%3A4176caf548e995285c2f32701426289a0fefc21fd427a4c2c6164282fa04bba0

Observe the domains from the results. Observe that they were all scanned for the the /reg route.

Add the new indicators to the tables...............

## Action the New Indicators

... take the domain indicator from the results...
... search it in Any Run.... take tedbutz[.]com for example. It reveals other  indicators...