# @ohos.distributedsched.abilityConnectionManager (Cross-Device Connection Management)
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @hu-zhiqiong-->

The **abilityConnectionManager** module provides APIs for cross-device connection management. After successful networking between devices, a system application and a third-party application can start a [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md) of the same application across these devices to establish a Bluetooth connection. This way, data (specifically, text) can be transmitted across the devices over the connection.

The following figure shows the logical layered architecture of multi-device collaboration.

 

The key principles of the logical layered architecture are as follows:

1. **Collaboration adaptation API**: Applications use the **abilityConnectionManager** API to quickly establish connections and sessions within seconds based on the soft bus. When a connection is established, the peer application is automatically started.
2. **Session ID–based data transmission**: After a connection is established, the two applications directly transmit data (via **sendMessage** or **sendData**) through the soft bus based on the session ID. This ensures higher efficiency and security for point-to-point communication.
3. **Point-to-point collaboration framework**: Devices A and B run a symmetric collaboration framework layer to manage the entire session lifecycle (creation → connection → transmission → disconnection → destruction). The APIs **connect** and **acceptConnect** are paired and called to ensure connection reliability.
4. **Event-driven communication**: The **on**/**off** registration mechanism is used to listen for connection status (**connect**/**disconnect**) and data receiving (**receiveMessage**/**receiveData**) events, implementing asynchronous and decoupled collaborative communication.

> **NOTE**
>
> The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```js
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## abilityConnectionManager.createAbilityConnectionSession

createAbilityConnectionSession(serviceName:&nbsp;string,&nbsp;context:&nbsp;Context,&nbsp;peerInfo:&nbsp;PeerInfo,&nbsp;connectOptions:&nbsp;ConnectOptions):&nbsp;number

Creates a collaboration session between applications. A collaboration session is used to manage the connection status of cross-device communication. You need to create a session on both devices and then use the connect method to establish a connection.

**Required permissions**: ohos.permission.INTERNET, ohos.permission.GET_NETWORK_INFO, ohos.permission.SET_NETWORK_INFO, and ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 801 is returned.

**Parameters**

| Name      | Type                                     | Mandatory  | Description       |
| --------- | --------------------------------------- | ---- | --------- |
| serviceName  | string | Yes   | Service name for the application. The service name must be the same on the local end and peer end. The value contains a maximum of 256 characters.|
| context | [Context](../apis-ability-kit/js-apis-inner-application-context.md) | Yes| Application context.|
| peerInfo  | [PeerInfo](#peerinfo)               | Yes   | Collaboration information of the peer end.|
| connectOptions  | [ConnectOptions](#connectoptions)               | Yes   | Connection options for the application.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| number | ID of the collaboration session that is successfully created, which will be used in subsequent API calls such as **connect**, **acceptConnect**, **sendMessage**, **sendData**, and **disconnect**. The value is an integer greater than 100.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities.|

**Example**

1. On device A, call **createAbilityConnectionSession()** to create a collaboration session and return the session ID.

   ```ts
   import { abilityConnectionManager, distributedDeviceManager } from '@kit.DistributedServiceKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   
   let dmClass: distributedDeviceManager.DeviceManager;
   
   function initDmClass(): void {
     try {
       dmClass = distributedDeviceManager.createDeviceManager('com.example.remotephotodemo');
     } catch (err) {
       hilog.error(0x0000, 'testTag', 'createDeviceManager err: ' + JSON.stringify(err));
     }
   }
   
   function getRemoteDeviceId(): string | undefined {
     initDmClass();
     if (typeof dmClass === 'object' && dmClass !== null) {
       hilog.info(0x0000, 'testTag', 'getRemoteDeviceId begin');
       let list = dmClass.getAvailableDeviceListSync();
       if (typeof (list) === 'undefined' || typeof (list.length) === 'undefined') {
         hilog.info(0x0000, 'testTag', 'getRemoteDeviceId err: list is null');
         return;
       }
       if (list.length === 0) {
         hilog.info(0x0000, 'testTag', 'getRemoteDeviceId err: list is empty');
         return;
       }
       return list[0].networkId;
     } else {
       hilog.info(0x0000, 'testTag', 'getRemoteDeviceId err: dmClass is null');
       return;
     }
   }
   
   @Entry
   @Component
   struct Index {
     createSession(): void {
       // Define peer device information.
       const peerInfo: abilityConnectionManager.PeerInfo = {
         deviceId: getRemoteDeviceId()!,
         bundleName: 'com.example.remotephotodemo',
         moduleName: 'entry',
         abilityName: 'EntryAbility',
         serviceName: 'collabTest'
       };
        const myRecord: Record<string, string> = {
          'newKey1': 'value1',
        };
   
       // Define connection options.
       const connectOptions: abilityConnectionManager.ConnectOptions = {
         needSendData: true,
         startOptions: abilityConnectionManager.StartOptionParams.START_IN_FOREGROUND,
         parameters: myRecord
       };
       let context = this.getUIContext().getHostContext();
       try {
         let sessionId = abilityConnectionManager.createAbilityConnectionSession("collabTest", context, peerInfo, connectOptions);
         hilog.info(0x0000, 'testTag', 'createSession sessionId is', sessionId);
       } catch (error) {
         hilog.error(0x0000, 'testTag', error);
       }
     }
   
     build() {
     }
   }
   ```
   
2. On device B, **createAbilityConnectionSession** can be called in **onCollaborate**, which is triggered when the application is started.

   ```ts
   import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
   import { abilityConnectionManager } from '@kit.DistributedServiceKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
    
   export default class EntryAbility extends UIAbility {
     onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult {
       hilog.info(0x0000, 'testTag', '%{public}s', 'on collaborate');
       let param = wantParam["ohos.extra.param.key.supportCollaborateIndex"] as Record<string, Object>
       this.onCollab(param);
       return 0;
     }
    
     onCollab(collabParam: Record<string, Object>) {
       const sessionId = this.createSessionFromWant(collabParam);
       if (sessionId == -1) {
         hilog.info(0x0000, 'testTag', 'Invalid session ID.');
         return;
       }
     }
    
     createSessionFromWant(collabParam: Record<string, Object>): number {
       let sessionId = -1;
       const peerInfo = collabParam["PeerInfo"] as abilityConnectionManager.PeerInfo;
       if (peerInfo == undefined) {
         return sessionId;
       }
    
       const options = collabParam["ConnectOption"] as abilityConnectionManager.ConnectOptions;
       try {
         sessionId = abilityConnectionManager.createAbilityConnectionSession("collabTest", this.context, peerInfo, options);
         AppStorage.setOrCreate('sessionId', sessionId);
         hilog.info(0x0000, 'testTag', 'createSession sessionId is ' + sessionId);
       } catch (error) {
         hilog.error(0x0000, 'testTag', error);
       }
       return sessionId;
     }
   }
   
   ```

## abilityConnectionManager.destroyAbilityConnectionSession

destroyAbilityConnectionSession(sessionId:&nbsp;number):&nbsp;void

Destroys a collaboration session between applications. This method is used together with **createAbilityConnectionSession** to release session resources. This API must be called after a collaboration session is successfully created. Destroying a session will release related resources. You are advised to call **disconnect** to disconnect the connection before destroying the session. If this method is not called, resource leak will occur.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

**Parameters**

| Name      | Type                                      | Mandatory  | Description                             |
| --------- | ---------------------------------------- | ---- |---------------------------------|
| sessionId | number | Yes| Collaboration session ID.<br>The value is an integer greater than or equal to 100. If a value less than 100 or a non-existent collaboration session ID is passed, error code 401 is returned.|

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  hilog.info(0x0000, 'testTag', 'destroyAbilityConnectionSession called');
  let sessionId = 100;
  abilityConnectionManager.destroyAbilityConnectionSession(sessionId);
  ```

## abilityConnectionManager.getPeerInfoById

getPeerInfoById(sessionId:&nbsp;number):&nbsp;PeerInfo&nbsp;|&nbsp;undefined

Obtains information about the peer application in the specified session. This API must be called after a collaboration session is successfully created.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, an empty value is returned.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| sessionId | number  | Yes   | ID of the collaboration session. The value is returned by the **createAbilityConnectionSession** API.  |

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| [PeerInfo](#peerinfo) \| undefined | Information about the collaboration app on the receiving end. If the session ID is not found, **undefined** is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  hilog.info(0x0000, 'testTag', 'getPeerInfoById called');
  // The session ID needs to be created and obtained through the createAbilityConnectionSession API. The value here is only an example.
  let sessionId = 100;
  // Obtain information about the peer application in the specified session.
  const peerInfo = abilityConnectionManager.getPeerInfoById(sessionId);
  ```

## abilityConnectionManager.connect

connect(sessionId:&nbsp;number):&nbsp;Promise&lt;ConnectResult&gt;

Sets up a UIAbility connection after a collaboration session is created and the session ID is obtained. Before calling this API, ensure that a collaboration session has been created on both devices. The **connect** API establishes a connection through the underlying distributed communication service. It must be used together with **acceptConnect** on device B to establish a connection. Calling **connect** will start the application on device B. The connection process triggers the **connect** event to notify the status change. This API uses a promise to return the result. If the connection fails, the **errorCode** field in the returned **ConnectResult** object contains the specific error information. For details about the error cause, see the **ConnectErrorCode** enumeration.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

**Parameters**

| Name      | Type                                     | Mandatory  | Description       |
| --------- | --------------------------------------- | ---- | --------- |
| sessionId | number | Yes   | ID of the created collaboration session, which is returned by the **createAbilityConnectionSession** API.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;ConnectResult&gt; | Promise used to return the result. If the operation is successful, **resolve** returns the [ConnectResult](#connectresult) (including the **isConnected** and **errorCode** fields). If the operation fails, **reject** returns an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

After a collaboration session is established and the session ID is obtained on device A,call **connect()** to set up a UIAbility connection and start the application on device B.

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  let sessionId = 100;
  abilityConnectionManager.connect(sessionId).then((ConnectResult) => {
    if (!ConnectResult.isConnected) {
      hilog.info(0x0000, 'testTag', 'connect failed');
      return;
    }
  }).catch(() => {
    hilog.error(0x0000, 'testTag', "connect failed");
  })
  ```

## abilityConnectionManager.acceptConnect

acceptConnect(sessionId:&nbsp;number,&nbsp;token:&nbsp;string):&nbsp;Promise&lt;void&gt;

Accepts the UIAbility connection after a collaboration session is set up and the session ID is obtained. Before calling this method, ensure that a collaboration session has been created on both devices. This method must be used together with the **connect** method of device A. When device A calls the **connect** method, the application on device B is started. After a session is created in the **onCollaborate** lifecycle of device B, device B calls the **acceptConnect** method. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| sessionId | number | Yes   | ID of the collaboration session.|
| token | string | Yes   | Token value passed by the application on device A. The value is obtained from the **'ohos.dms.collabToken'** key in the **wantParam** parameter of the **onCollaborate** lifecycle method after the application is started. When device A calls the **connect** method, the system automatically generates a **collabToken** and passes it to device B through the **want** parameter. Device B can obtain the token from the **wantParam** parameter in the **onCollaborate** lifecycle callbacks.   |

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

After **createAbilityConnectionSession** is called on device A to create a collaboration session and the session ID is obtained, call **acceptConnect** to accept the connection on device B.

  ```ts
  import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  export default class EntryAbility extends UIAbility {
    onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
      hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    }

    onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult {
      hilog.info(0x0000, 'testTag', '%{public}s', 'on collaborate');
      let param = wantParam["ohos.extra.param.key.supportCollaborateIndex"] as Record<string, Object>
      this.onCollab(param);
      return 0;
    }

    onCollab(collabParam: Record<string, Object>) {
      const sessionId = this.createSessionFromWant(collabParam);
      if (sessionId == -1) {
        hilog.info(0x0000, 'testTag', 'Invalid session ID.');
        return;
      }
      const collabToken = collabParam["ohos.dms.collabToken"] as string;
      abilityConnectionManager.acceptConnect(sessionId, collabToken).then(() => {
        hilog.info(0x0000, 'testTag', 'acceptConnect success');
      }).catch(() => {
        hilog.error(0x0000, 'testTag', 'failed'); 
      })
    }

    createSessionFromWant(collabParam: Record<string, Object>): number {
      let sessionId = -1;
      const peerInfo = collabParam["PeerInfo"] as abilityConnectionManager.PeerInfo;
      if (peerInfo == undefined) {
        return sessionId;
      }

      const options = collabParam["ConnectOption"] as abilityConnectionManager.ConnectOptions;
      try {
        sessionId = abilityConnectionManager.createAbilityConnectionSession("collabTest", this.context, peerInfo, options);
        AppStorage.setOrCreate('sessionId', sessionId);
        hilog.info(0x0000, 'testTag', 'createSession sessionId is ' + sessionId);
      } catch (error) {
        hilog.error(0x0000, 'testTag', error);
      }
      return sessionId;
    }
  }
  ```

## abilityConnectionManager.disconnect

disconnect(sessionId:&nbsp;number):&nbsp;void

Disconnects the UIAbility connection to end the collaboration session after a collaboration session is created, the application is connected, and the collaboration service is complete. This method must be called after a connection is established by calling **connect()**.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

**Parameters**

| Name      | Type                                   | Mandatory  | Description       |
| --------- | ------------------------------------- | ---- | --------- |
| sessionId | number | Yes   | ID of the collaboration session.    |

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  hilog.info(0x0000, 'testTag', 'disconnectRemoteAbility begin');
  let sessionId = 100;
  abilityConnectionManager.disconnect(sessionId);
  ```

## abilityConnectionManager.reject

reject(token:&nbsp;string,&nbsp;reason:&nbsp;string):&nbsp;void;

Rejects a connection request in a cross-device collaboration session. After a connection request sent from the peer application is rejected, a rejection reason is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| token | string | Yes   | Token used for application collaboration management.   |
| reason | string | Yes   | Reason why the connection is rejected.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

  ```ts
  import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  export default class EntryAbility extends UIAbility {
      onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult {
        hilog.info(0x0000, 'testTag', '%{public}s', 'on collaborate');
        let collabParam = wantParam["ohos.extra.param.key.supportCollaborateIndex"] as Record<string, Object>;
        const collabToken = collabParam["ohos.dms.collabToken"] as string;
        const reason = 'test';
        hilog.info(0x0000, 'testTag', 'reject begin');
        abilityConnectionManager.reject(collabToken, reason);
        return AbilityConstant.CollaborateResult.REJECT;
      }
  }

  ```

## abilityConnectionManager.on('connect')

on(type:&nbsp;'connect',&nbsp;sessionId:&nbsp;number,&nbsp;callback:&nbsp;Callback&lt;EventCallbackInfo&gt;):&nbsp;void

Enables listening for **connect** events. This event is triggered when the **connect** API is successfully called. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

**Parameters**

| Name      | Type                                   | Mandatory  | Description   |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | Yes   |   Event type. This field has a fixed value of **connect**. This event is triggered when [abilityConnectionManager.connect()](#abilityconnectionmanagerconnect) is called.  |
| sessionId | number  | Yes   | ID of the collaboration session.|
| callback | Callback&lt;[EventCallbackInfo](#eventcallbackinfo)&gt; | Yes   | Registered callback function.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  // The session ID needs to be created and obtained through the createAbilityConnectionSession API. The value here is only an example.
  let sessionId = 100;
  abilityConnectionManager.on("connect", sessionId,(callbackInfo) => {
    hilog.info(0x0000, 'testTag', 'session connect, sessionId is', callbackInfo.sessionId);
  });

  ```

## abilityConnectionManager.off('connect')

off(type:&nbsp;'connect',&nbsp;sessionId:&nbsp;number,&nbsp;callback?:&nbsp;Callback&lt;EventCallbackInfo&gt;):&nbsp;void

Disables listening for **connect** events.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

**Parameters**

| Name      | Type                                   | Mandatory  | Description   |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | Yes   |   Event callback type. The supported event is **'connect'**, which can be canceled only after being registered using [abilityConnectionManager.on('connect')](#abilityconnectionmanageronconnect).   |
| sessionId | number  | Yes   | ID of the collaboration session.|
| callback | Callback&lt;[EventCallbackInfo](#eventcallbackinfo)&gt; | No   | Callback used to return the result. If this parameter is not passed, all callback listeners for the event are canceled.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';

  // The session ID needs to be created and obtained through the createAbilityConnectionSession API. The value here is only an example.
  let sessionId = 100;
  abilityConnectionManager.off("connect", sessionId);

  ```

## abilityConnectionManager.on('disconnect')

on(type:&nbsp;'disconnect',&nbsp;sessionId:&nbsp;number,&nbsp;callback:&nbsp;Callback&lt;EventCallbackInfo&gt;):&nbsp;void

Enables listening for **disconnect** events.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

**Parameters**

| Name      | Type                                   | Mandatory  | Description   |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | Yes   |   Event type. This field has a fixed value of **disconnect**. This event is triggered when [abilityConnectionManager.disconnect()](#abilityconnectionmanagerdisconnect) is called.  |
| sessionId | number  | Yes   | ID of the collaboration session.|
| callback | Callback&lt;[EventCallbackInfo](#eventcallbackinfo)&gt; | Yes   | Registered callback function.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  // The sessionId needs to be created and obtained through the createAbilityConnectionSession API. The value here is only an example.
  let sessionId = 100;
  abilityConnectionManager.on("disconnect", sessionId,(callbackInfo) => {
    hilog.info(0x0000, 'testTag', 'session disconnect, sessionId is', callbackInfo.sessionId);
  });

  ```

## abilityConnectionManager.off('disconnect')

off(type:&nbsp;'disconnect',&nbsp;sessionId:&nbsp;number,&nbsp;callback?:&nbsp;Callback&lt;EventCallbackInfo&gt;):&nbsp;void

Disables listening for **disconnect** events.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

**Parameters**

| Name      | Type                                   | Mandatory  | Description   |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | Yes   |   Event callback type. The supported event is **'disconnect'**, which can be canceled only after being registered through [abilityConnectionManager.on('disconnect')](#abilityconnectionmanagerondisconnect).   |
| sessionId | number  | Yes   | ID of the collaboration session.|
| callback | Callback&lt;[EventCallbackInfo](#eventcallbackinfo)&gt; | No   | Callback to be unregistered. If this parameter is not passed, all callback functions of the event will be unregistered.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  // The session ID needs to be created and obtained through the createAbilityConnectionSession API. The value here is only an example.
  let sessionId = 101;
  abilityConnectionManager.off("disconnect", sessionId);

  ```

## abilityConnectionManager.on('receiveMessage')

on(type:&nbsp;'receiveMessage',&nbsp;sessionId:&nbsp;number,&nbsp;callback:&nbsp;Callback&lt;EventCallbackInfo&gt;):&nbsp;void

Enables listening for **receiveMessage** events.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

**Parameters**

| Name      | Type                                   | Mandatory  | Description   |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | Yes   |   Event type. This field has a fixed value of **receiveMessage**. This event is triggered when [abilityConnectionManager.sendMessage()](#abilityconnectionmanagersendmessage) is called.  |
| sessionId | number  | Yes   | ID of the collaboration session.|
| callback | Callback&lt;[EventCallbackInfo](#eventcallbackinfo)&gt; | Yes   | Registered callback function.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  // The sessionId needs to be created and obtained through the createAbilityConnectionSession API. The value here is only an example.
  let sessionId = 100;
  abilityConnectionManager.on("receiveMessage", sessionId,(callbackInfo) => {
    hilog.info(0x0000, 'testTag', 'receiveMessage, sessionId is', callbackInfo.sessionId);
  });

  ```

## abilityConnectionManager.off('receiveMessage')

off(type:&nbsp;'receiveMessage',&nbsp;sessionId:&nbsp;number,&nbsp;callback?:&nbsp;Callback&lt;EventCallbackInfo&gt;):&nbsp;void

Disables listening for **receiveMessage** events.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

**Parameters**

| Name      | Type                                   | Mandatory  | Description   |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | Yes   |   Event callback type. The supported event is **'receiveMessage'**, which can be canceled only after being registered using [abilityConnectionManager.on('receiveMessage')](#abilityconnectionmanageronreceivemessage).   |
| sessionId | number  | Yes   | ID of the collaboration session.|
| callback | Callback&lt;[EventCallbackInfo](#eventcallbackinfo)&gt; | No   | Callback to be unregistered. If this parameter is not passed, all callback functions of the event will be unregistered.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  // The session ID needs to be created and obtained through the createAbilityConnectionSession API. The value here is only an example.
  let sessionId = 100;
  abilityConnectionManager.off("receiveMessage", sessionId);

  ```

## abilityConnectionManager.on('receiveData')

on(type:&nbsp;'receiveData',&nbsp;sessionId:&nbsp;number,&nbsp;callback:&nbsp;Callback&lt;EventCallbackInfo&gt;):&nbsp;void

Enables listening for **receiveData** events.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

**Parameters**

| Name      | Type                                   | Mandatory  | Description   |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | Yes   |   Event type. This field has a fixed value of **receiveData**. This event is triggered when [abilityConnectionManager.sendData()](#abilityconnectionmanagersenddata) is called.  |
| sessionId | number  | Yes   | ID of the collaboration session.|
| callback | Callback&lt;[EventCallbackInfo](#eventcallbackinfo)&gt; | Yes   | Registered callback function.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  // The session ID needs to be created and obtained through the createAbilityConnectionSession API. The value here is only an example.
  let sessionId = 100;
  abilityConnectionManager.on("receiveData", sessionId,(callbackInfo) => {
    hilog.info(0x0000, 'testTag', 'receiveData, sessionId is', callbackInfo.sessionId);
  });

  ```

## abilityConnectionManager.off('receiveData')

off(type:&nbsp;'receiveData',&nbsp;sessionId:&nbsp;number,&nbsp;callback?:&nbsp;Callback&lt;EventCallbackInfo&gt;):&nbsp;void

Disables listening for **receiveData** events.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

**Parameters**

| Name      | Type                                   | Mandatory  | Description   |
| --------- | ------------------------------------- | ---- | ----- |
| type | string  | Yes   |   Event callback type. The supported event is **'receiveData'**, which can be canceled only after being registered using [abilityConnectionManager.on('receiveData')](#abilityconnectionmanageronreceivedata).   |
| sessionId | number  | Yes   | ID of the collaboration session.|
| callback | Callback&lt;[EventCallbackInfo](#eventcallbackinfo)&gt; | No   | Callback to be unregistered. If this parameter is not passed, all callback functions of the event will be unregistered.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';

  // The session ID needs to be created and obtained through the createAbilityConnectionSession API. The value here is only an example.
  let sessionId = 100;
  abilityConnectionManager.off("receiveData", sessionId);

  ```

## abilityConnectionManager.sendMessage

sendMessage(sessionId:&nbsp;number,&nbsp;msg:&nbsp;string):&nbsp;Promise&lt;void&gt;

Sends text messages after a collaboration session is created and a connection is set up by calling the **connect** API. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| sessionId | number | Yes   | ID of the collaboration session. The value is returned by the **createAbilityConnectionSession** API.|
| msg | string | Yes   | Text content. The maximum size of the text content is 1 KB. If the length exceeds the upper limit, error code 401 is returned.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value. If the message is sent successfully, **resolve** will be called. If the message fails to be sent, **reject** will be called.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit'; 
  import { hilog } from '@kit.PerformanceAnalysisKit';

  let sessionId = 100;
  abilityConnectionManager.sendMessage(sessionId, "message send success").then(() => {
    hilog.info(0x0000, 'testTag', "sendMessage success");
  }).catch(() => {
    hilog.error(0x0000, 'testTag', "sendMessage failed");
  })
  ```

## abilityConnectionManager.sendData

sendData(sessionId:&nbsp;number,&nbsp;data:&nbsp;ArrayBuffer):&nbsp;Promise&lt;void&gt;

Sends [ArrayBuffer](../../arkts-utils/arraybuffer-object.md) byte streams from one device to another after a collaboration connection is successfully established, the session ID is obtained, and the app is successfully connected. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| sessionId | number | Yes   | ID of the collaboration session.|
| data | [ArrayBuffer](../../arkts-utils/arraybuffer-object.md) | Yes   | Byte stream information.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

  ```ts
  import { abilityConnectionManager } from '@kit.DistributedServiceKit';
  import { hilog } from '@kit.PerformanceAnalysisKit';
  import { util } from '@kit.ArkTS';
 
  let textEncoder = util.TextEncoder.create("utf-8");
  const arrayBuffer  = textEncoder.encodeInto("data send success");

  let sessionId = 100;
  abilityConnectionManager.sendData(sessionId, arrayBuffer.buffer).then(() => {
    hilog.info(0x0000, 'testTag', "sendData success");
  }).catch(() => {
    hilog.error(0x0000, 'testTag', "sendData failed");
  })
  ```

## PeerInfo

Defines the application collaboration information.

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

 **Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name                   | Type      |Read Only  | Optional  | Description                |
| ----------------- | ------ | ----  | ---- | ------------------ |
| deviceId          | string | No  |No   | Network ID of the peer device, which is used to identify the remote device to be connected. You can obtain the value by calling the distributed device management API **getAvailableDeviceListSync**.    |
| bundleName        | string | No  |No   | Bundle name of the peer app, which uniquely identifies the app to be connected. The value must be the same as the bundle name of the peer app.|
| moduleName        | string | No  |No   | Module name of the peer app, which uniquely identifies the app module to be connected. Generally, the value is **'entry'** or another custom module name.|
| abilityName       | string | No  |No    | Component name of the peer app, which uniquely identifies the UIAbility component to be connected. The value must be the same as the ability name of the peer app.|
| serviceName       | string | No  |Yes    | Service name for the application. If this parameter is set, its value must be the same as that of **serviceName** in the **createAbilityConnectionSession** API. If this parameter is not set, the default service name is used.|

## ConnectOptions

Connection options for the application.

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name         | Type   | Read Only  | Optional  | Description         |
| ----------- | ------- | ---- | ---- | ----------- |
| needSendData    | boolean  | No   | Yes  | Whether data needs to be transmitted. The value **true** indicates that data needs to be transmitted (the **sendMessage** and **sendData** methods can be called), and the value **false** indicates that data does not need to be transmitted. If no value is passed, the default value **false** is used.    |
| startOptions | [StartOptionParams](#startoptionparams) | No   | Yes  | App startup options. **START_IN_FOREGROUND** (with value **0**) indicates that the peer app is started in the foreground, which is suitable for scenarios that require user interaction. If no value is passed, the default startup configuration is used.|
| parameters | Record&lt;string, string&gt;  | No   | Yes  | Additional configuration for the connection. This parameter is passed when custom parameters, such as the identity and service ID, need to be passed to the peer device. If no value is passed, no additional information is transferred.   |

## ConnectResult

Defines the connection result.

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

 **Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name      | Type  | Read Only  | Optional  | Description     |
| -------- | ------ | ---- | ---- | ------- |
| isConnected | boolean | No  | No| **true** indicates that the connection is successful. **false** indicates that the connection fails. For details about the cause, see the **errorCode** or **reason** field.|
| errorCode | [ConnectErrorCode](#connecterrorcode) | No  | Yes  | Connection error code. This field exists when the connection fails and is used to identify the specific cause. This field does not exist when the connection is successful.|
| reason | string | No  | Yes  | Connection rejection reason, which is returned only when the connection is rejected. The value is the **reason** parameter passed when the peer app calls the **reject** API. It is used to notify the local end of the specific reason for rejection. This parameter is not included when the connection is successful or not rejected.|

## EventCallbackInfo

Defines the event callback information.

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

 **Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name      | Type   | Read Only| Optional| Description         |
| -------- | ------ | ---- | ---- | ----------- |
| sessionId | number   | No  | No  |   Collaboration session ID.|
| reason | [DisconnectReason](#disconnectreason)     | No  | Yes  | Disconnection reason. This parameter is available when the **disconnect** event is triggered and is used to identify the specific disconnection reason. This parameter is not available for other event types.|
| msg | string   | No  | Yes  | Received message. This parameter is available when the **receiveMessage** event is triggered and contains the received text message content. This parameter is not available for other event types.|
| data  | ArrayBuffer | No  | Yes  | Received byte stream. This parameter is available when the **receiveData** event is triggered. It contains the received binary data. This parameter is not available for other event types.|

## CollaborateEventInfo

Collaboration event information.

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

 **Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name      | Type  | Read Only  | Optional  | Description     |
| -------- | ------ | ---- | ---- | ------- |
| eventType | [CollaborateEventType](#collaborateeventtype) | No  | No| Collaboration event type. The value **0** indicates **SEND_FAILURE**, and the value **1** indicates **COLOR_SPACE_CONVERSION_FAILURE**.|
| eventMsg | string | No  | Yes  | Content of a collaboration event. This parameter is available when **eventType** is set to **SEND_FAILURE** or **COLOR_SPACE_CONVERSION_FAILURE**.|

## ConnectErrorCode

Enumerates connection error codes.

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

 **Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name|  Value| Description|
|-------|-------|-------|
| CONNECTED_SESSION_EXISTS | 0 |A session already exists between applications.|
| PEER_APP_REJECTED | 1 |The peer application rejects the collaboration request.|
| LOCAL_WIFI_NOT_OPEN | 2 |Wi-Fi is disabled at the local end.|
| PEER_WIFI_NOT_OPEN | 3 |Wi-Fi is disabled at the peer end.|
| PEER_ABILITY_NO_ONCOLLABORATE | 4 |The **onCollaborate** callback is not implemented.|
| SYSTEM_INTERNAL_ERROR | 5 |An internal system error occurs.|

## StartOptionParams

Enumerates application start options.

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

 **Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name|  Value| Description|
|-------|-------|-------|
| START_IN_FOREGROUND | 0 |Start of the peer application in the foreground.|

## CollaborateEventType

Enumerates collaboration event types.

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

 **Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name|  Value| Description|
|-------|-------|-------|
| SEND_FAILURE | 0 |Task sending failure. This event is generated when a collaboration task (such as a collaboration event) fails to be sent during cross-device collaboration. Common causes include network exceptions and unreachable peer devices.|
| COLOR_SPACE_CONVERSION_FAILURE | 1 |Color space conversion failure. This event is generated when the image data fails to be converted from the color space of the source device to that of the target device in cross-device image collaboration scenarios. The common causes include unsupported color format and incorrect conversion parameters.|

## DisconnectReason

Enumerates the disconnection reasons.

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

 **Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name|  Value| Description|
|-------|-------|-------|
| PEER_APP_CLOSE_COLLABORATION | 0 |The peer application proactively disables collaboration.|
| PEER_APP_EXIT | 1 |The peer application exits.|
| NETWORK_DISCONNECTED | 2 |The network is disconnected.|

## CollaborationKeys

Enumerates app collaboration key values.

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

 **Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name               |                  Value            | Description                  |
| -------------------| ------------------------------- | ---------------------- |
| PEER_INFO           | ohos.collaboration.key.peerInfo | Key value of the peer device information.|
| CONNECT_OPTIONS     | ohos.collaboration.key.connectOptions | Key value of the connection option.  |
| COLLABORATE_TYPE    | ohos.collaboration.key.abilityCollaborateType | Key value of the collaboration type.  |

## CollaborationValues

**Device behavior differences**: If this API is called on a wearable device that does not support distributed services or on a device controlled by an enterprise policy, error code 401 is returned.

 **Model restriction**: This API can be used only in the stage model.

Enumerates application collaboration values.

**System capability**: SystemCapability.DistributedSched.AppCollaboration

| Name                                     | Value      | Description                  |
| ----------------------------------------- | -------- | ---------------------- |
| ABILITY_COLLABORATION_TYPE_DEFAULT | ohos.collaboration.value.abilityCollab | Default collaboration.|
| ABILITY_COLLABORATION_TYPE_CONNECT_PROXY  | ohos.collaboration.value.connectProxy | Collaboration via connection proxy.  |
