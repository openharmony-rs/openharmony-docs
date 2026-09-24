# getPhotoAccessHelper (System API)

## Modules to Import

```TypeScript
import { sendablePhotoAccessHelper } from '@kit.MediaLibraryKit';
```

<a id="getphotoaccesshelper-1"></a>

## getPhotoAccessHelper

```TypeScript
function getPhotoAccessHelper(context: Context, userId: number): PhotoAccessHelper
```

Obtains a PhotoAccessHelper instance for the specified user, letting you access and modify media files in an album.

**Since:** 19

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |
| userId | number | Yes | ID of the user. |

**Return value:**

| Type | Description |
| --- | --- |
| [PhotoAccessHelper](arkts-medialibrary-sendablephotoaccesshelper-photoaccesshelper-i.md) | PhotoAccessHelper instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Called by non-system application |
| 13900020 | Invalid argument |

**Examples**

```TypeScript
// The phAccessHelper instance obtained is a global object. It is used by default in subsequent operations. If the code snippet is not added, an error will be reported indicating that phAccessHelper is not defined.
// Obtain the context from the component and ensure that the return value of this.getUiContext().getHostContext() is UIAbilityContext.
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Button("example").onClick(async () => {
        let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
        // 101 indicates the user ID of another user space.
        let phAccessHelper = sendablePhotoAccessHelper.getPhotoAccessHelper(context, 101);
      }).width('100%')
    }
    .height('90%')
  }
}
```
