# About This Kit
<!--Kit: Location Kit-->
<!--Subsystem: Location-->
<!--Owner: @xxthadsl-->
<!--Designer: @liu-binjun-->
<!--Tester: @gcw_MslijYkf-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=c9ba8f78b9508882630beebd38c66c0613ccfa4a translatedAt=2026-11-03T07:13:41.907Z pushedAt=2026-11-03T07:13:41.907Z nl=1 -->

## Overview

People take their mobile devices wherever they go. Mobile devices have become a necessity in people's daily routines, whether it be for looking at the weather forecast, browsing news, hailing a taxi, navigating, or recording data from a workout. All these activities are so much associated with the location services on mobile devices.

With the location awareness capability offered by OpenHarmony, mobile devices will be able to obtain real-time, accurate location data. Building location awareness into your application can also lead to a better contextual experience for application users.

Your application can call location-specific APIs to obtain the location information of a mobile device for offering location-based services such as drive navigation and motion track recording.

### About Location Kit

Location Kit uses multiple positioning technologies, including GNSS, base station positioning, and WLAN/Bluetooth positioning. The latter two are collectively referred to as network positioning. Together, these technologies determine a device's location accurately, whether the device is indoors or outdoors.

- **Coordinate**<br>
  A coordinate describes a location on the earth using the longitude and latitude in reference to the World Geodetic Coordinate System 1984.

- **GNSS positioning**<br>
  GNSS positioning locates a mobile device by using the location algorithm offered by the device chip to compute the location information provided by the Global Navigation Satellite System, for example, GPS, GLONASS, BeiDou, and Galileo. Whichever positioning system will be used during the location process depends on a hardware capability of the device.

- **Base station positioning**<br>
  Base station positioning estimates the current location of a mobile device based on the location of the resident base station in reference to the neighboring base stations. This technology provides only a low accuracy and requires access to the cellular network.

- **WLAN or Bluetooth positioning**<br>
  WLAN or Bluetooth positioning estimates the current location of a mobile device based on the locations of WLANs and Bluetooth devices that can be discovered by the device. The location accuracy of this technology depends on the distribution of fixed WLAN access points (APs) and Bluetooth devices around the device. A high density of WLAN APs and Bluetooth devices can produce a more accurate location result than base station positioning. This technology also requires access to the network.

<!--RP1--><!--RP1End-->

### Constraints

Location awareness is a basic system service for applications. Request location updates when your service scenario begins and stop the request when it ends. While the request is active, the system reports real-time location results to your application.

Your application can use the location function only after the user has granted the required permission and turned on the location function. If the location function is off, the system will not provide the location service for any application.

Since the location information is considered sensitive, your application still needs to obtain the location access permission from the user even if the user has turned on the location function. The system will provide the location service for your application only after it has been granted the permission to access the device location information.

Location Kit provides different capabilities on different devices, and some capabilities depend on hardware support. For example, positioning chips such as GPS or BeiDou provide GNSS positioning. Devices without a positioning chip can still use WLAN or base station positioning if they have WLAN or cellular network access.

<!--RP2--><!--RP2End-->

<!--RP3--><!--RP3End-->

### Samples

The following sample is provided to help you better understand how to use Location Kit:

- [Location: Location Kit (ArkTS) (API14)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ConnectivityKit/Location)
