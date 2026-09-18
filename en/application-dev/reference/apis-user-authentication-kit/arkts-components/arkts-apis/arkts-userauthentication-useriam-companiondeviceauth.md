# @ohos.userIAM.companionDeviceAuth(Companion Device Authentication)

The **companionDeviceAuth** module is an important part of the OpenHarmony user identity and access management (UserIAM) system. It is dedicated to companion device authentication management. This module provides the system application with capabilities such as querying and subscribing to companion devices, and managing the service scope.

This module applies to the following scenarios:

- Managing the authentication relationship between a companion device and the primary device.  
- Querying and subscribing to the status changes of a companion device.  
- Managing the service scope supported by a companion device.  
- Implementing continuous authentication.  
- Processing device selection and registration.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getStatusMonitor](arkts-userauthentication-companiondeviceauth-getstatusmonitor-f-sys.md) | Obtains the status monitor. This API is used to obtain the status monitor object of a specified user. The object can be used to query and subscribe to the template status, continuous authentication status, and available device status of the companion device. |
| [registerDeviceSelectCallback](arkts-userauthentication-companiondeviceauth-registerdeviceselectcallback-f-sys.md) | Registers a callback for companion device selection. When the system requires the user to select a companion device, this callback is triggered. The application needs to return the information about the selected device in the callback. Through this callback, the application can implement custom device selection logic, for example, displaying a device selection screen for the user to select a device. |
| [registerPasscodePromptCallback](arkts-userauthentication-companiondeviceauth-registerpasscodepromptcallback-f-sys.md) | Registers the callback invoked when the framework needs a companion device passcode. If a callback has already been registered, the new one replaces it. |
| [unregisterDeviceSelectCallback](arkts-userauthentication-companiondeviceauth-unregisterdeviceselectcallback-f-sys.md) | Unregisters a callback for companion device selection. After the callback is unregistered, the system will no longer invoke the device selection callback registered by the application, and the device selection will fall back to the default system behavior. |
| [unregisterPasscodePromptCallback](arkts-userauthentication-companiondeviceauth-unregisterpasscodepromptcallback-f-sys.md) | Unregisters the callback used to prompt for a companion device passcode. |
| [updateEnabledBusinessIds](arkts-userauthentication-companiondeviceauth-updateenabledbusinessids-f-sys.md) | Updates the service scope supported by the specified companion device template. This API is used to modify the list of service IDs enabled for a registered template, thereby controlling the service scenarios in which the template can be used. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ContinuousAuthParam](arkts-userauthentication-companiondeviceauth-continuousauthparam-i-sys.md) | Defines continuous authentication parameters. They are used to configure parameters related to the subscription to the continuous authentication status, for example, specifying the target template to be subscribed to. |
| [DeviceKey](arkts-userauthentication-companiondeviceauth-devicekey-i-sys.md) | Defines the device service ID. It uniquely identifies a device and its user, including the device ID type, device ID, user ID, and sub-profile ID. |
| [DeviceSelectResult](arkts-userauthentication-companiondeviceauth-deviceselectresult-i-sys.md) | Returns the result of companion device selection. It is used to return the device information and extended context selected by the user in the device selection callback. |
| [DeviceStatus](arkts-userauthentication-companiondeviceauth-devicestatus-i-sys.md) | Defines the device status information. It describes the current status of the companion device, including the device service ID, user name, model information, device name, online status, list of supported service IDs, and device sub-profile name. |
| [PasscodePromptParams](arkts-userauthentication-companiondeviceauth-passcodepromptparams-i-sys.md) | Params carried by the framework when prompting for a companion device passcode. |
| [StatusMonitor](arkts-userauthentication-companiondeviceauth-statusmonitor-i-sys.md) | Status monitor object. It is used to listen for or obtain information such as the template status, continuous authentication status, and available device status. This object can be obtained by calling [getStatusMonitor](arkts-userauthentication-companiondeviceauth-getstatusmonitor-f-sys.md). |
| [TemplateStatus](arkts-userauthentication-companiondeviceauth-templatestatus-i-sys.md) | Describes the complete status information about a registered companion device authentication template, including the template ID, data confirmation status, validity, user ID, time when the template is added, supported services, and associated device status. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [BusinessId](arkts-userauthentication-companiondeviceauth-businessid-e-sys.md) | Enumerates service IDs. A service ID uniquely identifies a service scenario supported by the companion device. The service scenarios supported by different companion devices vary according to the authentication security. For example, executing voice commands without screen unlocking. |
| [DeviceIdType](arkts-userauthentication-companiondeviceauth-deviceidtype-e-sys.md) | Enumerates device ID types. They are used to define the device service identifier type. System-defined types and vendor-defined types are supported. |
| [SelectPurpose](arkts-userauthentication-companiondeviceauth-selectpurpose-e-sys.md) | Selects the purpose of the companion device. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [AvailableDeviceStatusCallback](arkts-userauthentication-companiondeviceauth-availabledevicestatuscallback-t-sys.md) | Defines the callback triggered for receiving notifications of available device status changes. When the list of available devices changes (for example, a new device goes online or a device goes offline), the system notifies the application through this callback. |
| [ContinuousAuthStatusCallback](arkts-userauthentication-companiondeviceauth-continuousauthstatuscallback-t-sys.md) | Defines the callback triggered for receiving notifications of continuous authentication status changes. When the authentication status of a companion device changes, the system applies the current authentication result and authentication reliability level through this callback notification. |
| [DeviceSelectCallback](arkts-userauthentication-companiondeviceauth-deviceselectcallback-t-sys.md) | Defines the callback triggered for the companion device selection. When the system requires the user to select a companion device (for example, when adding a template or performing authentication), this callback is triggered. The application needs to return the information about the selected device. |
| [PasscodePromptCallback](arkts-userauthentication-companiondeviceauth-passcodepromptcallback-t-sys.md) | Defines the callback invoked when the framework needs a passcode for a companion device. |
| [PasscodeSubmitCallback](arkts-userauthentication-companiondeviceauth-passcodesubmitcallback-t-sys.md) | Defines the callback used to submit a passcode entered by the user. |
| [TemplateStatusCallback](arkts-userauthentication-companiondeviceauth-templatestatuscallback-t-sys.md) | Defines the callback triggered for receiving notifications of template status changes. When the template status changes (for example, the template is added, deleted, or its validity changes), the system notifies the application through this callback. |
<!--DelEnd-->
