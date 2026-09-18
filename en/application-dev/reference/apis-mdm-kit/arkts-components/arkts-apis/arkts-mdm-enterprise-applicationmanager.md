# @ohos.enterprise.applicationManager(Application Management)

This module provides application management capabilities, including managing the application running blocklist, application running trustlist, auto-startup application list, keep-alive application list, non-stoppable application list, background freeze-exempt application list, notification trustlist, and cross-device application trustlist. It is suitable for enterprise device management scenarios, enabling control over application running permissions, auto- startup management, keep-alive application management, and more, thereby enhancing enterprise device security and compliance.

> **NOTE:** 
> 
> The APIs of this module can be called only by a device administrator application that is enabled. For details, see
> [MDM Kit Development](../../../mdm/mdm-kit-guide.md). The
> [applicationManager.isAppKioskAllowed](arkts-mdm-applicationmanager-isappkioskallowed-f.md) API is available to all
> applications.

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addAllowedDistributeAbilityConnBundles](arkts-mdm-applicationmanager-addalloweddistributeabilityconnbundles-f.md) | Adds the cross-device application trustlist for a specific distributed service for a specified user. Applications in the trustlist can use the specific distributed service to transfer data across devices without being subject to the restrictions imposed by [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md). |
| [addAllowedNotificationBundles](arkts-mdm-applicationmanager-addallowednotificationbundles-f.md) | Adds applications to the notification trustlist. After the notification trustlist is set, applications not in the trustlist cannot send notifications. |
| [addAllowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md) | Adds applications to the application running trustlist. Only applications in the trustlist are allowed to run under the specified user. |
| [addAutoStartApps](arkts-mdm-applicationmanager-addautostartapps-f.md) | Adds the auto-start applications for the current user. Applications added to the auto-start list via this API cannot be manually disabled for auto-start by users on the device. However, they can be removed from the auto-start list using the [removeAutoStartApps](arkts-mdm-applicationmanager-removeautostartapps-f.md) API. |
| [addAutoStartApps](arkts-mdm-applicationmanager-addautostartapps-f.md) | Adds a list of applications that automatically start upon device startup for a specified user, and sets whether to prohibit the user from manually canceling application auto-start. |
| [addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md) | Adds applications to the application running blocklist. Applications added to the blocklist are not allowed to run under the current or specified user. Since API version 21, if the application running trustlist [addAllowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md) is not empty, the application running blocklist cannot be added via this API. Otherwise, the error code 9200010 is reported. |
| [addDockApp](arkts-mdm-applicationmanager-adddockapp-f.md) | Adds an application to the bottom shortcut bar of a PC/2-in-1 device based on the location index. Then users can tap the application icon in the shortcut bar to directly launch the application. The application icon is the default icon displayed on the home screen. |
| [addFreezeExemptedApps](arkts-mdm-applicationmanager-addfreezeexemptedapps-f.md) | Adds applications to the background freeze-exempt application list for a specified user. This policy applies only to installed applications. If the parameter list contains uninstalled applications, error code 9200012 will be returned. If an application in the list is uninstalled after the policy is set, the uninstalled application will be removed from the list. Adding an application that already exists in the list will return success, but the application will not be added repeatedly to the policy list. |
| [addHideLauncherIcon](arkts-mdm-applicationmanager-addhidelaunchericon-f.md) | Adds applications to the home screen icon hide list. |
| [addKeepAliveApps](arkts-mdm-applicationmanager-addkeepaliveapps-f.md) | Adds applications to the keep-alive list; once added, the application processes will be kept alive automatically. After the device is powered on or the application is killed, the system will proactively restart these application processes. |
| [addKeepAliveApps](arkts-mdm-applicationmanager-addkeepaliveapps-f.md) | Adds applications to the keep-alive list; once added, the application processes will be kept alive automatically. You can also set whether to disable manual keep-alive cancellation. After the device is powered on or the application is killed, the system will proactively restart these application processes. |
| [addUserNonStopApps](arkts-mdm-applicationmanager-addusernonstopapps-f.md) | Adds applications to the non-stoppable application list for a specified user. This policy only applies to installed applications. If the parameter list contains uninstalled applications, error code 9200012 will be returned. If an application in the list is uninstalled after the policy is set, the uninstalled application will be removed from the list. Adding an application that already exists in the list will return success, but the application will not be added repeatedly to the policy list. |
| [clearUpApplicationData](arkts-mdm-applicationmanager-clearupapplicationdata-f.md) | Clears all application data. |
| [getAllowedDistributeAbilityConnBundles](arkts-mdm-applicationmanager-getalloweddistributeabilityconnbundles-f.md) | Obtains the cross-device application trustlist for a specific distributed service under a specified user. |
| [getAllowedKioskApps](arkts-mdm-applicationmanager-getallowedkioskapps-f.md) | Obtains the applications allowed to run in kiosk mode. |
| [getAllowedKioskApps](arkts-mdm-applicationmanager-getallowedkioskapps-f.md) | Obtains the applications allowed to run in kiosk mode. |
| [getAllowedNotificationBundles](arkts-mdm-applicationmanager-getallowednotificationbundles-f.md) | Obtains the list of applications that are allowed to send notifications. |
| [getAllowedRunningBundles](arkts-mdm-applicationmanager-getallowedrunningbundles-f.md) | Obtains the list of applications allowed to run by a specified user. |
| [getAllowedRunningBundles](arkts-mdm-applicationmanager-getallowedrunningbundles-f.md) | Obtains the application running trustlist of a specified user. |
| [getApplicationWindowStates](arkts-mdm-applicationmanager-getapplicationwindowstates-f.md) | Queries the window state information list of the specified application. It can retrieve information such as whether the application is in the bottom dock and whether the application window is currently displayed in the foreground. |
| [getAutoStartApps](arkts-mdm-applicationmanager-getautostartapps-f.md) | Checks the auto-start applications for the current user. |
| [getAutoStartApps](arkts-mdm-applicationmanager-getautostartapps-f.md) | Checks the auto-start applications for the current user. |
| [getAutoStartApps](arkts-mdm-applicationmanager-getautostartapps-f.md) | Checks the auto-start applications for the specified user. |
| [getAutoStartApps](arkts-mdm-applicationmanager-getautostartapps-f.md) | Checks the auto-start applications for the specified user. |
| [getDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-getdisallowedrunningbundlessync-f.md) | Obtains applications that are not allowed to run by the current user or specified user. |
| [getDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-getdisallowedrunningbundlessync-f.md) | Obtains the application running blocklist of the current user or specified user. |
| [getDockApps](arkts-mdm-applicationmanager-getdockapps-f.md) | Obtains the list of applications in the shortcut bar currently. |
| [getFreezeExemptedApps](arkts-mdm-applicationmanager-getfreezeexemptedapps-f.md) | Obtains the background freeze-exempt application list of all users on the current device. |
| [getFreezeExemptedApps](arkts-mdm-applicationmanager-getfreezeexemptedapps-f.md) | Obtains the background freeze-exempt application list of all users on the current device. |
| [getHideLauncherIcon](arkts-mdm-applicationmanager-gethidelaunchericon-f.md) | Queries the list of applications whose home screen icons are hidden for the current user. |
| [getKeepAliveApps](arkts-mdm-applicationmanager-getkeepaliveapps-f.md) | Obtains the bundle name of the keep-alive application. |
| [getKeepAliveApps](arkts-mdm-applicationmanager-getkeepaliveapps-f.md) | Obtains the bundle name of the keep-alive application. |
| [getUserNonStopApps](arkts-mdm-applicationmanager-getusernonstopapps-f.md) | Obtains the non-stoppable application list of all users on the current device. |
| [getUserNonStopApps](arkts-mdm-applicationmanager-getusernonstopapps-f.md) | Obtains the non-stoppable application list of all users on the current device. |
| [isAbilityDisabled](arkts-mdm-applicationmanager-isabilitydisabled-f.md) | Checks whether the Ability component of a specified application (system application or third-party application) is disabled. |
| [isAbilityDisabled](arkts-mdm-applicationmanager-isabilitydisabled-f.md) | Checks whether the Ability component of a specified application (system application or third-party application) is disabled. |
| [isAppKioskAllowed](arkts-mdm-applicationmanager-isappkioskallowed-f.md) | Checks whether an application is allowed to run in kiosk mode. |
| [isModifyAutoStartAppsDisallowed](arkts-mdm-applicationmanager-ismodifyautostartappsdisallowed-f.md) | Checks whether a specified user is prohibited from canceling application auto-start. |
| [isModifyKeepAliveAppsDisallowed](arkts-mdm-applicationmanager-ismodifykeepaliveappsdisallowed-f.md) | Checks whether the application is forbidden to cancel the keep-alive status. |
| [publishFormToDesktop](arkts-mdm-applicationmanager-publishformtodesktop-f.md) | Publishes the form to the desktop. |
| [queryBundleStatsInfos](arkts-mdm-applicationmanager-querybundlestatsinfos-f.md) | Queries the accumulated foreground runtime statistics of applications under a specified user account within a given time period. The minimum query granularity is one day. The API requires the start time (**startTime**), end time (**endTime**), and target user account ID (**accountId**) to be passed in. **startTime** and **endTime** are millisecond-level timestamps. The caller can pass custom values. The default value of **startTime** is 00:00:00.000 of the current day, and the default of **endTime** is 24:00:00.000 of the current day (that is, 00:00:00 of the following day). The API returns an array of **BundleStatsInfo**, where each element contains the bundle name of an application, its clone index, and the foreground usage duration (in milliseconds) within the specified time period. If **startTime** is set to **0**, the query starts from the device's first boot time. If **startTime** is later than **endTime**, the API returns error code 9200012. |
| [queryTrafficStats](arkts-mdm-applicationmanager-querytrafficstats-f.md) | Queries the data usage of a specified application within a specified period for the current user. This API uses a promise to return the result. |
| [removeAllowedDistributeAbilityConnBundles](arkts-mdm-applicationmanager-removealloweddistributeabilityconnbundles-f.md) | Removes the cross-device application trustlist for a specific distributed service for a specified user. After the trustlist is removed, if there are still remaining applications in the list, only those applications can use the specific distributed service to transmit data across devices without being subject to the restrictions imposed by [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md). If the list has been removed and there are no remaining applications, no applications under the specified user are allowed to use the specific distributed service for cross-device data transmission. |
| [removeAllowedNotificationBundles](arkts-mdm-applicationmanager-removeallowednotificationbundles-f.md) | Removes applications from the notification trustlist. |
| [removeAllowedRunningBundles](arkts-mdm-applicationmanager-removeallowedrunningbundles-f.md) | Removes applications from the application running trustlist of the specified user. After an application is removed, it is not allowed to run under the current or specified user. |
| [removeAutoStartApps](arkts-mdm-applicationmanager-removeautostartapps-f.md) | Removes the auto-start applications for the current user. After the deletion, the applications will no longer automatically start upon system boot. |
| [removeAutoStartApps](arkts-mdm-applicationmanager-removeautostartapps-f.md) | Removes the specified application from the auto-start application list of a specified user. |
| [removeDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-removedisallowedrunningbundlessync-f.md) | Removes applications from the application running blocklist of the current or specified user. After an application is removed, it is allowed to run under the current or specified user. |
| [removeDockApp](arkts-mdm-applicationmanager-removedockapp-f.md) | Removes an application from the shortcut bar. |
| [removeFreezeExemptedApps](arkts-mdm-applicationmanager-removefreezeexemptedapps-f.md) | Removes the background freeze-exempt application list for a specified user. After the removal, the applications can be frozen by the system. If the parameter list includes uninstalled applications, the removal will still succeed. Installed applications will be removed from the list, while uninstalled ones will not impact the removal process. |
| [removeHideLauncherIcon](arkts-mdm-applicationmanager-removehidelaunchericon-f.md) | Removes applications from the home screen icon hide list. |
| [removeKeepAliveApps](arkts-mdm-applicationmanager-removekeepaliveapps-f.md) | Removes a specified application from the keep-alive list. |
| [removeUserNonStopApps](arkts-mdm-applicationmanager-removeusernonstopapps-f.md) | Removes the non-stoppable application list for a specified user. After the removal, the user can stop the applications on the device. If the parameter list includes uninstalled applications, the removal will still succeed. Installed applications will be removed from the list, while uninstalled ones will not impact the removal process. |
| [setAbilityDisabled](arkts-mdm-applicationmanager-setabilitydisabled-f.md) | Sets whether to disable the Ability component of a specified application (system application or third-party application). Currently, only the UIAbility type is supported. After the UIAbility type is disabled, the UI of the Ability component cannot be started. |
| [setAllowedKioskApps](arkts-mdm-applicationmanager-setallowedkioskapps-f.md) | Sets applications allowed to run in kiosk mode. |
| [setKioskFeatures](arkts-mdm-applicationmanager-setkioskfeatures-f.md) | Sets the features of the kiosk mode. You can use this API to control whether the notification center and control panel can be accessed in kiosk mode. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addDisallowedRunningBundles](arkts-mdm-applicationmanager-adddisallowedrunningbundles-f-sys.md) | Adds the applications that are not allowed to run under the current user. This API uses an asynchronous callback to return the result. From API version 21, if the allowed application list [addAllowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md) is not empty, the prohibited application list cannot be added using this API. Otherwise, the error code 9200010 is reported. |
| [addDisallowedRunningBundles](arkts-mdm-applicationmanager-adddisallowedrunningbundles-f-sys.md) | Adds the applications that are not allowed to run under a specified user (specified by **userId**). This API uses an asynchronous callback to return the result. From API version 21, if the allowed application list [addAllowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md) is not empty, the prohibited application list cannot be added using this API. Otherwise, the error code 9200010 is reported. |
| [addDisallowedRunningBundles](arkts-mdm-applicationmanager-adddisallowedrunningbundles-f-sys.md) | Adds the applications that are not allowed to run by the current or specified user. This API uses a promise to return the result. From API version 21, if the allowed application list [addAllowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md) is not empty, the prohibited application list cannot be added using this API. Otherwise, the error code 9200010 is reported. |
| [getDisallowedRunningBundles](arkts-mdm-applicationmanager-getdisallowedrunningbundles-f-sys.md) | Obtains applications that are not allowed to run by the current user. This API uses an asynchronous callback to return the result. |
| [getDisallowedRunningBundles](arkts-mdm-applicationmanager-getdisallowedrunningbundles-f-sys.md) | Obtains an application from the applications that are not allowed to run by the current user (specified by **userId**). This API uses an asynchronous callback to return the result. |
| [getDisallowedRunningBundles](arkts-mdm-applicationmanager-getdisallowedrunningbundles-f-sys.md) | Obtains applications that are not allowed to run under the current user or a specified user. This API uses a promise to return the result. |
| [removeDisallowedRunningBundles](arkts-mdm-applicationmanager-removedisallowedrunningbundles-f-sys.md) | Removes an application from the applications that are not allowed to run under the current user. This API uses an asynchronous callback to return the result. |
| [removeDisallowedRunningBundles](arkts-mdm-applicationmanager-removedisallowedrunningbundles-f-sys.md) | Removes an application from the applications that are not allowed to run under the current user (specified by **userId**). This API uses an asynchronous callback to return the result. |
| [removeDisallowedRunningBundles](arkts-mdm-applicationmanager-removedisallowedrunningbundles-f-sys.md) | Removes applications from the applications that are not allowed to run under the current or specified user. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [BundleStatsInfo](arkts-mdm-applicationmanager-bundlestatsinfo-i.md) | Application bundle statistics. |
| [DockInfo](arkts-mdm-applicationmanager-dockinfo-i.md) | Describes information about an application in the shortcut bar. |
| [FormInfo](arkts-mdm-applicationmanager-forminfo-i.md) | Information about a form. |
| [WindowStateInfo](arkts-mdm-applicationmanager-windowstateinfo-i.md) | Defines the application window state information. |

### Enums

| Name | Description |
| --- | --- |
| [KioskFeature](arkts-mdm-applicationmanager-kioskfeature-e.md) | Defines the features of the kiosk mode. |
| [ServiceType](arkts-mdm-applicationmanager-servicetype-e.md) | Distributed service type. |
| [WindowState](arkts-mdm-applicationmanager-windowstate-e.md) | Enumerates application window states. |
