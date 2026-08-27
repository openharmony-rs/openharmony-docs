# getPhotoAccessHelper（系统接口）

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## getPhotoAccessHelper

```TypeScript
function getPhotoAccessHelper(context: Context, userId: number): PhotoAccessHelper
```

支持跨用户获取相册管理模块的实例，用于访问和修改相册中的媒体文件。

**起始版本：** 19

**需要权限：** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的上下文。 |
| userId | number | 是 | 传入待访问用户的id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PhotoAccessHelper | 相册管理模块的实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 13900020 | Invalid argument |

**示例**

```TypeScript
// 此处获取的phAccessHelper实例为全局对象，后续使用到phAccessHelper的地方默认为使用此处获取的对象，如未添加此段代码报phAccessHelper未定义的错误请自行添加。
// 请在组件内获取context，确保this.getUiContext().getHostContext()返回结果为UIAbilityContext
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  build() {
    Row() {
      Button("example").onClick(async () => {
        let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
        // 此处101表示其他用户空间的userid
        let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context, 101);
      }).width('100%')
    }
    .height('90%')
  }
}
```
