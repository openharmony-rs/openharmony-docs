# @ohos.screenLock

systemScreenLock

@namespace screenLock

**Since:** 7

**System capability:** SystemCapability.MiscServices.ScreenLock

## Modules to Import

```TypeScript
import { screenLock } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [isScreenLocked](arkts-basicservices-screenlock-isscreenlocked-f.md) | Checks whether the screen is currently locked. |
| [isScreenLocked](arkts-basicservices-screenlock-isscreenlocked-f.md) | Checks whether the screen is currently locked. |
| [isSecureMode](arkts-basicservices-screenlock-issecuremode-f.md) | Checks whether the screen lock of the current device is secure. |
| [isSecureMode](arkts-basicservices-screenlock-issecuremode-f.md) | Checks whether the screen lock of the current device is secure. |
| [unlockScreen](arkts-basicservices-screenlock-unlockscreen-f.md) | Unlock the screen. |
| [unlockScreen](arkts-basicservices-screenlock-unlockscreen-f.md) | Unlock the screen. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getScreenLockAuthState](arkts-basicservices-screenlock-getscreenlockauthstate-f-sys.md) | Obtain the screen lock authentication state for os account local userId. |
| [getStrongAuth](arkts-basicservices-screenlock-getstrongauth-f-sys.md) | Obtain strong authentication reason flags for os account local userId. |
| [getUnlockPolicy](arkts-basicservices-screenlock-getunlockpolicy-f-sys.md) | Obtains the authentication policy used to unlock the screen. |
| [isDeviceLocked](arkts-basicservices-screenlock-isdevicelocked-f-sys.md) | Check whether the device is currently locked and the screenlock requires an identity to authenticate and unlock. |
| [isLocked](arkts-basicservices-screenlock-islocked-f-sys.md) | Checks whether the screen is currently locked. |
| [isScreenLockDisabled](arkts-basicservices-screenlock-isscreenlockdisabled-f-sys.md) | Check whether screen lock is disabled for os account local userId. |
| [lock](arkts-basicservices-screenlock-lock-f-sys.md) | Lock the screen. |
| [lock](arkts-basicservices-screenlock-lock-f-sys.md) | Lock the screen. |
| [onSystemEvent](arkts-basicservices-screenlock-onsystemevent-f-sys.md) | Register system event related to screen lock service. |
| [requestStrongAuth](arkts-basicservices-screenlock-requeststrongauth-f-sys.md) | Request strong authentication for os account local userId. |
| [sendScreenLockEvent](arkts-basicservices-screenlock-sendscreenlockevent-f-sys.md) | The screen lock app sends the event to the screen lock service. |
| [sendScreenLockEvent](arkts-basicservices-screenlock-sendscreenlockevent-f-sys.md) | The screen lock app sends the event to the screen lock service. |
| [setScreenLockAuthState](arkts-basicservices-screenlock-setscreenlockauthstate-f-sys.md) | Set the screen lock authentication state for os account local userId. |
| [setScreenLockDisabled](arkts-basicservices-screenlock-setscreenlockdisabled-f-sys.md) | Disable screen lock showing for os account local userId. This only becomes effective when there is no password. |
| [unlock](arkts-basicservices-screenlock-unlock-f-sys.md) | Unlock the screen. |
| [unlock](arkts-basicservices-screenlock-unlock-f-sys.md) | Unlock the screen. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [SystemEvent](arkts-basicservices-screenlock-systemevent-i-sys.md) | Indicates the system event type and parameter related to the screenlock management service. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [AuthState](arkts-basicservices-screenlock-authstate-e-sys.md) | Indicates the screen lock authentication state. |
| [StrongAuthReasonFlags](arkts-basicservices-screenlock-strongauthreasonflags-e-sys.md) | Indicates the strong authentication reason flags used to request. |
| [UnlockPolicy](arkts-basicservices-screenlock-unlockpolicy-e-sys.md) | Indicates the screen lock authentication policy used to unlock the screen. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [EventType](arkts-basicservices-screenlock-eventtype-t-sys.md) | Indicates the system event type related to the screen lock management service. Added unlockPolicyChanged. |
<!--DelEnd-->
