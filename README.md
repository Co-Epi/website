# CoEpi: Community Epidemiology In Action

[Home page](https://co-epi.github.io/website/) | [Manual #CoEpi](manual.md) | [Initial conceptual design schematic](documents/flu-smart/FluSmart_Visio.pdf) | [Tech Questions](tech-questions.md) | [Other ideas](webapp-poc.md)

## A COVID pandemic is nearly inevitable
As COVID-19 transitions from epidemic to pandemic, and responses transition from containment to mitigation, the question arises: “What can we do?” As public health authorities scramble to trace contacts, ensure health systems are prepared, and even begin to implement wider social distancing measures as outbreaks spread, the advice to individuals remains simple: scrub down your hands with soap after touching surfaces, stay home from work or school if sick, etc. This is good advice, but leaves open the question of when it’s appropriate to take more disruptive action to reduce transmission risk.

## What can you do?
COVID-19 is here, in our communities, and people are dying. You, yes everyone, can start taking action today to slow the spread of #coronavirus. This isn't normally true, but in this crisis you, personally, can save at least one life by putting #CoEpi, Community Epidemiology, into Action, and talking to everyone to know about your own symptoms, asking about theirs, and being extra vigilant when you're symptomatic or exposed, to prevent the transmission of contagious illnesses, break the chains of COVID-19 coronavirus transmission, and ultimately save the life of a parent, grandparent, or vulnerable relative of someone in your community. [Here's how to start](manual.md)

## What can we do together?
The CoEpi project attempts to bridge the gap between governmental public health actions and individual attention to hygiene. We believe it is possible to combine modern smartphone technology and cloud computing to empower individuals and their personal networks to automatically and anonymously track their own contacts, and inform themselves and their friends and family about increased infection risks. This will allow individuals to make informed risk-based decisions about when it’s most important to implement additional social distancing measures above and beyond the measures being recommended community-wide. It will also enable communities with active community transmission to track and quarantine chains of infection remotely and at scale.  Other communities will achieve earlier, and more complete detection when COVID arrives.  Through digital interaction, personal contact and risks are decreased, and frontline medical resources are reserved for individuals that truly require emergency medical care.

## The CoEpi team
The CoEpi team currently consists of a small group of individuals with diverse and relevant skills who feel the need to put those skills to use in service of our own loved ones, our broader social networks, our communities, and humanity. We are committed to working openly and transparently, publishing all of our work completely open-source for anyone to use in any way they can, to make sure we are all doing everything we can to minimize the death and disruption caused by the COVID-19 pandemic.

## We need your help
We are already starting on building the CoEpi app described below. We have a very solid initial design, and have recruited individuals who can begin producing a minimum viable product. But we can’t move fast enough on our own. If you’re someone with skills and time you could use to help, please get in touch with us immediately: every day it takes us to ramp up development is another day that people are dying. If you don’t have the ability to help out directly, please share this with anyone you know who might be able to, or who might know others who could help. If you have connections at a company who might be able to commit people to helping on this open source project, either by working with us or doing something similar internally, please reach out to them and let them know how urgent it is and how much of a difference they could make.

Currently, we are seeking:
* ReactNative mobile development expertise
* Backend experience with rails/postgres/Heroku

If you're someone who would like to test the early version of the #CoEpi app (or if you have other skills to volunteer), fill out [this form](https://forms.gle/MLeKz9nerPvX8fwC8).

## The CoEpi app: vision
To fully unleash the power of community epidemiology (CoEpi), we are creating an app that empowers people to leverage their personal social network for better awareness of granular infection risks.

The CoEpi app will have utmost regard for personal privacy and will ask for permission when any sharing of sensitive data is needed.  It will only ask individuals to contribute their private data for the good of their community if they become unwell; even when this occurs, the system is designed to permit only the minimum necessary information to be revealed, such that the actual identity of the volunteer participants is maximally concealed.

The CoEpi mobile app will ask permission for everything it does, and will allow individuals to:
* simply install the app to get started, without disclosing any personal information.
* enable or disable tracking their own location history (only locally on their own device), with the ability to enable or disable such tracking on a scheduled, geofenced, or manual basis to avoid collecting any sensitive information the user would never wish to share.
* enable or disable on-demand or background scanning for other devices nearby using Bluetooth Low Energy (BLE), and recording (only on the local device) the history of other devices seen by the app.
* enable or disable contextual hygiene reminders, for example to remind them to wash or sanitize hands when arriving at a new location like home or work, and/or after contact with large numbers of people, as indicated by a significant number of other BLE devices being in range for a significant period of time.  
* produce a report on the device which shows a timeline of personal location history, likely as either a timeline or  a map.  This report should be able to be emailed or printed on user request.  The use case of this information is in its application to individual health care, and in manual contact tracing activity should an individual wish to still contribute to community good after diagnosis but decline to use the networked methodology below.
* be alerted when other CoEpi users come into close range for an extended period of time, and if both users consent, allow them to register a close-contact connection between the devices, allowing either user to preferentially share more information with trusted close contacts than with acquaintances.
* track their own respiratory or gastrointestinal symptoms. When tracking symptoms, the app will optionally prompt the user for additional updates on symptom progression, providing the user with a comprehensive illness history if the symptoms progress to the point of requiring medical attention.
* consent to share any symptoms/results with close contacts, weaker recent contacts, second-degree contacts, future first and/or second-degree contacts, and/or public health officials.
* be alerted, via push notification or by periodic anonymous polling, when another CoEpi user who has shared symptoms was nearby at any point when they may have been contagious.
* invite anyone to begin using the app (and optionally, register as a close contact) via text message, email, QR code, custom shareable URL, etc. Users would be encouraged to invite people in their own social network, as the app will be most useful when the people you’re most likely to be sharing germs with are using it.

Community application of this system will allow visualisation of the distribution of suspected and actual cases of all respiratory and GI illnesses being actively transmitted in the community, most notably COVID-19. In partnership with local public health officials, it could be used to inform community control actions such as travel restrictions and voluntary quarantine.  Global application of this system would dramatically improve the data that is made available to decision makers.
 
In the future, if successful this system could be re-used for more effective control of existing transmissible infectious diseases such as influenza and measles, as well as future pandemic diseases.

## Symptom reporting and sharing

Once fully integrated with secure and anonymous cloud APIs, the full power of CoEpi will come from the ability to report and share symptoms, and perform automatic real-time contact matching and tracing at scale. Here’s how it would work from a user’s perspective:

When a user enters any symptoms or abnormal results, they will be asked to report the recollected date/time of symptom onset, the current severity of symptoms, from minimal to severe, the type of symptoms, and any additional details required based on the previous answers. They’ll then be prompted to choose whether to share full or partial symptom details for the benefit of others. They can choose to share with close contacts, and/or with weaker recent contacts, second-degree contacts, future first and/or second-degree contacts, and/or public health officials.
* Close contacts would be already-registered in-person contacts as described above.
* Weaker contacts would be any other CoEpi users whose BLE identifiers (IDs) have been observed by the affected user’s app while potentially infectious, even if it didn’t result in a close contact registration.
* Second-degree contacts are all CoEpi users who subsequently (within X hours) came in range of a BLE ID that the affected user was nearby while potentially infectious.
* Future contacts would be all CoEpi users who come in range of the affected user during the period when they might remain infectious, and optionally any second-degree contacts who come in range (within X hours) of a BLE ID that the affected user comes nearby.
* Public health officials (and potentially epidemiological researchers) could choose to receive anonymized symptom reports from CoEpi users who optionally choose to share them. If the individual wishes to participate, the app could additionally request permission to upload approximate locations visited during each time period for public health purposes.  This approximation could be done by converting the GPS coordinates to a geohash, for example the 5 character precision with a reported accuracy of +/- 2.4km.  

Any reports of severe symptoms will be prompted and advised how to immediately contact local health services for advice on when/how to engage with the healthcare system. Reports of severe symptoms shared with contacts will be provided only on general terms. If a user reports having received an official diagnosis or having required hospitalization, that information will only be shared with public health officials, so they can link the patient’s CoEpi record with their official medical records as needed, and choose whether/how to perform any contact tracing or otherwise alert/contact any CoEpi users with contact matches.

## Contact matching and alerting
When a contact of a potentially infectious CoEpi user is notified of the fact, they’ll be told about the details of the symptoms reported so far, the date/time/place of their contact with the potentially affected user (or second-degree exposure), whether or not the person is a registered close contact, and they’ll be provided with guidance as to actions they should take: being on the lookout for symptoms, extra attention to hygiene, etc. For more dangerous symptoms consistent with COVID or influenza, they may also receive recommendations to begin practicing social distancing measures, working from home if possible, etc., and instructions on how to call their healthcare providers for guidance on what to do next.
The user will then be able to optionally enable periodic check-ins where the app will ask the user to report any symptoms they’ve noticed, what if anything they’re doing to reduce possible re-transmission, and will prompt the user to consent to share that information with other CoEpi users and/or public health officials if appropriate.

## Completely free and open source
The CoEpi app and server code will be completely open-source and free to use.

There will be a main publicly-available server run by the CoEpi community to handle new app registration, symptom and test reporting, etc. This server will endeavor not to retain any PII from individuals. Client IP addresses will not be stored in a database or recorded in log files any longer than necessary. Phone numbers and email addresses will not be linked to the user in any way. There will be no “user accounts” on the server with usernames and passwords: if someone gets a new phone, they’ll need to re-register all their close contacts the next time they come in contact.

Anyone who doesn’t trust the community-run server, or who wants to run their own for any other reason, can run their own server and invite people in their social network to (also) use that one. Anyone can read from multiple servers, and choose one or more of those servers to submit symptoms/tests to. We may choose to implement FHIR integration or similar to allow health systems to run their own server so patients can choose to report symptoms to and receive test results from the hospital’s EHR.

## How can you help with CoEpi?
We need lots of help to get this project going quickly - we especially need people right now with mobile app development experience (ReactNative), and also folks experienced with building scalable cloud applications with backend data stores and flexible container-based front ends, to help get #CoEpi off the ground as fast as possible. 

If you’re interested in diving in on this project, and have any idea of how you could help, please reach out to [Dana](https://twitter.com/danamlewis) and [Scott](https://twitter.com/scottleibrand), and we can get you connected to the group. 
If you're someone who would like to test the early version of the #CoEpi app (or if you have other skills to volunteer), fill out [this form](https://forms.gle/MLeKz9nerPvX8fwC8).

And finally, as noted above, if you don’t have the ability to help out directly, please share this with anyone you know who might be able to, or who might know others who could help. If you have connections at an organization who might be able to commit people to helping on this, either by working with us or doing something similar internally, please reach out to them and let them know how urgent it is and how much of a difference they could make.
