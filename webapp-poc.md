# [CoEpi Project](index.md)

[Home page](https://co-epi.github.io/website/) | [Manual #CoEpi](diy.md) | [Initial conceptual design schematic](documents/flu-smart/FluSmart_Visio.pdf) | [Tech Questions](tech-questions.md) | [Other ideas](webapp-poc.md)

## Web Proof of Concept

Update: our current thinking is to skip this step and straight to building a minimum viable standalone mobile app. If anyone else would like to implement something along the lines described below, please feel free.

As an initial proof of concept, we could build a website that allows users to get tailored information, specific to their location and/or social network, about their level of potential exposure as well as suggestions for hygiene, social distancing, or self-isolation measures appropriate to their location/history.
* Allow people to enter a location of interest, and see on a map the nearest publicly known locations of community transmission.
* Allow people to cross-check their location history exported from Google Maps (or another app) against known (public) locations of community transmission.
  * Location history export can be processed locally in-browser without uploading for full privacy.
  * If users want to trade privacy for the convenience and reassurance of proactive notifications, we could allow them to upload a list of locations (perhaps without detailed timestamps, to preserve some privacy) so that any new community transmission locations generate an alert to anyone who’s been there recently. Then they can re-run the local processing against the public data feeds to get details on how likely they were to have been exposed.

It looks like we might need some sort of trusted relationship with a public health agency to get any detailed location data on public places visited by COVID-19 cases. In the meantime, we should on making a web app POC of our CoEpi app using a similar anonymous mechanism (albeit with slightly weaker privacy guarantees against reidentification by attackers with access to other surveillance data). Here’s how it’d work:

The web app has two modes: “Report Symptoms” and “Check Exposure”.

### Common elements:
* Both modes accept as input (via a file picker dialog) kml files manually exported from Google Maps’ Timeline feature (https://www.google.com/maps/timeline) by selecting a day of interest and clicking Export this day to KML under the gear icon. 
  * TODO: see if we can generate the list of download URLs to make it easier to get all the days of interest.
  * This works for me, on a Mac with my personal Google account logged in as authuser 0. We should figure out whether there’s a way to reliably do that from within a browser, or at least give people a list of links to click on.
```
    $ for month in 1; do
        for day in $(seq 30 31); do
          /Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome 'https://www.google.com/maps/timeline/kml?authuser=0&pb=!1m8!1m3!1i2020!'$month'i1!3i'$day'!2m3!1i2020!'$month'i1!3i'$day;
        done;
      done
    Opening in existing browser session.
    Opening in existing browser session.
```
* In both modes, javascript running locally on the browser parses the kml and pulls out all the locations visited with a street address in the `<address>` or `<name>` tag, and the `<TimeSpan>` over which the user was there. Initially, the local javascript would only include the TimeSpan records’ date, not specific times, to preserve privacy and allow for less-specific matches. Once enough users in a given city are uploading data, records there could be rounded to hourly granularity instead, to minimize non-time-overlapping matches without risking privacy due to the large number of independent records.
* The user is free to select which locations to upload (to store or just check) vs. which ones to keep locally and not match. Google Maps’ kml exports have the addresses of commercial locations in the `<address>` tag, and residential addresses in the `<name>` tag, so we can select commercial locations for upload by default, unselect the location named Home by default, and visually differentiate / group commercial and residential locations for easy selection and unselection. 
All web server logs containing client IPs are quickly rotated and deleted.

### Report Symptoms mode:
* In “Report Symptoms” mode, the user identifies the set of symptoms from a preselected checklist (including sufficient “other” categories to capture everything we want to allow people to report) selects the date when they first experienced symptoms, and the local javascript shows all the locations and their corresponding timeframes since that date. If the user chooses to unselect any locations, we should inform them that by doing so CoEpi will be unable to inform anyone else who was there of the reported symptoms and let them know they should instead reach out privately to do so.
* Once the user reporting symptoms has selected the locations to upload, the local javascript hashes the addresses (for mild we-promise-not-to-look-inside obscurity, but not true security resistant to a simple brute-force scan of all addresses in the country) and uploads them using TLS to the CoEpi server, which stores each symptoms set + address hash + TimeSpan combination as an independent record keyed by address hash, not associated with any other address + TimeSpan records (or any directly personally identifying information) to help preserve privacy (particularly once more than a few people in a given city are uploading data). No usernames or other PII should be uploaded, and the insertion time of the record should be omitted, to prevent correlation with web server logs containing client IP.
* If a user later reports continuation of the same symptoms set using the original illness start date, the duplicate values would be consolidated into a single record and nothing would change in the database for the already-reported dates. If they report a different (possibly overlapping) set of symptoms with the same original illness start date, the additional symptoms would be added. The end result would likely exist in the DB as an indexable key of the address hash, with values corresponding to the symptom set + TimeSpan combination.

### Check Exposure mode:
* In “Check Exposure” mode, the user selects up to about 2 weeks of kml files, which are locally parsed in the browser and address hashes generated as described above. The hashed addresses and rounded TimeSpans are provided to the server, it looks them up in its database, and any matches found are returned and displayed, along with the reported symptoms that were (later) observed by people present at that location on that date and/or hour. The server does not retain any records of what records were checked or whether or not any records were matched.


## Tech Q&A

### Website POC
* What location data can be exported from Google Maps etc.?
  * Per <https://support.google.com/maps/thread/13214681?hl=en> you can export individual days' data as kml.
  * If you want to export your entire history and then pare it down, <https://webapps.stackexchange.com/questions/97919/turning-google-timeline-into-a-travel-map> has directions for that.
* What has already been done?
  * <http://googlemapsmania.blogspot.com/2020/02/covid-19-maps.html>
