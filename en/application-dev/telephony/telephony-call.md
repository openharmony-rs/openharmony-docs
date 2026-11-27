# Call Service Development
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @shao-yikai-->
<!--Designer: @wnazgul-->
<!--Tester: @jiang_99-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=a110e197dd55ada77ddf24e68485b5078465980e translatedAt=2026-11-26T02:29:17.446Z pushedAt=2026-11-26T02:44:39.338Z nl=1 -->

## Scenario Description

You can implement the call service in either of the following ways:
<!--Del-->
- For a system application, use the **dialCall** API to make a voice or video call. The call will be displayed on the application page.
<!--DelEnd-->
- For a third-party application, use the **makeCall** API to start the system call application. Users can then make calls as needed.

## Basic Concepts

- Call status code

  A code used to report the current call status to the application, so that the application can then take appropriate logic processing. For example, if there is no ongoing call, the application allows you to make a new call.

  | Name              | Value  | Description                                                        |
  | ------------------ | ---- | ------------------------------------------------------------ |
  | CALL_STATE_UNKNOWN | -1   | The call status fails to be obtained and is unknown.                        |
  | CALL_STATE_IDLE    | 0    | No call is in progress.                                    |
  | CALL_STATE_RINGING | 1    | The call is in the ringing or waiting state.                                    |
  | CALL_STATE_OFFHOOK | 2    | At least one call is in dialing, active, or on hold, and no new incoming call is ringing or waiting.|

## Constraints

1. The call service is available only on standard-system devices.
2. An available SIM card must be present on the device.


## Available APIs

> **NOTE**
> To ensure app running efficiency, most API calls are asynchronous. For asynchronous APIs, both callback and promise modes are provided. The following examples use the callback mode. For more methods, see [@ohos.telephony.call (call service)](../reference/apis-telephony-kit/js-apis-call.md).

|                                  Name                                            | Description                                                        |
| ----------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| hasVoiceCapability(): boolean;                                                      | Checks whether the device has the voice capability. The default value is `true`.<br/>-`true`: yes<br/>-`false`: no                                        |
|<!--DelRow--> dialCall(phoneNumber: string, callback: AsyncCallback&lt;void&gt;): void;                 | Makes a call. This is a system API.                                     |
| makeCall(phoneNumber: string, callback: AsyncCallback&lt;void&gt;): void;                 | Jumps to the dial interface and displays the number to be dialed.                                  |

The observer module provides the function of subscribing to and unsubscribing from call service status. For details about the APIs, see [@ohos.telephony.observer (telephony service status listening)](../reference/apis-telephony-kit/js-apis-observer.md).

| Name                                                      | Description              |
| ------------------------------------------------------------ | ------------------ |
| on(type: 'callStateChange', options: { slotId: number }, callback: Callback<[CallStateInfo](../reference/apis-telephony-kit/js-apis-observer.md#callstateinfo11)>): void; | Listens for call status changes. |

## How to Develop

<!--Del-->
### Making a Call by Using the dialCall API (Only for System Applications)

1. Declare the required permission: **ohos.permission.PLACE_CALL**.

   This permission is of the **system\_basic** level. Before applying for the permission, ensure that the [basic principles for permission management](../security/AccessToken/app-permission-mgmt-overview.md#basic-principles-for-using-permissions) are met. Then, declare the requried permission by referring to [Requesting Application Permissions](../security/AccessToken/determine-application-mode.md#requesting-permissions-for-system_basic-applications).
2. Import the **call** and **observer** modules.
3. Invoke the **hasVoiceCapability** API to check whether the device supports the voice call function.
4. Invoke the **dialCall** API to make a call.
5. (Optional) Register the observer for call service status changes.
   <!-- @[DialCall](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Telephony_Kit/MakeCall/MakeCall/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { call, observer } from '@kit.TelephonyKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   // ...
       // Call the query capability API.
       let isSupport = call.hasVoiceCapability();
       if (isSupport) {
           // If the device supports the call capability, call the following API to dial.
           call.dialCall('13xxxx', (err: BusinessError) => {
               console.error(`callback: dial call err->${JSON.stringify(err)}`);
           })
   
           // Subscribe to call service status changes (optional).
           class SlotId {public slotId: number = 0}
           class CallStateCallback {
               public state: call.CallState = call.CallState.CALL_STATE_UNKNOWN;
               public number: string = '';
           }
           let slotId: SlotId = {slotId: 0}
           observer.on('callStateChange', slotId, (data: CallStateCallback) => {
               console.info('call state change, data is:' + JSON.stringify(data));
           });
       }
   ```

<!--DelEnd-->
### Making a Call by Using the makeCall API

1. Import the **call** and **observer** modules.
2. Invoke the **hasVoiceCapability** API to check whether the device supports the voice call function.
3. Call the **makeCall** API to launch the dial screen and display the dialed number.
4. (Optional) Register the observer for call service status changes.

   <!-- @[MakeCall](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Telephony_Kit/MakeCall/MakeCall/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { call, observer } from '@kit.TelephonyKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   // ...
         // Call the query capability API.
         let isSupport = call.hasVoiceCapability();
         if (isSupport) {
             // If the device supports the call capability, jump to the dial interface and display the dialed number.
             // Starting from API 15, phone numbers in tel format are supported, for example, "tel:13xxxx".
             call.makeCall('13xxxx', (err: BusinessError) => {
                 if (!err) {
                     console.info('make call success.');
                 } else {
                     console.error('make call fail, err is:' + JSON.stringify(err));
                 }
             });
             // Subscribe to call service status changes (optional).
             class SlotId {public slotId: number = 0}
             class CallStateCallback {
                 public state: call.CallState = call.CallState.CALL_STATE_UNKNOWN;
                 public number: string = '';
             }
             let slotId: SlotId = {slotId: 0}
             observer.on('callStateChange', slotId, (data: CallStateCallback) => {
                 console.info('call state change, data is:' + JSON.stringify(data));
             });
         }
   ```

## Samples

The following sample is provided to help you better understand how to develop the call service:

- [Making a Call (ArkTS) (API 9)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/SystemFeature/Telephony/Call)
