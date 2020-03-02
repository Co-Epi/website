# [CoEpi Community Epidemiology Project](index.md)

[Home page](https://co-epi.github.io/website/) | [Manual #CoEpi](diy.md) | [Initial conceptual design schematic](documents/flu-smart/FluSmart_Visio.pdf) | [Tech Questions](tech-questions.md) | [Other ideas](webapp-poc.md)

## Tech questions and preliminary research notes

If you're reading this, please contribute as well! If you can think of any technical questions, answers, or comments on how CoEpi would work, no matter how "dumb" you think they are, please PR them below (click the View on GitHub button above, then click the little Edit icon that looks like a pencil).

## iOS App
* Can apps stay in BT/wifi listen mode and get MAC addresses seen (like bluez does)?
  * <https://developer.apple.com/library/archive/documentation/NetworkingInternetWeb/Conceptual/CoreBluetooth_concepts/CoreBluetoothBackgroundProcessingForIOSApps/PerformingTasksWhileYourAppIsInTheBackground.html>
  * <https://scribles.net/enabling-background-ble-scanning-on-iphone/>
  * “Passing nil to perform a wild card scan is not supported in the background.” - <https://medium.com/@cbartel/ios-scan-and-connect-to-a-ble-peripheral-in-the-background-731f960d520d>
* Is it possible to wake the app to do more extensive scanning on Significant Location Change? <https://developer.apple.com/documentation/corelocation/getting_the_user_s_location/using_the_significant-change_location_service>
  * Possibly yes, according to <https://developer.apple.com/documentation/corelocation/getting_the_user_s_location/handling_location_events_in_the_background> (if Background App Refresh is enabled, per <https://medium.com/@calvinlin_96474/ios-11-continuous-background-location-update-by-swift-4-12ce3ac603e3>)
* Is it possible to extend background location processing after an application wake event (for example on Significant Change in Location) to scan for BLE devices for a few minutes before going back to sleep? <https://community.estimote.com/hc/en-us/articles/203914068-Is-it-possible-to-use-beacon-ranging-in-the-background->
### Real-world scanning
I had to fly to SJC on the day they announced the first community transmission in the Bay Area (and immediately home that evening), so I downloaded some BLE scanner apps to see how easy it is to see nearby devices. There are literally 100 devices in range of me on this plane, and about 10 with strong signal from the people sitting nearby. It takes only a couple seconds for the scanner apps to see them. So it shouldn’t take much power for the phone to scan each time the app wakes up, log results, and go back to sleep.

## Android App
(copy of iOS questions for now: modify as we start to explore the options on Android)
* Can apps stay in BT/wifi listen mode and get MAC addresses seen (like bluez does)?
* Is it possible to wake the app to do more extensive scanning on Significant Location Change? 
* Is it possible to extend background location processing after an application wake event (for example on Significant Change in Location) to scan for BLE devices for a few minutes before going back to sleep?
