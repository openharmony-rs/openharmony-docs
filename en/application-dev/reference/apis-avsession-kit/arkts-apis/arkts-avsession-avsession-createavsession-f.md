# createAVSession

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## createAVSession

```TypeScript
function createAVSession(context: Context, tag: string, type: AVSessionType, callback: AsyncCallback<AVSession>): void
```

Create an AVSession instance. An ability can only create one AVSession

**Since:** 10

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | The context of application |
| tag | string | Yes | A user-defined name for this session |
| type | [AVSessionType](arkts-avsession-avsession-avsessiontype-t.md) | Yes | The type of session [AVSessionType](arkts-avsession-avsession-avsessiontype-t.md) |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AVSession](arkts-avsession-avsession-avsession-i.md)&gt; | Yes | async callback for AVSession. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

**Examples**

```TypeScript
import { avSession } from '@kit.AVSessionKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
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
              if (err) {
                console.error(`Failed to create AV session, error code: ${err.code}, error message: ${err.message}`);
                return;
              }
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


<a id="createavsession-1"></a>

## createAVSession

```TypeScript
function createAVSession(context: Context, tag: string, type: AVSessionType): Promise<AVSession>
```

Create an AVSession instance. An ability can only create one AVSession

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | The context of application |
| tag | string | Yes | A user-defined name for this session |
| type | [AVSessionType](arkts-avsession-avsession-avsessiontype-t.md) | Yes | The type of session [AVSessionType](arkts-avsession-avsession-avsessiontype-t.md) |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVSession](arkts-avsession-avsession-avsession-i.md)&gt; | Promise for AVSession |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-session-service-exception) | Session service exception. |

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
