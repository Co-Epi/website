# Tech questions and preliminary research notes
## Website POC
* What location data can be exported from Google Maps etc.?
  * Per <https://support.google.com/maps/thread/13214681?hl=en> you can export individual days' data as kml.
  * If you want to export your entire history and then pare it down, <https://webapps.stackexchange.com/questions/97919/turning-google-timeline-into-a-travel-map> has directions for that.
## iOS App
* Can apps stay in BT/wifi listen mode and get MAC addresses seen (like bluez does)?
  * <https://developer.apple.com/library/archive/documentation/NetworkingInternetWeb/Conceptual/CoreBluetooth_concepts/CoreBluetoothBackgroundProcessingForIOSApps/PerformingTasksWhileYourAppIsInTheBackground.html>
  * <https://scribles.net/enabling-background-ble-scanning-on-iphone/>
  * “Passing nil to perform a wild card scan is not supported in the background.” - <https://medium.com/@cbartel/ios-scan-and-connect-to-a-ble-peripheral-in-the-background-731f960d520d>
* Is it possible to wake the app to do more extensive scanning on Significant Location Change? <https://developer.apple.com/documentation/corelocation/getting_the_user_s_location/using_the_significant-change_location_service>
  * Possibly yes, according to <https://developer.apple.com/documentation/corelocation/getting_the_user_s_location/handling_location_events_in_the_background> (if Background App Refresh is enabled, per <https://medium.com/@calvinlin_96474/ios-11-continuous-background-location-update-by-swift-4-12ce3ac603e3>)
* Is it possible to extend background location processing after an application wake event (for example on Significant Change in Location) to scan for BLE devices for a few minutes before going back to sleep? <https://community.estimote.com/hc/en-us/articles/203914068-Is-it-possible-to-use-beacon-ranging-in-the-background->
## Android App
(copy of iOS questions for now: modify as we start to explore the options on Android)
* Can apps stay in BT/wifi listen mode and get MAC addresses seen (like bluez does)?
* Is it possible to wake the app to do more extensive scanning on Significant Location Change? 
* Is it possible to extend background location processing after an application wake event (for example on Significant Change in Location) to scan for BLE devices for a few minutes before going back to sleep?
