# AVCastController

AVCastController definition used to implement a remote control when a cast is connected

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## setDisplaySurface

```TypeScript
setDisplaySurface(surfaceId: string, callback: AsyncCallback<void>): void
```

Set a surface instance to display playing view, used at sink side.

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| surfaceId | string | Yes | surface id, video player will use this id get a surface instance. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | A callback instance used to return when set surface completed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600109](../errorcode-avsession.md#6600109-remote-session-does-not-exist) | The remote connection is not established. |

**Examples**

```TypeScript
import { media } from '@kit.MediaKit';

let surfaceID: string = '';
media.createAVRecorder().then((avRecorder) => {
  avRecorder.getInputSurface((surfaceId: string) => {
    console.info('Succeeded in getting input surface.');
    surfaceID = surfaceId;
    if (surfaceID) {
      // Obtain the avCastController instance through avSession.getAVCastController.
      avCastController.setDisplaySurface(surfaceID).then(() => {
        console.info('Succeeded in setting display surface.');
      });
    }
  });
})
```

```TypeScript
import { media } from '@kit.MediaKit';

let surfaceID: string = '';
media.createAVRecorder().then((avRecorder) => {
  avRecorder.getInputSurface((surfaceId: string) => {
    console.info('Succeeded in getting input surface.');
    surfaceID = surfaceId;
    if (surfaceID) {
      // Obtain the avCastController instance through avSession.getAVCastController.
      avCastController.setDisplaySurface(surfaceID, () => {
          console.info('Succeeded in setting display surface.');
      });
    }
  });
})
```

## setDisplaySurface

```TypeScript
setDisplaySurface(surfaceId: string): Promise<void>
```

Set a surface instance to display playing view, used at sink side.

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.AVCast

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| surfaceId | string | Yes | surface id, video player will use this id get a surface instance. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600109](../errorcode-avsession.md#6600109-remote-session-does-not-exist) | The remote connection is not established. |

**Examples**

See [setDisplaySurface](#setdisplaysurface)
