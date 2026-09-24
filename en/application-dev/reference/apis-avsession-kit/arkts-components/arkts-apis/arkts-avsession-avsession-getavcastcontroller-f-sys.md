# getAVCastController (System API)

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## getAVCastController

```TypeScript
function getAVCastController(sessionId: string, callback: AsyncCallback<AVCastController>): void
```

Register a callback to retrieve an avsession cast controller. This function can be used at both side to get the same controller to do the playback control.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | string | Yes | Specifies the sessionId to get controller. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AVCastController](arkts-avsession-avsession-avcastcontroller-i.md)&gt; | Yes | async callback for the AVCastController. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |

**Examples**

```TypeScript
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(async () => {
          // Obtain the descriptors of all sessions in the system.
          let descriptors = await AVSessionManager.getAllSessionDescriptors();
          if (descriptors.length === 0) {
            console.error(`No session in system, can not create controller.`);
            return;
          }
          // Obtain the session ID of the target session to create a controller.
          let sessionId = descriptors[0].sessionId;

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


<a id="getavcastcontroller-2"></a>

## getAVCastController

```TypeScript
function getAVCastController(sessionId: string): Promise<AVCastController>
```

Get the current session's remote controller client. If the avsession is not under casting state, the controller will return null.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_MEDIA_RESOURCES

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | string | Yes | Specifies the sessionId to get controller. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVCastController](arkts-avsession-avsession-avcastcontroller-i.md)&gt; | Promise for the AVCastController |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |
| [6600102](../errorcode-avsession.md#6600102-session-does-not-exist) | The session does not exist. |

**Examples**

```TypeScript
import { avSession } from '@kit.AVSessionKit';

@Entry
@Component
struct Index {
  @State message: string = 'hello world';

  build() {
    Column() {
      Text(this.message)
        .onClick(async () => {
          // Obtain the descriptors of all sessions in the system.
          let descriptors = await AVSessionManager.getAllSessionDescriptors();
          if (descriptors.length === 0) {
            console.error(`No session in system, can not create controller.`);
            return;
          }
          // Obtain the session ID of the target session to create a controller.
          let sessionId = descriptors[0].sessionId;

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
