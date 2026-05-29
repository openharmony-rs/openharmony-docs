# Functions
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { avSession } from '@kit.AVSessionKit';
```

## avSession.createAVSession<sup>10+</sup>

createAVSession(context: Context, tag: string, type: AVSessionType): Promise\<AVSession>

Creates an AVSession. This API uses a promise to return the result. An application process can have only one AVSession, and repeated calling of this API fails.

> **NOTE**
> 
> - During service execution, the AVSession object must be kept alive to prevent issues such as background control muting, device selection exceptions, and abnormal display of notification, lock screen, or capsule playback control widgets.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name| Type                           | Mandatory| Description                          |
| ------ | ------------------------------- | ---- | ------------------------------ |
| context| [Context](../apis-ability-kit/js-apis-inner-app-context.md) | Yes| Context of the UIAbility, which is used to obtain information about the application component.|
| tag    | string                          | Yes  | Custom session name.            |
| type   | [AVSessionType](arkts-apis-avsession-t.md#avsessiontype10) | Yes  | Session type.|

**Return value**

| Type                             | Description                                                        |
| --------------------------------- | ------------------------------------------------------------ |
| Promise<[AVSession](arkts-apis-avsession-AVSession.md)\> | Promise used to return the AVSession obtained, which can be used to obtain the session ID, set the metadata and playback state information, and send key events.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |

**Example**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  private avsessionController !: avSession.AVSessionController;
  @State message: string = 'hello world';

  build() { 
    Column() {
        Text(this.message)
          .onClick(()=>{
            let currentAVSession: avSession.AVSession;
            let tag = "createNewSession";
            let context: Context = this.getUIContext().getHostContext() as Context;
            let sessionId: string;  // Used as an input parameter of subsequent functions.

            avSession.createAVSession(context, tag, "audio").then(async (data: avSession.AVSession) => {
            currentAVSession = data;
            sessionId = currentAVSession.sessionId;
            console.info(`Succeeded in creating AV session, sessionId: ${sessionId}`);
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## avSession.createAVSession<sup>10+</sup>

createAVSession(context: Context, tag: string, type: AVSessionType, callback: AsyncCallback\<AVSession>): void

Creates an AVSession. This API uses an asynchronous callback to return the result. An application process can have only one AVSession, and repeated calling of this API fails.

> **NOTE**
> 
> - During service execution, the AVSession object must be kept alive to prevent issues such as background control muting, device selection exceptions, and abnormal display of notification, lock screen, or capsule playback control widgets.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name  | Type                                   | Mandatory| Description                                                        |
| -------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
| context| [Context](../apis-ability-kit/js-apis-inner-app-context.md) | Yes| Context of the UIAbility, which is used to obtain information about the application component.    |
| tag      | string                                  | Yes  | Custom session name.                                          |
| type     | [AVSessionType](arkts-apis-avsession-t.md#avsessiontype10)         | Yes  | Session type.                              |
| callback | AsyncCallback<[AVSession](arkts-apis-avsession-AVSession.md)\> | Yes  | Callback used to return the AVSession obtained, which can be used to obtain the session ID, set the metadata and playback state information, and send key events.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 401 |  parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| 6600101  | Session service exception. |

**Example**

```ts
import { avSession } from '@kit.AVSessionKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private avsessioncontroller !: avSession.AVSessionController;
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(()=>{
          let currentAVSession: avSession.AVSession;
          let tag = "createNewSession";
          let context: Context = this.getUIContext().getHostContext() as Context;
          let sessionId: string;  // Used as an input parameter of subsequent functions.

          avSession.createAVSession(context, tag, "audio", async (err:BusinessError, data: avSession.AVSession) => {
              currentAVSession = data;
              sessionId = currentAVSession.sessionId;
              console.info(`Succeeded in creating AV session, sessionId: ${sessionId}`);
            });
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## avSession.getAVSession<sup>22+</sup>

getAVSession(context: Context): Promise\<AVSession>

Obtains an AVSession object. This API uses a promise to return the result.

This API returns an existing AVSession object that was previously created in the current process. If no AVSession object exists, the call fails and an exception is thrown.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Parameters**

| Name| Type                           | Mandatory| Description                          |
| ------ | ------------------------------- | ---- | ------------------------------ |
| context| [Context](../apis-ability-kit/js-apis-inner-app-context.md) | Yes| Context of the UIAbility, which is used to obtain information about the application component.|

**Return value**

| Type                             | Description                                                        |
| --------------------------------- | ------------------------------------------------------------ |
| Promise<[AVSession](arkts-apis-avsession-AVSession.md)\> | Promise used to return the AVSession obtained, which can be used to obtain the session ID, set the metadata and playback state information, and send key events.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 6600101  | Session service exception. |
| 6600102  | The session does not exist. |

**Example**

```ts
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  private avsessioncontroller !: avSession.AVSessionController;
  @State message: string = 'hello world';

  build() {
    Column() {
        Text(this.message)
          .onClick(()=>{
            let currentAVSession: avSession.AVSession;
            let context: Context = this.getUIContext().getHostContext() as Context;
            let sessionId: string;  // Used as an input parameter of subsequent functions.
            let sessionTag: string;

            avSession.getAVSession(context).then(async (data: avSession.AVSession) => {
              currentAVSession = data;
              sessionId = currentAVSession.sessionId;
              sessionTag = currentAVSession.sessionTag;
              console.info(`Succeeded in getting AV session, sessionId: ${sessionId}, sessionTag: ${sessionTag}`);
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## avSession.getAllSessionDescriptors<sup>23+</sup>

getAllSessionDescriptors(): Promise\<Array\<Readonly\<AVSessionDescriptor>>>

Obtains the descriptors of all sessions that have been configured with media information and registered with the control callback. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES or ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC
A system application can apply for either **ohos.permission.MANAGE_MEDIA_RESOURCES** or **ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC**. A common application can only apply for the restricted permission **ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC**.

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**Return value**

| Type                                                        | Description                                         |
| ------------------------------------------------------------ | --------------------------------------------- |
| Promise\<Array\<Readonly\<[AVSessionDescriptor](arkts-apis-avsession-i.md#avsessiondescriptor-23)\>\>\> | Promise used to return an array of AVSessionDescriptor objects, each of which is read only.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
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
            avSession.getAllSessionDescriptors().then((descriptors: avSession.AVSessionDescriptor[]) => {
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

## avSession.createController<sup>23+</sup>

createController(sessionId: string): Promise\<AVSessionController>

Creates a session controller based on the session ID. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES or ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC
A system application can apply for either **ohos.permission.MANAGE_MEDIA_RESOURCES** or **ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC**. A common application can only apply for the restricted permission **ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC**.

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**Parameters**

| Name   | Type  | Mandatory| Description    |
| --------- | ------ | ---- | -------- |
| sessionId | string | Yes  | Session ID.|

**Return value**

| Type                                                 | Description                                                        |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| Promise<[AVSessionController](arkts-apis-avsession-AVSessionController.md)\> | Promise used to return the session controller created, which can be used to obtain the session ID,<br>send commands and events to sessions, and obtain metadata and playback state information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | Permission denied. |
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
                avSession.createController(descriptors[0]?.sessionId).then((avcontroller: avSession.AVSessionController) => {
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

## avSession.onSessionCreate<sup>23+</sup>

onSessionCreate(callback: Callback\<AVSessionDescriptor>): void

Subscribes to session creation events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**Parameters**

| Name   | Type                  | Mandatory| Description                                                        |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback\<[AVSessionDescriptor](arkts-apis-avsession-i.md#avsessiondescriptor-23)\> | Yes  | Callback used to report the session descriptor.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
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
            avSession.onSessionCreate((descriptor: avSession.AVSessionDescriptor) => {
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

## avSession.onSessionDestroy<sup>23+</sup>

onSessionDestroy(callback: Callback\<AVSessionDescriptor>): void

Subscribes to the session destroy events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**Parameters**

| Name  | Type           | Mandatory| Description                                                        |
| -------- | ---------------| ---- | ------------------------------------------------------------ |
| callback | Callback\<[AVSessionDescriptor](arkts-apis-avsession-i.md#avsessiondescriptor-23)\> | Yes  | Callback used to report the session descriptor.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied.|
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
            avSession.onSessionDestroy((descriptor: avSession.AVSessionDescriptor) => {
              console.info(`on sessionDestroy : ${descriptor.sessionId}`);
            });
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## avSession.onTopSessionChange<sup>23+</sup>

onTopSessionChange(callback: Callback\<AVSessionDescriptor>): void

Subscribes to the top session change events. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**Parameters**

| Name  | Type                | Mandatory| Description                                                        |
| -------- | --------------------| ---- | ------------------------------------------------------------ |
| callback | Callback\<[AVSessionDescriptor](arkts-apis-avsession-i.md#avsessiondescriptor-23)\> | Yes  | Callback used to report the session descriptor.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
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
            avSession.onTopSessionChange((descriptor: avSession.AVSessionDescriptor) => {
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

## avSession.offSessionCreate<sup>23+</sup>

offSessionCreate(callback?: Callback\<AVSessionDescriptor>): void

Unsubscribes from session creation events. After unsubscription, the event will no longer be received.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**Parameters**

| Name  | Type      | Mandatory| Description      |
| -------- | ----------| ---- | ----------|
| callback | Callback\<[AVSessionDescriptor](arkts-apis-avsession-i.md#avsessiondescriptor-23)\> | No  | Callback If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, events of all related sessions are unsubscribed.                              |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
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
            avSession.onSessionCreate((descriptor: avSession.AVSessionDescriptor) => {
            });
            avSession.offSessionCreate();
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## avSession.offSessionDestroy<sup>23+</sup>

offSessionDestroy(callback?: Callback\<AVSessionDescriptor>): void

Unsubscribes from session destroy events. After unsubscription, the event will no longer be received.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**Parameters**

| Name  | Type       | Mandatory| Description                     |
| -------- | -----------| ---- | -------------------------|
| callback | Callback\<[AVSessionDescriptor](arkts-apis-avsession-i.md#avsessiondescriptor-23)\> | No  | Callback If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, events of all related sessions are unsubscribed.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
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
            avSession.onSessionDestroy((descriptor: avSession.AVSessionDescriptor) => {
            });
            avSession.offSessionDestroy();
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## avSession.offTopSessionChange<sup>23+</sup>

offTopSessionChange(callback?: Callback\<AVSessionDescriptor>): void

Unsubscribes from the top session change events. After unsubscription, the event will no longer be received.

**Required permissions**: ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC

**System capability**: SystemCapability.Multimedia.AVSession.Manager

**Parameters**

| Name  | Type             | Mandatory| Description                       |
| -------- | -----------------| ---- | ---------------------------- |
| callback | Callback\<[AVSessionDescriptor](arkts-apis-avsession-i.md#avsessiondescriptor-23)\> | No  | Callback If the unsubscription is successful, **err** is **undefined**; otherwise, **err** is an error object.<br>The **callback** parameter is optional. If it is not specified, events of all related sessions are unsubscribed.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AVSession Management Error Codes](errorcode-avsession.md).

| ID| Error Message|
| -------- | ---------------------------------------- |
| 201 | permission denied. |
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
            avSession.offTopSessionChange((descriptor: avSession.AVSessionDescriptor) => {
            });
            avSession.offTopSessionChange();
          })
      }
    .width('100%')
    .height('100%')
  }
}
```

## avSession.isDesktopLyricSupported<sup>23+</sup>

isDesktopLyricSupported(): Promise\<boolean>

Checks whether the device supports the desktop lyrics feature. This API uses a promise to return the result.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.AVSession.Core

**Return value**

| Type                      | Description                              |
|----------------------------|-----------------------------------|
| Promise\<boolean> | Promise The value **true** indicates that the device supports the desktop lyrics feature, and **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [AVSession Management Error Codes](errorcode-avsession.md).

| ID  | Error Message                                            |
|---------|--------------------------------------------------------|
| 6600101 | Session service exception.                             |

**Example**

```ts
import { avSession } from '@kit.AVSessionKit';

avSession.isDesktopLyricSupported().then((isSupported: boolean) => {
  console.info(`Succeeded in checking desktop lyric supported: ${isSupported}`);
});
```
