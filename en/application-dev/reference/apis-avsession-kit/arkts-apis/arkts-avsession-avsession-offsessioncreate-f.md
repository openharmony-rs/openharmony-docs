# offSessionCreate

## Modules to Import

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## offSessionCreate

```TypeScript
function offSessionCreate(callback?: Callback<AVSessionDescriptor>): void
```

Unregister session create callback

**Since:** 23

**Required permissions:** ohos.permission.MANAGE_MEDIA_RESOURCES_FOR_PUBLIC

**System capability:** SystemCapability.Multimedia.AVSession.Manager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AVSessionDescriptor](arkts-avsession-avsession-avsessiondescriptor-i.md)&gt; | No | Used to unregister listener for ('sessionCreate') command |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | permission denied. |
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
