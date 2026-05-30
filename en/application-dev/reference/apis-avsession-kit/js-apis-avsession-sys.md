# @ohos.multimedia.avsession (AVSession Management) (System API)
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester:@chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

The AVSession module provides APIs for media playback control so that applications can access the system's Media Controller.

This module provides the following typical features related to media sessions:

- [AVCastController](#avcastcontroller10): used to control playback, listen for remote playback state changes, and obtain the remote playback state in casting scenarios.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.multimedia.avsession (AVSession Management)](arkts-apis-avsession.md).

## Modules to Import

```ts
import { avSession } from '@kit.AVSessionKit';
```

## Usage Guidelines

This topic describes only system APIs. Before using these APIs, you must create an instance. For details about how to create an instance, see the description and example of the public API [avSession.createAVSession](arkts-apis-avsession-f.md#avsessioncreateavsession10).

## avSession.getAllSessionDescriptors 

getAllSessionDescriptors(callback: AsyncCallback\<Array\<Readonly\<AVSessionDescriptor>>>): void 

Obtains the descriptors of all sessions that have been configured with media information and registered with the control callback. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES (available only to system applications)

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                      | 
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------ | 
| callback | AsyncCallback<Array<Readonly<[AVSessionDescriptor](arkts-apis-avsession-i.md#avsessiondescriptor-23)\>\>\> | Yes  | Callback used to return an array of AVSessionDescriptor objects, each of which is read only.| 

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message| 
| -------- | ---------------------------------------- | 
| 201 | permission denied. | 
| 202 | Not System App. |
| 6600101  |Session service exception. | 

**Example**

```ts 
import { avSession } from '@kit.AVSessionKit';

@Entry 
@Component 
struct Index { 
  @State message: string = 'hello world'; 

  build() { 
    Column() { 
        Text(this.message) 
          .onClick(()=>{ 
            avSession.getAllSessionDescriptors((descriptors: avSession.AVSessionDescriptor[]) => { 
                console.info(`Succeeded in getting all session descriptors, length: ${descriptors.length}`); 
                if (descriptors.length > 0 ) { 
                    console.info(`Succeeded in getting session descriptor, isActive: ${descriptors[0].isActive}`); 
                    console.info(`Succeeded in getting session descriptor, type: ${descriptors[0].type}`); 
                    console.info(`Succeeded in getting session descriptor, sessionTag: ${descriptors[0].sessionTag}`); 
                } 
            }); 
          }) 
      } 
    .width('100%') 
    .height('100%') 
  } 
} 
```

## avSession.getSessionDescriptors<sup>22+</sup>

getSessionDescriptors(category: SessionCategory): Promise\<Array\<Readonly\<AVSessionDescriptor>>>

Obtains the session descriptors based on the session category. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name   | Type                             | Mandatory| Description           |
| --------  | ----------------------------------| ---- |  ---------------|
| category  |  [SessionCategory](#sessioncategory22) |  Yes | Session category.|


**Return value**

| Type                                                                       | Description                                  |
| --------------------------------------------------------------------------- | -------------------------------------- |
| Promise\<Array\<Readonly\<[AVSessionDescriptor](arkts-apis-avsession-i.md#avsessiondescriptor-23)\>\>\> | Promise used to return an array of **AVSessionDescriptor** objects of the corresponding category, each of which is read only.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
| 202 | Not System App. |
| 6600101  | Session service exception. |

**Example**

```ts
avSession.getSessionDescriptors(avSession.SessionCategory.CATEGORY_ALL).then((descriptors: avSession.AVSessionDescriptor[]) => {
  console.info(`Succeeded in getting session descriptors, length: ${descriptors.length}`);
  if (descriptors.length > 0) {
    console.info(`Succeeded in getting session descriptor, isActive: ${descriptors[0].isActive}`);
    console.info(`Succeeded in getting session descriptor, type: ${descriptors[0].type}`);
    console.info(`Succeeded in getting session descriptor, sessionTag: ${descriptors[0].sessionTag}`);
  }
});
```

## avSession.getHistoricalSessionDescriptors<sup>10+</sup>

getHistoricalSessionDescriptors(maxSize?: number): Promise\<Array\<Readonly\<AVSessionDescriptor>>>

Obtains the descriptors of all historical sessions. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name  | Type   | Mandatory| Description                                                            |
| -------- | ------ | ---- | -----------------------------------------------------------------|
| maxSize  | number | No  | Maximum number of descriptors to obtain. The value ranges from 0 to 10. If this parameter is left blank, the default value **3** is used.|

**Return value**

| Type                                                                       | Description                                  |
| --------------------------------------------------------------------------- | -------------------------------------- |
| Promise\<Array\<Readonly\<[AVSessionDescriptor](arkts-apis-avsession-i.md#avsessiondescriptor-23)\>\>\> | Promise used to return an array of AVSessionDescriptor objects, each of which is read only.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avSession.getHistoricalSessionDescriptors().then((descriptors: avSession.AVSessionDescriptor[]) => {
  console.info(`Succeeded in getting historical session descriptors, length: ${descriptors.length}`);
  if (descriptors.length > 0 && descriptors[0]) {
    console.info(`Succeeded in getting historical session descriptor, isActive: ${descriptors[0].isActive}`);
    console.info(`Succeeded in getting historical session descriptor, type: ${descriptors[0].type}`);
    console.info(`Succeeded in getting historical session descriptor, sessionTag: ${descriptors[0].sessionTag}`);
    console.info(`Succeeded in getting historical session descriptor, sessionId: ${descriptors[0].sessionId}`);
    console.info(`Succeeded in getting historical session descriptor, bundleName: ${descriptors[0].elementName.bundleName}`);
  }
});
```

## avSession.getHistoricalSessionDescriptors<sup>10+</sup>

getHistoricalSessionDescriptors(maxSize: number, callback: AsyncCallback\<Array\<Readonly\<AVSessionDescriptor>>>): void

Obtains the descriptors of all historical sessions. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                                           | Mandatory| Description                                                            |
| -------- | ------------------------------------------------------------------------------ | ---- |-----------------------------------------------------------------|
| maxSize  | number                                                                         | Yes | Maximum number of descriptors to obtain. The value ranges from 0 to 10.|
| callback | AsyncCallback<Array<Readonly<[AVSessionDescriptor](arkts-apis-avsession-i.md#avsessiondescriptor-23)\>\>\> | Yes  | Callback used to return an array of AVSessionDescriptor objects, each of which is read only.                             |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 |  permission denied. |
| 202 |  Not System App.  |
| 401 |  parameter check failed. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  |Session service exception. |

**Example**

```ts
avSession.getHistoricalSessionDescriptors(1, (descriptors: avSession.AVSessionDescriptor[]) => { 
    console.info(`Succeeded in getting historical session descriptors, length: ${descriptors.length}`); 
    if (descriptors.length > 0 ) { 
      console.info(`Succeeded in getting historical session descriptor, isActive: ${descriptors[0].isActive}`); 
      console.info(`Succeeded in getting historical session descriptor, type: ${descriptors[0].type}`); 
      console.info(`Succeeded in getting historical session descriptor, sessionTag: ${descriptors[0].sessionTag}`); 
      console.info(`Succeeded in getting historical session descriptor, sessionId: ${descriptors[0].sessionId}`); 
      console.info(`Succeeded in getting historical session descriptor, bundleName: ${descriptors[0].elementName.bundleName}`); 
    } 
});
```

## avSession.getHistoricalAVQueueInfos<sup>11+</sup>

getHistoricalAVQueueInfos(maxSize: number, maxAppSize: number) : Promise\<Array\<Readonly\<AVQueueInfo>>>

Obtains all the historical playlists. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name  | Type   | Mandatory| Description                                                            |
| -------- | ------ | ---- | ---------------------------------------------------------------|
| maxSize  | number | Yes  | Maximum number of playlists that can be obtained. Currently, the maximum number is restricted by the system.                    |
| maxAppSize | number | Yes  | Maximum number of applications to which the playlists to be obtained belong. Currently, the maximum number is restricted by the system.            |

**Return value**

| Type                                                                       | Description                                  |
| --------------------------------------------------------------------------- | ------------------------------------- |
| Promise\<Array\<Readonly\<[AVQueueInfo](#avqueueinfo11)\>\>\> | Promise used to return all the read-only historical playlists.               |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avSession.getHistoricalAVQueueInfos(3, 5).then((avQueueInfos: avSession.AVQueueInfo[]) => {
  console.info(`Succeeded in getting historical AV queue infos, length: ${avQueueInfos.length}`);
});
```

## avSession.getHistoricalAVQueueInfos<sup>11+</sup>

getHistoricalAVQueueInfos(maxSize: number, maxAppSize: number, callback: AsyncCallback\<Array\<Readonly\<AVQueueInfo>>>): void;

Obtains all the historical playlists. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                                           | Mandatory| Description                                                            |
| -------- | ----------------------------------------------------------------------------- | ---- |---------------------------------------------------------------|
| maxSize  | number                                                                        | Yes  | Maximum number of playlists that can be obtained. Currently, the maximum number is restricted by the system.                     |
| maxAppSize | number                                                                      | Yes  | Maximum number of applications to which the playlists to be obtained belong. Currently, the maximum number is restricted by the system.              |
| callback | AsyncCallback<Array<Readonly<[AVQueueInfo](#avqueueinfo11)\>\>\> | Yes  | Callback used to return all the read-only historical playlists.                             |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  |Session service exception. |

**Example**

```ts
avSession.getHistoricalAVQueueInfos(3, 5, (avQueueInfos: avSession.AVQueueInfo[]) => { 
    console.info(`Succeeded in getting historical AV queue infos, length: ${avQueueInfos.length}`); 
});
```

## avSession.createController 

createController(sessionId: string, callback: AsyncCallback\<AVSessionController>): void 

Creates a session controller based on the session ID. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES (available only to system applications)

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name   | Type                                                       | Mandatory| Description                                                        | 
| --------- | ----------------------------------------------------------- | ---- |------------------------------------------------------------ | 
| sessionId | string                                                      | Yes  | Session ID.                                                    | 
| callback  | AsyncCallback<[AVSessionController](arkts-apis-avsession-AVSessionController.md)\> | Yes  | Callback used to return the session controller created, which can be used to obtain the session ID,<br>send commands and events to sessions, and obtain metadata and playback state information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message| 
| -------- | ---------------------------------------- | 
| 201 | permission denied. | 
| 202 | Not System App. | 
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. | 
| 6600101  | Session service exception. | 
| 6600102  | The session does not exist. | 

**Example**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
        Text(this.message)
          .onClick(()=>{
            avSession.getAllSessionDescriptors().then((descriptors: avSession.AVSessionDescriptor[]) => {
              console.info(`Succeeded in getting all session descriptors, length: ${descriptors.length}`);
              if (descriptors.length > 0 ) {
avSession.createController(descriptors[0]?.sessionId, (avcontroller: avSession.AVSessionController) => { 
                    console.info('Succeeded in creating controller.'); 
                });
              }
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## avSession.castAudio

castAudio(session: SessionToken | 'all', audioDevices: Array<audio.AudioDeviceDescriptor>): Promise\<void>

Casts a session to a list of devices. This API uses a promise to return the result.

Before calling this API, import the **ohos.multimedia.audio** module to obtain the descriptors of these audio devices.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES (available only to system applications)

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name       | Type          | Mandatory| Description|
| ------------ | -------------- |------|------|
| session      | [SessionToken](#sessiontoken) &#124; 'all' | Yes  | Session token. **SessionToken** indicates a specific token, and **'all'** indicates all tokens.|
| audioDevices | Array\<[audio.AudioDeviceDescriptor](../apis-audio-kit/arkts-apis-audio-i.md#audiodevicedescriptor)\> | Yes  | Audio devices. |

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If casting is successful, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600104  | The remote session connection failed. |

**Example**

```ts
import { audio } from '@kit.AudioKit';

let audioManager = audio.getAudioManager();
let audioRoutingManager = audioManager.getRoutingManager();
let audioDevices: audio.AudioDeviceDescriptors | undefined = undefined;
audioRoutingManager.getDevices(audio.DeviceFlag.OUTPUT_DEVICES_FLAG).then((data) => {
  audioDevices = data;
  console.info('Promise returned to indicate that the device list is obtained.');
});

if (audioDevices !== undefined) {
  avSession.castAudio('all', audioDevices as audio.AudioDeviceDescriptors).then(() => {
    console.info('Succeeded in creating controller.');
  });
}
```

## avSession.castAudio

castAudio(session: SessionToken | 'all', audioDevices: Array<audio.AudioDeviceDescriptor>, callback: AsyncCallback\<void>): void

Casts a session to a list of devices. This API uses an asynchronous callback to return the result.

Before calling this API, import the **ohos.multimedia.audio** module to obtain the descriptors of these audio devices.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES (available only to system applications)

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name      | Type                                        | Mandatory| Description                                                        |
| ------------ |--------------------------------------------| ---- | ------------------------------------------------------------ |
| session      | [SessionToken](#sessiontoken) &#124; 'all' | Yes  | Session token. **SessionToken** indicates a specific token, and **'all'** indicates all tokens.|
| audioDevices | Array\<[audio.AudioDeviceDescriptor](../apis-audio-kit/arkts-apis-audio-i.md#audiodevicedescriptor)\>   | Yes  | Audio devices.|
| callback     | AsyncCallback\<void>     | Yes  | Callback used to return the result. If casting is successful, **err** is **undefined**; otherwise, **err** is an error object.     |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |
| 6600104  | The remote session connection failed. |

**Example**

```ts
import { audio } from '@kit.AudioKit';

let audioManager = audio.getAudioManager();
let audioRoutingManager = audioManager.getRoutingManager();
let audioDevices: audio.AudioDeviceDescriptors | undefined = undefined;
audioRoutingManager.getDevices(audio.DeviceFlag.OUTPUT_DEVICES_FLAG).then((data) => {
  audioDevices = data;
  console.info('Promise returned to indicate that the device list is obtained.');
  if (audioDevices !== undefined) {
    avSession.castAudio('all', audioDevices as audio.AudioDeviceDescriptors, () => {
        console.info('Succeeded in casting audio.');
    });
  }
});
```

## avSession.startAVPlayback<sup>11+</sup>

startAVPlayback(bundleName: string, assetId: string): Promise\<void>

Starts an application to play a media asset. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES (available only to system applications)

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name       | Type          | Mandatory| Description|
| ------------ | -------------- |------|------|
| bundleName   | string         | Yes  | Bundle name of the application.|
| assetId      |string           | Yes  | ID of the media asset. |

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the playback is successful, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
| 202 | Not System App. Interface caller is not a system app. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| 6600101  | Session service exception. |

**Example**

```ts
import { audio } from '@kit.AudioKit';

avSession.startAVPlayback("com.example.myapplication", "121278").then(() => {
  console.info('Succeeded in starting AV playback.');
});
```

## avSession.getDistributedSessionController<sup>18+</sup>

getDistributedSessionController(distributedSessionType: DistributedSessionType): Promise<Array\<AVSessionController>>

Obtains remote distributed session controllers based on the remote session type. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name   | Type                                                                     | Mandatory| Description     |
| --------- |-------------------------------------------------------------------------| ---- |---------|
| distributedSessionType | [DistributedSessionType](#distributedsessiontype18) | Yes  | Remote session type.|

**Return value**

| Type                                                                                | Description                                                                   |
|------------------------------------------------------------------------------------|-----------------------------------------------------------------------|
| Promise<Array<[AVSessionController](arkts-apis-avsession-AVSessionController.md)\>> | Promise used to return an array of session controller instances of the corresponding type. You can view the session ID, send commands and events to the session, and obtain metadata and playback status information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID  | Error Message                                                                                                 |
|---------|-------------------------------------------------------------------------------------------------------|
| 201     | permission denied.                                                                                    |
| 202     | Not System App. |
| 6600101 | Session service exception.                                                                            |
| 6600109 | The remote connection is not established.                                                             |

**Example**

```ts
import { avSession } from '@kit.AVSessionKit';

avSession.getDistributedSessionController(avSession.DistributedSessionType.TYPE_SESSION_REMOTE).then((sessionControllers: Array<avSession.AVSessionController>) => {
  console.info(`Succeeded in getting distributed session controller, length: ${sessionControllers.length}`);
});
```


## SessionToken

Describes the information about a session token.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES (available only to system applications)

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

| Name     | Type  | Read-Only| Optional| Description        |
| :-------- | :----- | :--- |:--- | :----------- |
| sessionId | string | No| No  | Session ID.      |
| pid       | number | No | Yes| Process ID of the session.|
| uid       | number | No  | Yes| User ID.      |

## avSession.on('sessionCreate') 

on(type: 'sessionCreate', callback: (session: AVSessionDescriptor) => void): void 

Subscribes to session creation events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**
 
| Name   | Type                  | Mandatory| Description                                                        |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| type     | string                 | Yes  | Event type. The event **'sessionCreate'** is triggered when a session is created.|
| callback | (session: [AVSessionDescriptor](arkts-apis-avsession-i.md#avsessiondescriptor-23)) => void | Yes  | Callback used to report the session descriptor.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message| 
| -------- | ---------------------------------------- | 
| 202 | Not System App. | 
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. | 
| 6600101  | Session service exception. | 

 **Example**
```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
        Text(this.message)
          .onClick(()=>{
            avSession.on('sessionCreate', (descriptor: avSession.AVSessionDescriptor) => {
              console.info(`on sessionCreate : isActive : ${descriptor.isActive}`);
              console.info(`on sessionCreate : type : ${descriptor.type}`);
              console.info(`on sessionCreate : sessionTag : ${descriptor.sessionTag}`);
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}

```

## avSession.on('sessionDestroy') 

on(type: 'sessionDestroy', callback: (session: AVSessionDescriptor) => void): void 

Subscribes to session destroy events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name  | Type           | Mandatory| Description                                                        |
| -------- | ---------------| ---- | ------------------------------------------------------------ |
| type     | string         | Yes  | Event type. The event **'sessionDestroy'** is triggered when a session is destroyed.|
| callback | (session: [AVSessionDescriptor](arkts-apis-avsession-i.md#avsessiondescriptor-23)) => void | Yes  | Callback used to report the session descriptor.|

 **Error codes**

 For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).
 
 | ID| Error Message| 
 | -------- | ---------------------------------------- | 
 | 202 | Not System App. | 
 | 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. | 
 | 6600101  | Session service exception. | 
 
**Example**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
        Text(this.message)
          .onClick(()=>{
            avSession.on('sessionDestroy', (descriptor: avSession.AVSessionDescriptor) => {
              console.info(`on sessionDestroy : ${descriptor.sessionId}`);
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}
```
 
## avSession.on('topSessionChange') 

on(type: 'topSessionChange', callback: (session: AVSessionDescriptor) => void): void 

Subscribes to the top session change events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | --------------------| ---- | ------------------------------------------------------------ |
| type     | string      | Yes  | Event type. The event **'topSessionChange'** is triggered when the top session is changed.|
| callback | (session: [AVSessionDescriptor](arkts-apis-avsession-i.md#avsessiondescriptor-23)) => void | Yes  | Callback used to report the session descriptor.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message| 
| -------- | ---------------------------------------- | 
| 202 | Not System App. | 
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. | 
| 6600101  | Session service exception. | 

**Example**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
        Text(this.message)
          .onClick(()=>{
            avSession.on('topSessionChange', (descriptor: avSession.AVSessionDescriptor) => {
              console.info(`on topSessionChange : isActive : ${descriptor.isActive}`);
              console.info(`on topSessionChange : type : ${descriptor.type}`);
              console.info(`on topSessionChange : sessionTag : ${descriptor.sessionTag}`);
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## avSession.off('sessionCreate') 

off(type: 'sessionCreate', callback?: (session: AVSessionDescriptor) => void): void 

Unsubscribes from session creation events. After unsubscription, the event will no longer be received.

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

 **Parameters**

| Name  | Type      | Mandatory| Description      |
| -------- | ----------| ---- | ----------|
| type     | string    | Yes  | Event type, which is **'sessionCreate'** in this case.|
| callback | (session: [AVSessionDescriptor](arkts-apis-avsession-i.md#avsessiondescriptor-23)) => void | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **session** parameter in the callback describes a media session. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.                              |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message| 
| -------- | ---------------------------------------- | 
| 202 | Not System App. | 
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. | 
| 6600101  | Session service exception. | 

**Example**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
        Text(this.message)
          .onClick(()=>{
            avSession.on('sessionCreate', (descriptor: avSession.AVSessionDescriptor) => {
            });
            avSession.off('sessionCreate');
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## avSession.off('sessionDestroy') 

off(type: 'sessionDestroy', callback?: (session: AVSessionDescriptor) => void): void 

Unsubscribes from session destroy events. After unsubscription, the event will no longer be received.

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name  | Type       | Mandatory| Description                     |
| -------- | -----------| ---- | -------------------------|
| type     | string     | Yes  | Event type, which is **'sessionDestroy'** in this case.|
| callback | (session: [AVSessionDescriptor](arkts-apis-avsession-i.md#avsessiondescriptor-23)) => void | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **session** parameter in the callback describes a media session. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message| 
| -------- | ---------------------------------------- | 
| 202 | Not System App. | 
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. | 
| 6600101  | Session service exception. | 

**Example**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
        Text(this.message)
          .onClick(()=>{
            avSession.on('sessionDestroy', (descriptor: avSession.AVSessionDescriptor) => {
            });
            avSession.off('sessionDestroy');
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## avSession.off('topSessionChange') 

off(type: 'topSessionChange', callback?: (session: AVSessionDescriptor) => void): void 

Unsubscribes from the top session change events. After unsubscription, the event will no longer be received.

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name  | Type             | Mandatory| Description                       |
| -------- | -----------------| ---- | ---------------------------- |
| type     | string           | Yes  | Event type, which is **'topSessionChange'** in this case.|
| callback | (session: [AVSessionDescriptor](arkts-apis-avsession-i.md#avsessiondescriptor-23)) => void | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **session** parameter in the callback describes a media session. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message| 
| -------- | ---------------------------------------- | 
| 202 | Not System App. | 
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. | 
| 6600101  | Session service exception. | 

**Example**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
        Text(this.message)
          .onClick(()=>{
            avSession.on('topSessionChange', (descriptor: avSession.AVSessionDescriptor) => {
            });
            avSession.off('topSessionChange');
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## avSession.on('sessionServiceDie')

on(type: 'sessionServiceDie', callback: () => void): void

Subscribes to session service death events. Upon receiving this event, the application can clear resources.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**System API**: This is a system API.

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| type     | string               | Yes  | Event type. The event **'sessionServiceDie'** is triggered when the session service dies.|
| callback | callback: () => void | Yes  | Callback used for subscription. If the subscription is successful, **err** is **undefined**; otherwise, **err** is an error object.                               |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avSession.on('sessionServiceDie', () => {
  console.info('on sessionServiceDie  : session is  Died ');
});
```

## avSession.off('sessionServiceDie')

off(type: 'sessionServiceDie', callback?: () => void): void

Unsubscribes from session service death events.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**System API**: This is a system API.

**Parameters**

| Name   | Type                   | Mandatory |      Description                                              |
| ------   | ---------------------- | ---- | ------------------------------------------------------- |
| type     | string                 | Yes   | Event type. The event **'sessionServiceDie'** is triggered when the session service dies.|
| callback | callback: () => void   | No   | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.           |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avSession.off('sessionServiceDie');
```


## avSession.on('distributedSessionChange')<sup>18+</sup>

on(type: 'distributedSessionChange', distributedSessionType: DistributedSessionType, callback: Callback<Array\<AVSessionController>>): void

Subscribes to the latest distributed remote session change events.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                                                 | Mandatory| Description                                                                      |
| -------- |-------------------------------------------------------------------------------------| ---- |--------------------------------------------------------------------------|
| type     | string                                                                              | Yes  | Event type. The event **'distributedSessionChange'** is triggered when the latest distributed session is changed.|
| distributedSessionType     | [DistributedSessionType](#distributedsessiontype18)             | Yes  | Remote session type.                                                                 |
| callback | Callback<Array<[AVSessionController](arkts-apis-avsession-AVSessionController.md)\>> | Yes  | Callback used to return an array of session controller instances of the corresponding type. You can view the session ID, send commands and events to the session, and obtain metadata and playback status information.           |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID  | Error Message                                                                                             |
|---------|---------------------------------------------------------------------------------------------------|
| 202     | Not System App. |
| 6600101 | Session service exception.                                                                        |

**Example**

```ts
avSession.on('distributedSessionChange', avSession.DistributedSessionType.TYPE_SESSION_REMOTE, (sessionControllers: Array<avSession.AVSessionController>) => {
  console.info(`on distributedSessionChange size: ${sessionControllers.length}`);
});
```


## avSession.off('distributedSessionChange')<sup>18+</sup>

off(type: 'distributedSessionChange', distributedSessionType: DistributedSessionType, callback?: Callback<Array\<AVSessionController>>): void

Unsubscribes from the latest distributed remote session change events.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                                                 | Mandatory| Description                                                           |
| -------- |-------------------------------------------------------------------------------------|----|---------------------------------------------------------------|
| type     | string                                                                              | Yes | Event type. The event **'distributedSessionChange'** is triggered when the latest distributed session is changed.                   |
| distributedSessionType     | [DistributedSessionType](#distributedsessiontype18)             | Yes | Remote session type.                                                      |
| callback | Callback<Array<[AVSessionController](arkts-apis-avsession-AVSessionController.md)\>> | No | Callback used to return an array of session controller instances of the corresponding type. You can view the session ID, send commands and events to the session, and obtain metadata and playback status information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID  | Error Message                                                                                             |
|---------|---------------------------------------------------------------------------------------------------|
| 202     | Not System App. |
| 6600101 | Session service exception.                                                                        |

**Example**

```ts
avSession.off('distributedSessionChange', avSession.DistributedSessionType.TYPE_SESSION_REMOTE);
```

## avSession.sendSystemAVKeyEvent

sendSystemAVKeyEvent(event: KeyEvent, callback: AsyncCallback\<void>): void

Sends a system key event to the top session. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES (available only to system applications)

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                 |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------- |
| event    | [KeyEvent](../apis-input-kit/js-apis-keyevent.md#keyevent) | Yes  | Key event.                           |
| callback | AsyncCallback\<void>                                         | Yes  | Callback used to return the result. If the event is sent, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600105  | Invalid session command. |

**Example**

```ts
import { KeyEvent } from '@kit.InputKit';

let keyItem: KeyEvent.Key = {code:0x49, pressedTime:2, deviceId:0};
let event: KeyEvent.KeyEvent = {id:1, deviceId:0, actionTime:1, screenId:1, windowId:1, action:2, key:keyItem, unicodeChar:0, keys:[keyItem], ctrlKey:false, altKey:false, shiftKey:false, logoKey:false, fnKey:false, capsLock:false, numLock:false, scrollLock:false};

avSession.sendSystemAVKeyEvent(event, () => {
    console.info('Succeeded in sending system AV key event.');
});
```

## avSession.sendSystemAVKeyEvent

sendSystemAVKeyEvent(event: KeyEvent): Promise\<void>

Sends a system key event to the top session. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES (available only to system applications)

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name| Type                           | Mandatory| Description      |
| ------ | ------------------------------- | ---- | ---------- |
| event  | [KeyEvent](../apis-input-kit/js-apis-keyevent.md#keyevent) | Yes  | Key event.|


**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the event is sent, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600105  | Invalid session command. |

**Example**

```ts
import { KeyEvent } from '@kit.InputKit';

let keyItem: KeyEvent.Key = {code:0x49, pressedTime:2, deviceId:0};
let event: KeyEvent.KeyEvent = {id:1, deviceId:0, actionTime:1, screenId:1, windowId:1, action:2, key:keyItem, unicodeChar:0, keys:[keyItem], ctrlKey:false, altKey:false, shiftKey:false, logoKey:false, fnKey:false, capsLock:false, numLock:false, scrollLock:false};

avSession.sendSystemAVKeyEvent(event).then(() => {
  console.info('Succeeded in sending system AV key event.');
});
```

## avSession.sendSystemControlCommand

sendSystemControlCommand(command: AVControlCommand, callback: AsyncCallback\<void>): void

Sends a system control command to the top session. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES (available only to system applications)

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name  | Type                                 | Mandatory| Description                                 |
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| command  | [AVControlCommand](arkts-apis-avsession-i.md#avcontrolcommand10) | Yes  | Command to send.  |
| callback | AsyncCallback\<void>                  | Yes  | Callback used to return the result. If the command is sent, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600105  | Invalid session command. |
| 6600107  | Too many commands or events. |

**Example**

```ts
let cmd : avSession.AVControlCommandType = 'play';
// let cmd : avSession.AVControlCommandType = 'pause';
// let cmd : avSession.AVControlCommandType = 'stop';
// let cmd : avSession.AVControlCommandType = 'playNext';
// let cmd : avSession.AVControlCommandType = 'playPrevious';
// let cmd : avSession.AVControlCommandType = 'fastForward';
// let cmd : avSession.AVControlCommandType = 'rewind';
let avcommand: avSession.AVControlCommand = {command:cmd};
// let cmd : avSession.AVControlCommandType = 'seek';
// let avcommand = {command:cmd, parameter:10};
// let cmd : avSession.AVControlCommandType = 'setSpeed';
// let avcommand = {command:cmd, parameter:2.6};
// let cmd : avSession.AVControlCommandType = 'setLoopMode';
// let avcommand = {command:cmd, parameter:avSession.LoopMode.LOOP_MODE_SINGLE};
// let cmd : avSession.AVControlCommandType = 'toggleFavorite';
// let avcommand = {command:cmd, parameter:"false"};
avSession.sendSystemControlCommand(avcommand, () => {
    console.info('Succeeded in sending system control command.');
});
```

## avSession.sendSystemControlCommand

sendSystemControlCommand(command: AVControlCommand): Promise\<void>

Sends a system control command to the top session. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES (available only to system applications)

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name | Type                                 | Mandatory| Description                               |
| ------- | ------------------------------------- | ---- | ----------------------------------- |
| command | [AVControlCommand](arkts-apis-avsession-i.md#avcontrolcommand10) | Yes  | Command to send.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the command is sent, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600105  | Invalid session command. |
| 6600107  | Too many commands or events. |

**Example**

```ts

let cmd : avSession.AVControlCommandType = 'play';
// let cmd : avSession.AVControlCommandType = 'pause';
// let cmd : avSession.AVControlCommandType = 'stop';
// let cmd : avSession.AVControlCommandType = 'playNext';
// let cmd : avSession.AVControlCommandType = 'playPrevious';
// let cmd : avSession.AVControlCommandType = 'fastForward';
// let cmd : avSession.AVControlCommandType = 'rewind';
let avcommand: avSession.AVControlCommand = {command:cmd};
// let cmd : avSession.AVControlCommandType = 'seek';
// let avcommand = {command:cmd, parameter:10};
// let cmd : avSession.AVControlCommandType = 'setSpeed';
// let avcommand = {command:cmd, parameter:2.6};
// let cmd : avSession.AVControlCommandType = 'setLoopMode';
// let avcommand = {command:cmd, parameter:avSession.LoopMode.LOOP_MODE_SINGLE};
// let cmd : avSession.AVControlCommandType = 'toggleFavorite';
// let avcommand = {command:cmd, parameter:"false"};
avSession.sendSystemControlCommand(avcommand).then(() => {
  console.info('Succeeded in sending system control command.');
});
```

## ProtocolType<sup>10+</sup>

Enumerates the protocol types supported by the remote device.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

| Name                       | Value  | Description        |
| --------------------------- | ---- | ----------- |
| TYPE_CAST_PLUS_MIRROR      | 1    | Cast+ mirror mode.<br> **System API**: This is a system API.|

## avSession.startCastDeviceDiscovery<sup>10+</sup>

startCastDeviceDiscovery(callback: AsyncCallback\<void>): void

Starts cast-enabled device discovery. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type                                 | Mandatory| Description                                 |
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| callback | AsyncCallback\<void>                  | Yes  | Callback used to return the result. If the command is sent and device discovery starts, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202 | Not System App. |

**Example**

```ts

avSession.startCastDeviceDiscovery(() => {
    console.info('Succeeded in starting cast device discovery.');
});
```

## DistributedSessionType<sup>18+</sup>

Enumerates the session types supported by the remote distributed device.

**System capability**: SystemCapability.Multimedia.AVSession.Message

**System API**: This is a system API.

| Name                                    | Value| Description                       |
|----------------------------------------|---|---------------------------|
| TYPE_SESSION_REMOTE      | 0 | Session on the remote device.|
| TYPE_SESSION_MIGRATE_IN  | 1 | Session migrated to the local device.|
| TYPE_SESSION_MIGRATE_OUT | 2 | Session migrated to the remote device.|

## avSession.startCastDeviceDiscovery<sup>10+</sup>

startCastDeviceDiscovery(filter: number, callback: AsyncCallback\<void>): void

Starts cast-enabled device discovery with filter criteria specified. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type                                 | Mandatory| Description                                 |
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| filter | number | Yes| Filter criteria for device discovery. The value consists of **ProtocolType**s.|
| callback | AsyncCallback\<void>                  | Yes  | Callback used to return the result. If the command is sent and device discovery starts, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**Example**

```ts

let filter = 2;
avSession.startCastDeviceDiscovery(filter, () => {
    console.info('Succeeded in starting cast device discovery.');
});
```

## avSession.startCastDeviceDiscovery<sup>10+</sup>

startCastDeviceDiscovery(filter?: number, drmSchemes?: Array\<string>): Promise\<void>

Starts cast-enabled device discovery. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type                                 | Mandatory| Description                                 |
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| filter | number | No| Filter criteria for device discovery. The value consists of **ProtocolType**s.|
| drmSchemes | Array\<string> | No| Filter criteria for discovering devices that support DRM resource playback. The value consists of DRM UUIDs.<br>This parameter is supported since API version 12.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the command is sent and device discovery starts, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**Example**

```ts

let filter = 2;
let drmSchemes = ['3d5e6d35-9b9a-41e8-b843-dd3c6e72c42c'];
avSession.startCastDeviceDiscovery(filter, drmSchemes).then(() => {
  console.info('Succeeded in starting cast device discovery.');
});
```

## avSession.stopCastDeviceDiscovery<sup>10+</sup>

stopCastDeviceDiscovery(callback: AsyncCallback\<void>): void

Stops cast-enabled device discovery. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type                                 | Mandatory| Description                                 |
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| callback | AsyncCallback\<void>                  | Yes  | Callback used to return the result. If device discovery stops, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202 | Not System App. |

**Example**

```ts

avSession.stopCastDeviceDiscovery(() => {
    console.info('Succeeded in stopping cast device discovery.');
});
```

## avSession.stopCastDeviceDiscovery<sup>10+</sup>

stopCastDeviceDiscovery(): Promise\<void>

Stops cast-enabled device discovery. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If device discovery stops, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202 | Not System App. |

**Example**

```ts

avSession.stopCastDeviceDiscovery().then(() => {
  console.info('Succeeded in stopping cast device discovery.');
});
```

## avSession.setDiscoverable<sup>10+</sup>

setDiscoverable(enable: boolean, callback: AsyncCallback\<void>): void

Sets whether to allow the device discoverable. A discoverable device can be used as the cast receiver. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type                                 | Mandatory| Description                                 |
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| enable | boolean | Yes| Whether to allow the device discoverable. **true** if discoverable, **false** otherwise.|
| callback | AsyncCallback\<void>                  | Yes  | Callback used to return the result. If the setting is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**Example**

```ts

avSession.setDiscoverable(true, () => {
    console.info('Succeeded in setting discoverable.');
});
```

## avSession.setDiscoverable<sup>10+</sup>

setDiscoverable(enable: boolean): Promise\<void>

Sets whether to allow the device discoverable. A discoverable device can be used as the cast receiver. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type                                 | Mandatory| Description                                 |
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| enable | boolean | Yes| Whether to allow the device discoverable. **true** if discoverable, **false** otherwise.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**Example**

```ts

avSession.setDiscoverable(true).then(() => {
  console.info('Succeeded in setting discoverable.');
});
```

## avSession.on('deviceAvailable')<sup>10+</sup>

on(type: 'deviceAvailable', callback: (device: OutputDeviceInfo) => void): void

Subscribes to device discovery events.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| type     | string               | Yes  | Event type. The event **'deviceAvailable'** is triggered when a device is discovered.|
| callback | (device: [OutputDeviceInfo](arkts-apis-avsession-i.md#outputdeviceinfo10)) => void | Yes  | Callback used for subscription. If the subscription is successful, **err** is **undefined**; otherwise, **err** is an error object.                               |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
let castDevice: avSession.OutputDeviceInfo;
avSession.on('deviceAvailable', (device: avSession.OutputDeviceInfo) => {
  castDevice = device;
  console.info(`on deviceAvailable  : ${device} `);
});
```

## avSession.off('deviceAvailable')<sup>10+</sup>

off(type: 'deviceAvailable', callback?: (device: OutputDeviceInfo) => void): void

Unsubscribes from device discovery events.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name   | Type                   | Mandatory |      Description                                              |
| ------   | ---------------------- | ---- | ------------------------------------------------------- |
| type     | string                 | Yes   | Event type. The event **'deviceAvailable'** is triggered when a device is discovered.|
| callback     | (device: [OutputDeviceInfo](arkts-apis-avsession-i.md#outputdeviceinfo10)) => void                 | No   | Callback used to return the device information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
avSession.off('deviceAvailable');
```

## avSession.on('deviceOffline')<sup>11+</sup>

on(type: 'deviceOffline', callback: (deviceId: string) => void): void

Subscribes to device offline events.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | -------------------- | ---- | ------------------------------------------------------------ |
| type     | string               | Yes  | Event type. The event **'deviceOffline'** is triggered when a device gets offline.|
| callback | (deviceId: string) => void | Yes  | Callback used to return the result. The **deviceId** parameter in the callback indicates the device ID. If the subscription is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
let castDeviceId: string;
avSession.on('deviceOffline', (deviceId: string) => {
  castDeviceId = deviceId;
  console.info(`on deviceOffline  : ${deviceId} `);
});
```

## avSession.off('deviceOffline')<sup>11+</sup>

off(type: 'deviceOffline', callback?: (deviceId: string) => void): void

Unsubscribes from device offline events.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name   | Type                   | Mandatory |      Description                                              |
| ------   | ---------------------- | ---- | ------------------------------------------------------- |
| type     | string                 | Yes   | Event type, which is **'deviceOffline'** in this case.|
| callback | (deviceId: string) => void | No  | Callback used to return the result. The **deviceId** parameter in the callback indicates the device ID. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**Example**

```ts
avSession.off('deviceOffline');
```

## avSession.getAVCastController<sup>10+</sup>

getAVCastController(sessionId: string, callback: AsyncCallback\<AVCastController>): void

Obtains the cast controller when a casting connection is set up. This API uses an asynchronous callback to return the result.

This API can be called on both the local and remote devices. You can use the API to obtain the same controller to control audio playback after cast.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES

**System API**: This is a system API.

**Parameters**

| Name   | Type                                                       | Mandatory| Description                                                        |
| --------- | ----------------------------------------------------------- | ---- |------------------------------------------------------------ |
| sessionId | string                    | Yes  |Session ID.|
| callback  | AsyncCallback<[AVCastController](#avcastcontroller10)\> | Yes  | Callback used to return the cast controller.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception |
| 6600102  | session does not exist |

**Example**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context = this.getUIContext().getHostContext() as Context;
          let sessionId: string = ""; // Used as an input parameter of subsequent functions.

          let avCastController: avSession.AVCastController;
          avSession.getAVCastController(sessionId, (avcontroller: avSession.AVCastController) => {
              avCastController = avcontroller;
              console.info('Succeeded in getting AV cast controller.');
          });
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## avSession.getAVCastController<sup>10+</sup>

getAVCastController(sessionId: string): Promise\<AVCastController>

Obtains the cast controller when a casting connection is set up. This API uses a promise to return the result.

This API can be called on both the local and remote devices. You can use the API to obtain the same controller to control audio playback after cast.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES

**System API**: This is a system API.

**Parameters**

| Name   | Type                      | Mandatory| Description                                                        |
| --------- | ------------------------- | ---- | ------------------------------------------------------------ |
| sessionId | string                    | Yes  |Session ID.|

**Return value**

| Type                                                       | Description            |
| --------- | ------------------------------------------------------------ |
| Promise<[AVCastController](#avcastcontroller10)\>  | Promise used to return the cast controller.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | server exception |
| 6600102  | The session does not exist |

**Example**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(() => {
          let currentAVSession: avSession.AVSession | undefined = undefined;
          let tag = "createNewSession";
          let context = this.getUIContext().getHostContext() as Context;
          let sessionId: string = ""; // Used as an input parameter of subsequent functions.

          let avCastController: avSession.AVCastController;
          avSession.getAVCastController(sessionId).then((avcontroller: avSession.AVCastController) => {
            avCastController = avcontroller;
            console.info('Succeeded in getting AV cast controller.');
          });
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## avSession.startCasting<sup>10+</sup>

startCasting(session: SessionToken, device: OutputDeviceInfo, callback: AsyncCallback\<void>): void

Starts casting. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES (available only to system applications)

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type                                 | Mandatory| Description                                 |
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| session      | [SessionToken](#sessiontoken) | Yes  | Session token.  |
| device | [OutputDeviceInfo](arkts-apis-avsession-i.md#outputdeviceinfo10)                        | Yes  | Device-related information.|
| callback | AsyncCallback\<void>                  | Yes  | Callback used to return the result. If the command is sent and casting starts, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600108 | Device connection failed.       |

**Example**

```ts

let myToken: avSession.SessionToken = {
  sessionId: sessionId,
}
let castDevice: avSession.OutputDeviceInfo | undefined = undefined;
avSession.on('deviceAvailable', (device: avSession.OutputDeviceInfo) => {
  castDevice = device;
  console.info(`on deviceAvailable  : ${device} `);
  if (castDevice !== undefined) {
    avSession.startCasting(myToken, castDevice, () => {
        console.info('Succeeded in starting casting.');
    });
  }
});
```


## avSession.startCasting<sup>10+</sup>

startCasting(session: SessionToken, device: OutputDeviceInfo): Promise\<void>

Starts casting. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES (available only to system applications)

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type                                 | Mandatory| Description                                 |
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| session      | [SessionToken](#sessiontoken) | Yes  | Session token.  |
| device | [OutputDeviceInfo](arkts-apis-avsession-i.md#outputdeviceinfo10)                        | Yes  | Device-related information.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the command is sent and casting starts, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| 6600101  | Session service exception. |
| 6600108 | Device connection failed.       |

**Example**

```ts

let myToken: avSession.SessionToken = {
  sessionId: sessionId,
}
let castDevice: avSession.OutputDeviceInfo | undefined = undefined;
avSession.on('deviceAvailable', (device: avSession.OutputDeviceInfo) => {
  castDevice = device;
  console.info(`on deviceAvailable  : ${device} `);
  if (castDevice !== undefined) {
    avSession.startCasting(myToken, castDevice).then(() => {
      console.info('Succeeded in starting casting.');
    });
  }
});
```

## avSession.stopCasting<sup>10+</sup>

stopCasting(session: SessionToken, callback: AsyncCallback\<void>): void

Stops castings. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type                                 | Mandatory| Description                                 |
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| session      | [SessionToken](#sessiontoken) | Yes  | Session token.  |
| callback | AsyncCallback\<void>                  | Yes  | Callback used to return the result. If casting stops, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| 6600109  | The remote connection is not established. |

**Example**

```ts

let myToken: avSession.SessionToken = {
  sessionId: sessionId,
}
avSession.stopCasting(myToken, () => {
    console.info('Succeeded in stopping casting.');
});
```

## avSession.stopCasting<sup>10+</sup>

stopCasting(session: SessionToken): Promise\<void>

Stops castings. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type                                 | Mandatory| Description                                 |
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| session      | [SessionToken](#sessiontoken) | Yes  | Session token.  |

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If casting stops, no value is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| 6600109  | The remote connection is not established. |

**Example**

```ts

let myToken: avSession.SessionToken = {
  sessionId: sessionId,
}
avSession.stopCasting(myToken).then(() => {
  console.info('Succeeded in stopping casting.');
});
```

## avSession.startDeviceLogging<sup>13+</sup>

startDeviceLogging(url: string, maxSize?: number): Promise\<void>

Starts to write device logs to a file. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type                                 | Mandatory| Description                                 |
| -------- | ------------------------------------- | ---- | ------------------------------------- |
| url | string                   | Yes  | Target file descriptor (unique identifier used to open a file).|
| maxSize | number                   | No  | Maximum size of the log file, in KB.|

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If the device logs are written to the file successfully, no result is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202        | Not System App. |
| 401        | Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 6600101    | Session service exception. |
| 6600102    | The session does not exist. |

**Example**

```ts
import { fileIo } from '@kit.CoreFileKit';

let file = await fileIo.open("filePath");
let url = file.fd.toString();
avSession.startDeviceLogging(url, 2048).then(() => {
  console.info('Succeeded in starting device logging.');
})
```

## avSession.stopDeviceLogging<sup>13+</sup>

stopDeviceLogging(): Promise\<void>

Stops device logging. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Return value**

| Type          | Description                         |
| -------------- | ----------------------------- |
| Promise\<void> | Promise used to return the result. If device logging is stopped, no result is returned; otherwise, an error object is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202        | Not System App. |
| 6600101    | Session service exception. |
| 6600102    | The session does not exist. |

**Example**

```ts
avSession.stopDeviceLogging().then(() => {
  console.info('Succeeded in stopping casting.');
});
```

## avSession.on('deviceLogEvent')<sup>13+</sup>

on(type: 'deviceLogEvent', callback: Callback\<DeviceLogEventCode>): void

Subscribes to device log events.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- |------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type, which is **'deviceLogEvent'** in this case.|
| callback | (callback: [DeviceLogEventCode](#devicelogeventcode13)) => void        | Yes  | Callback function, in which **DeviceLogEventCode** is the return value of the current device log event.                     |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202        | Not System App. |
| 401        | Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 6600101    | Session service exception. |
| 6600102    | The session does not exist. |

**Example**

```ts
avSession.on('deviceLogEvent', (eventCode: avSession.DeviceLogEventCode) => {
  console.info(`on deviceLogEvent code : ${eventCode}`);
});
```

## avSession.off('deviceLogEvent')<sup>13+</sup>

off(type: 'deviceLogEvent', callback?: Callback\<DeviceLogEventCode>): void

Unsubscribes from device log events.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- |------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type, which is **'deviceLogEvent'** in this case.|
| callback | (callback: [DeviceLogEventCode](#devicelogeventcode13)) => void        | No | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.           |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202        | Not System App. |
| 401        | Parameter check failed. 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 6600101    | Session service exception. |
| 6600102    | The session does not exist. |

**Example**

```ts
avSession.off('deviceLogEvent');
```

## DeviceState<sup>20+</sup>

Describes the connection state of the casting device.

**System API**: This is a system API.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

| Name           | Type  | Read-Only|  Optional| Description        |
| :------------- | :----- | :--- | :--- | :----------- |
| deviceId       | string | Yes  | No   | ID of the casting device.      |
| deviceState    | number | Yes  | No   | Connection status code of the casting device.|
| reasonCode     | number | Yes  | No   | Connection error code of the casting device.|
| radarErrorCode | number | Yes  | No   | System radar error code.|

## avSession.on('deviceStateChanged')<sup>20+</sup>

on(type: 'deviceStateChanged', callback: Callback\<DeviceState\>): void

Subscribes to casting device connection state events.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                         | Mandatory | Description                                                        |
| -------- | ------------------------------------------------------------ | ---- |------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type, which is **'deviceStateChanged'** in this case. This event is triggered when the connection state of the casting device changes.|
| callback | (callback: [DeviceState](#devicestate20)) => void            | Yes  | Callback function, in which **DeviceState** contains the casting device ID, connection status code, connection error code, and system radar error code.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201        | Permission denied. |
| 202        | Not System App. |

**Example**

```ts
avSession.on('deviceStateChanged', (state: avSession.DeviceState) => {
  console.info(`on deviceStateChanged state, deviceId=${state.deviceId}, connect status=${state.deviceState},
    reasonCode=${state.reasonCode}, radarErrorCode=${state.radarErrorCode}`)
})
```

## avSession.off('deviceStateChanged')<sup>20+</sup>

off(type: 'deviceStateChanged', callback?: Callback\<DeviceState>): void

Unsubscribes from casting device connection state events.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**Parameters**

| Name  | Type                                                         | Mandatory | Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type, which is **'deviceStateChanged'** in this case. This event is triggered when the connection state of the casting device changes.|
| callback | (callback: [DeviceState](#devicestate20)) => void            | No  | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. The **callback** parameter is optional. If it is not specified, all the subscriptions to the specified event are canceled for this session.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201        | Permission denied. |
| 202        | Not System App. |

**Example**

```ts
avSession.off('deviceStateChanged');
```

## AVCastController<sup>10+</sup>

After a casting connection is set up, you can call [avSession.getAVCastController](arkts-apis-avsession-AVSession.md#getavcastcontroller10) to obtain the cast controller. Through the controller, you can query the session ID, send commands and events to a session, and obtain session metadata and playback state information.

### setDisplaySurface<sup>10+</sup>

setDisplaySurface(surfaceId: string): Promise\<void>

Sets the surface ID for playback, which is used at the cast receiver (sink). This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type                                               | Mandatory| Description                        |
| -------- | --------------------------------------------------- | ---- | ---------------------------- |
| surfaceId | string | Yes  | Surface ID.|

**Return value**

| Type                                         | Description                       |
| --------------------------------------------- | --------------------------- |
| Promise\<void> | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600109  | The remote connection is not established. |

**Example**

```ts
import { media } from '@kit.MediaKit';

let surfaceID: string = '';
media.createAVRecorder().then((avRecorder) => {
  avRecorder.getInputSurface((surfaceId: string) => {
    console.info('Succeeded in getting input surface.');
    surfaceID = surfaceId;
    if (surfaceID) {
      avCastController.setDisplaySurface(surfaceID).then(() => {
        console.info('Succeeded in setting display surface.');
      });
    }
  });
})
```

### setDisplaySurface<sup>10+</sup>

setDisplaySurface(surfaceId: string, callback: AsyncCallback\<void>): void

Sets the surface ID for playback, which is used at the cast receiver (sink). This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type                                               | Mandatory| Description                        |
| -------- | --------------------------------------------------- | ---- | ---------------------------- |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result.|
| surfaceId | string | Yes  | Surface ID.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 202 | Not System App. |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600109  | The remote connection is not established. |

**Example**

```ts
import { media } from '@kit.MediaKit';

let surfaceID: string = '';
media.createAVRecorder().then((avRecorder) => {
  avRecorder.getInputSurface((surfaceId: string) => {
    console.info('Succeeded in getting input surface.');
    surfaceID = surfaceId;
    if (surfaceID) {
      avCastController.setDisplaySurface(surfaceID, () => {
          console.info('Succeeded in setting display surface.');
      });
    }
  });
})
```

### on('videoSizeChange')<sup>12+</sup>

on(type: 'videoSizeChange', callback: (width:number, height:number) => void): void

Subscribes to video size change events.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- |---- |
| type     | string      | Yes  | Event type. The event **'videoSizeChange'** is triggered when the video size changes.|
| callback | (width:number, height:number) => void    | Yes  | Callback used to return the video width and height.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.on('videoSizeChange', (width: number, height: number) => {
  console.info(`width : ${width} `);
  console.info(`height: ${height} `);
});
```

### off('videoSizeChange')<sup>12+</sup>

off(type: 'videoSizeChange'): void

Unsubscribes from video size changes.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

**Parameters**

| Name  | Type    | Mandatory| Description     |
| -------- | ------------------------------------------------------------ | ---- |---- |
| type     | string  | Yes  | Event type, which is **'videoSizeChange'** in this case.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| 6600101  | Session service exception. |

**Example**

```ts
avCastController.off('videoSizeChange');
```

## avSession.onActiveSessionChanged<sup>23+</sup>

function onActiveSessionChanged(callback: Callback<Array\<AVSessionDescriptor>>): void

Subscribes to changes to the session that can be displayed in the system control entry. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | --------------------| ---- | ------------------------------------------------------------ |
| callback | Callback\<Array\<[AVSessionDescriptor](#avsessiondescriptor)\>\> | Yes  | Callback used to return the sessions that can be displayed in the system control entry.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
| 202 |  Not System App. |
| 6600101  | Session service exception. |

**Example**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(() => {
          avSession.onActiveSessionChanged((descs: Array<avSession.AVSessionDescriptor>) => {
            descs.forEach((desc, index) => {
              console.info(`=== Session ${index + 1}/${descs.length} ===`);
              console.info(`on onActiveSessionChanged : isActive : ${desc.isActive}`);
              console.info(`on onActiveSessionChanged : type : ${desc.type}`);
              console.info(`on onActiveSessionChanged : sessionTag : ${desc.sessionTag}`);
            });
          });
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## avSession.offActiveSessionChanged<sup>23+</sup>

function offActiveSessionChanged(callback?: Callback<Array\<AVSessionDescriptor>>): void

Unsubscribes from changes to the session that can be displayed in the system control entry. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | --------------------| ---- | ------------------------------------------------------------ |
| callback | Callback\<Array\<[AVSessionDescriptor](#avsessiondescriptor)\>\> | No  | Callback used for unsubscription. If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>This parameter is optional. If it is not specified, the change events of all sessions that can be displayed in the system control entry are unsubscribed. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
| 202 |  Not System App. |
| 6600101  | Session service exception. |

**Example**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(() => {
          avSession.onActiveSessionChanged((descriptors: Array<avSession.AVSessionDescriptor>) => {
          });
          avSession.offActiveSessionChanged();
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## AVQueueInfo<sup>11+</sup>

Defines the attributes of a playlist.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**System API**: This is a system API.

| Name           | Type                     | Read-Only| Optional| Description                                                                 |
| --------------- |-------------------------| ---- |-------|-------------------------------------------------------------- |
| bundleName      | string                  | No| No  | Bundle name of the application to which the playlist belongs.                                                       |
| avQueueName     | string                  | No| No  | Playlist name.                                                   |
| avQueueId       | string                  | No| No  | Unique ID of the playlist.                                              |
| avQueueImage    | image.PixelMap &#124; string |No| No  | Cover image of the playlist, which can be pixel data of an image or an image path (local path or Internet path).    |
| lastPlayedTime  | number                  | No|Yes | Last time when the playlist is played.                                                       |

## DeviceInfo<sup>10+</sup>

Describes the information related to the output device.

| Name      | Type          | Read-Only| Optional| Description                  |
| ---------- | -------------- | ---- | ----|------------------ |
| ipAddress | string | No| Yes | IP address of the output device.<br>**System API**: This is a system API.<br> **System capability**: SystemCapability.Multimedia.AVSession.AVCast    |
| providerId | number | No   | Yes| Vendor of the output device.<br>**System API**: This is a system API.<br> **System capability**: SystemCapability.Multimedia.AVSession.AVCast   |
| authenticationStatus<sup>11+</sup> | number | No | Yes| Whether the output device is trusted. The default value is **0**, indicating that the device is untrusted. The value **1** means that the device is trusted.<br>**System API**: This is a system API.<br> **System capability**: SystemCapability.Multimedia.AVSession.AVCast   |
| networkId<sup>13+</sup> | string | No |Yes| Network ID of the output device.<br>**System API**: This is a system API.<br> **System capability**: SystemCapability.Multimedia.AVSession.AVCast|
|isLegacy<sup>13+</sup> | boolean | No| Yes| Whether the current device is a legacy device. **true** if it is a legacy device, **false** otherwise.<br>**System API**: This is a system API.<br> **System capability**: SystemCapability.Multimedia.AVSession.AVCast    |
|mediumTypes<sup>13+</sup>| number | No | Yes |Medium types used for device discovery.<br>1: Bluetooth Low Energy (BLE), which is used to discover and connect to Bluetooth devices.<br> 2: Constrained Application Protocol (CoAP), which is used to discover devices in a Local Area Network (LAN).<br>**System API**: This is a system API.<br> **System capability**: SystemCapability.Multimedia.AVSession.AVCast       |

## AVSessionDescriptor

Declares the session descriptor.

**System capability**: SystemCapability.Multimedia.AVSession.Manager

| Name         | Type             | Read-Only| Optional| Description |
| --------------| ---------------- | ---------------- | ---------------- |------|
| outputDevice | [OutputDeviceInfo](arkts-apis-avsession-i.md#outputdeviceinfo10)    | No| No| Information about the output device.<br>**System API**: This is a system API.<br> **System capability**: SystemCapability.Multimedia.AVSession.Manager       |

## DeviceLogEventCode<sup>13+</sup>

Enumerates the return values of device log events.

**System capability**: SystemCapability.Multimedia.AVSession.AVCast

**System API**: This is a system API.

| Name                       | Value  | Description        |
| --------------------------- | ---- | ----------- |
| DEVICE_LOG_FULL       | 1    | The log file is full.   |
| DEVICE_LOG_EXCEPTION       | 2    | An exception occurs during device logging.|

## SessionCategory<sup>22+</sup>

Enumerates the session categories in different scenarios.

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**System API**: This is a system API.

| Name               |  Value | Description        |
| --------------------| ---- | ----------- |
| CATEGORY_ACTIVE     |  1   | Session category that can be displayed in the system control entry.|
| CATEGORY_NOT_ACTIVE |  2   | Session category that cannot be displayed in the system control entry.|
| CATEGORY_ALL        |  3   | All session categories.|
