# getAVSession

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## getAVSession

```TypeScript
function getAVSession(context: Context): Promise<AVSession>
```

Get an AVSession instance if already created.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Multimedia.AVSession.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | The context of application |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AVSession](arkts-avsession-avsession-avsession-i.md)&gt; | Promise for AVSession |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
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
