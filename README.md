## A COVID pandemic is nearly inevitable

As COVID-19 transitions from epidemic to pandemic, and responses transition from containment to mitigation, the question arises: “What can we do?” As public health authorities scramble to trace contacts, ensure health systems are prepared, and even begin to implement wider social distancing measures as outbreaks spread, the advice to individuals remains simple: scrub down your hands with soap after touching surfaces, stay home from work or school if sick, etc. This is good advice, but leaves open the question of when it’s appropriate to take more disruptive action to reduce transmission risk.

## What can we do?

The CoEpi project attempts to bridge the gap between governmental public health actions and individual attention to hygiene. We believe it is possible to use modern smartphone technology, including Bluetooth Low Energy and Location Services, to empower individuals and their personal networks to automatically and anonymously track their own contacts, and inform themselves and their friends and family about increased infection risks. This will allow individuals to make informed risk-based decisions about when it’s most important to implement additional social distancing measures above and beyond the measures being recommended community-wide.

## Proof of Concept

As an initial proof of concept, we should build a website that allows users to get tailored information, specific to their location and/or social network, about their level of potential exposure as well as suggestions for hygiene, social distancing, or self-isolation measures appropriate to their location/history. 
* Allow people to enter a location of interest, and see on a map the nearest publicly known locations of community transmission.
* Allow people to cross-check their location history exported from Google Maps (or another app) against known (public) locations of community transmission.
  * Location history export can be processed locally in-browser without uploading for full privacy.
  * If users want to trade privacy for the convenience and reassurance of proactive notifications, we could allow them to upload a list of locations (perhaps without detailed timestamps, to preserve some privacy) so that any new community transmission locations generate an alert to anyone who’s been there recently. Then they can re-run the local processing against the public data feeds to get details on how likely they were to have been exposed.
  
## The CoEpi app

To fully unleash the power of community epidemiology (CoEpi), we should create an app that empowers people to leverage their personal social network for better awareness of granular infection risks.
* The CoEpi phone app would allow individuals to register their phone, disclosing only their age and gender (to be consistent with how public reports on COVID cases are disclosed) or their first name (for people concerned with their contacts knowing their age).
* The CoEpi app would run a continuous scan in the background for strong BLE signals, record unique identifier of each discovered device, along with the and timestamp of strongest signal and/or timeframe over which signal was seen. (Precise details TBD based on iOS/Android power limitations.)
* If two CoEpi apps come in range, they would both ask their users if they want to add a close contact. If both users say yes, they would each receive the age+gender/name of the other user, and register their contact’s hashed identifier.
* Users would be able to enter possible infectious diseases symptoms (respiratory, GI, etc., including everything from mild cold symptoms up to ICU admission) into the app, noting timeframes, severity, etc., as well as any official diagnoses or test results received via the healthcare system or via self-testing (temperature, pulse-ox, etc.).
* When they enter any symptoms or abnormal results, they would be prompted to choose whether to share full or partial details with close contacts, weaker recent contacts, second-degree contacts, future first and/or second-degree contacts, and/or public health officials.
  * Close contacts would be already-registered in-person contacts as described above.
  * Weaker contacts would be any other CoEpi users whose MAC addresses have been observed by the affected user’s app while potentially infectious, even if it didn’t result in a close contact registration.
  * Second-degree contacts are all CoEpi users who subsequently (within X hours) came in range of a MAC address that the affected user was nearby while potentially infectious.
  * Future contacts would be all CoEpi users who come in range of the affected user during the period when they might remain infectious, and optionally any second-degree contacts who come in range (within X hours) of a MAC address that the affected user comes nearby.
  * Public health officials (and potentially epidemiological researchers) could choose to receive anonymized symptom reports from CoEpi users who choose to share them.
  * For hospitalizations, test results, etc. we’ll want to implement validation mechanisms to prevent malicious users from spamming second-degree contacts with false information.
* When a contact of a potentially infectious CoEpi user is notified of the fact, they’ll be told about the details of the symptoms/results available so far, the date/time/place of their contact with the potentially affected user (or second-degree exposure), their age+gender/name if it’s a close contact, and will be provided with guidance as to actions they should take: being on the lookout for symptoms, extra attention to hygiene, etc. For more dangerous symptoms consistent with COVID or influenza, they may also receive recommendations to begin practicing social distancing measures, working from home if possible, etc., and instructions on how to call their healthcare providers for guidance on what to do next.
* When information about COVID cases and clusters becomes public, any location information disclosed would be imported into the CoEpi server and used to notify CoEpi users who may be at general risk, even if no information is available about specific first and second-degree contacts. Partnerships could also be established with public health agencies to allow publication through a CoEpi server of additional detailed location-exposure data for known COVID cases who aren’t using CoEpi.
* CoEpi users can invite anyone to begin using the app (and optionally, register as a close contact) via text message, email, custom shareable URL, etc. They would be encouraged to invite people in their own social network, as the app will be most useful when the people you’re most likely to be sharing germs with are using it.
* There will be a main publicly-available server run by the CoEpi community to handle MAC address registration, symptom and test reporting, etc. This server will endeavor not to retain any PII from individuals. Client IP addresses will not be stored in a database or recorded in log files any longer than necessary. Phone numbers and email addresses will not be linked to the user in any way. There will be no “user accounts” on the server with usernames and passwords: if someone gets a new phone, they’ll need to re-register all their close contacts the next time they come in contact.
* The CoEpi app and server code will be completely open-source. Anyone who doesn’t trust the community-run server, or who wants to run their own for any other reason, can run their own server and invite people in their social network to (also) use that one. Anyone can read from multiple servers, and choose one or more of those servers to submit symptoms/tests to. We may choose to implement FHIR integration or similar to allow health systems to run their own server so patients can choose to report symptoms to and receive test results from the hospital’s EHR.

## Do we really need a CoEpi app, even if we manage to contain COVID in some countries?

We’re designing CoEpi to be useful for reducing the spread of all infectious diseases, not just COVID. If widely used, CoEpi could meaningfully reduce many types of transmissible diseases, including respiratory infections like influenza and the common cold, and GI diseases like norovirus, rotovirus, etc., commonly referred to as “the stomach flu”. Widespread community adoption of CoEpi will increase communication within families, social networks, and communities with regards to multiple types of transmissible illnesses. Limiting these other transmissions may also make it easier to spot, contain, and treat outbreaks of COVID or new emerging viruses, would save resources to treat those most critically ill; and could directly save some of the tens of thousands of lives lost every year to flu complications.

## What else can individuals and families do?

Here are some of the other things individuals and communities should be doing to prepare for a COVID-19 pandemic.
* Read this article [https://virologydownunder.com/past-time-to-tell-the-public-it-will-probably-go-pandemic-and-we-should-all-prepare-now/](https://virologydownunder.com/past-time-to-tell-the-public-it-will-probably-go-pandemic-and-we-should-all-prepare-now/) and follow its advice, including the following:
  * Try to get a few extra months’ worth of prescription meds, if possible. 
  * Think through now how we will take care of sick family members while trying not to get infected. 
  * Cross-train key staff at work so one person’s absence won’t derail your organization’s ability to function.
  * Practice touching our faces less.
  * Replace handshakes with elbow-bumps. 
  * Start building harm-reduction habits like pushing elevator buttons with a knuckle instead of a fingertip. 

* Get your flu shot: if you get a serious case of flu and then catch COVID (possibly while in the hospital for flu) that dramatically increases your chances of dying from the coinfection: [https://twitter.com/V2019N/status/1231604410502897664](https://twitter.com/V2019N/status/1231604410502897664)
* Don’t book flights or non-refundable hotels more than a few weeks in the future: travel is likely to be seriously disrupted over the next few months as conferences etc. are shut down to minimize COVID transmission. 
* If you are planning a community event, party, gathering, conference, in-person meeting, etc. for either personal or professional reasons, try to keep your plans flexible. Determine whether it’d be possible to reschedule the event for later in the year or next year, and understand when you’d need to make such a decision to avoid excessive cost or disruption. If possible, also consider converting to a virtual event; or otherwise using a different format to achieve the goals of the event. 

