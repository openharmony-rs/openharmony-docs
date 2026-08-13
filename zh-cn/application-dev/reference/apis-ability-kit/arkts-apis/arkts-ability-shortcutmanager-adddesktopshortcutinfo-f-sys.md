# addDesktopShortcutInfo（系统接口）

## addDesktopShortcutInfo

```TypeScript
function addDesktopShortcutInfo(shortcutInfo: ShortcutInfo, userId: int): Promise<void>
```

增加指定用户的快捷方式信息。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_SHORTCUTS

<!--Device-shortcutManager-function addDesktopShortcutInfo(shortcutInfo: ShortcutInfo, userId: int): Promise<void>--><!--Device-shortcutManager-function addDesktopShortcutInfo(shortcutInfo: ShortcutInfo, userId: int): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shortcutInfo | ShortcutInfo | 是 | 快捷方式信息。 |
| userId | int | 是 | 用户id。可以通过 [getOsAccountLocalId接口](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | The specified app index is invalid. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle is disabled. |
| [17700070](../errorcode-bundle.md#17700070-指定的快捷方式id不合法) | The specified shortcut id is illegal. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |

## 示例

ArkTS-Dyn示例:

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct ShortcutExample {
  build() {
    Column({ space: 20 }) {
      Row({ space: 20 }) {
        Button('add').onClick(() => {
          let data: shortcutManager.ShortcutInfo = {
            id: "test1",
            bundleName: "com.example.myapplication",
            moduleName: "hello",
            hostAbility: "hello",
            icon: "hello",
            iconId: 1,
            label: "hello",
            labelId: 1,
            wants: [],
            appIndex: 0,
            sourceType: 0,
          }
          try {
            shortcutManager.addDesktopShortcutInfo(data, 100)
              .then(() => {
                console.info("addDesktopShortcutInfo success");
              }).catch((err: BusinessError) => {
              console.error(`addDesktopShortcutInfo errData is errCode:${err.code}  message:${err.message}`);
            });
          } catch (error) {
            let code = (error as BusinessError).code;
            let message = (error as BusinessError).message;
            console.error(`addDesktopShortcutInfo error is errCode:${code}  message:${message}`);
          }
        })
      }
    }
  }
}
```

ArkTS-Sta示例:

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 代码中使用的shortcutInfo、useId需为应用实际设置的快捷方式信息、用户ID。
let data: shortcutManager.ShortcutInfo = {
  id: "test1",
  bundleName: "com.example.myapplication",
  moduleName: "hello",
  hostAbility: "hello",
  icon: "hello",
  iconId: 1,
  label: "hello",
  labelId: 1,
  wants: [],
  appIndex: 0,
  sourceType: 0,
}
try {
  shortcutManager.addDesktopShortcutInfo(data, 100)
    .then(() => {
      console.info("addDesktopShortcutInfo success");
    }).catch((err: Error) => {
      console.error(`addDesktopShortcutInfo errData is errCode:${(err as BusinessError).code}  message:${(err as BusinessError).message}`);
    });
} catch (error) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  console.error(`addDesktopShortcutInfo error is errCode:${code}  message:${message}`);
}
```

