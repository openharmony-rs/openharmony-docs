# getUserFileMgr (System API)

## Modules to Import

```TypeScript
import { userFileManager } from '@kit.CoreFileKit';
```

## getUserFileMgr

```TypeScript
function getUserFileMgr(context: Context): UserFileManager
```

Obtains a **UserFileManager** instance. This instance can be used to access and modify user media data (such as audio and video assets, images, and documents).

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [getPhotoAccessHelper](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-photoaccesshelper-getphotoaccesshelper-f.md)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Context of the ability instance. |

**Return value:**

| Type | Description |
| --- | --- |
| [UserFileManager](arkts-corefile-userfilemanager-userfilemanager-i-sys.md) | **UserFileManager** instance obtained. |

**Examples**

```TypeScript
// The userFileManager instance obtained is a global object. It is used by default in subsequent operations. If the code snippet is not added, an error will be reported indicating that mgr is not defined.
// Obtain the context from the component and ensure that the return value of this.getUiContext().getHostContext() is UIAbilityContext.
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Button("example").onClick(async () => {
        let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
        let mgr = userFileManager.getUserFileMgr(context);
      }).width('100%')
    }
    .height('90%')
  }
}
```
