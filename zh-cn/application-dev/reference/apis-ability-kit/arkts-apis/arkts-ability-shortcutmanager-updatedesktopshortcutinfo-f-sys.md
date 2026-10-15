# updateDesktopShortcutInfo（系统接口）

## 导入模块

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
```

## updateDesktopShortcutInfo

```TypeScript
function updateDesktopShortcutInfo(shortcutInfo: ShortcutInfo, userId: number): Promise<void>
```

更新指定用户的快捷方式信息。使用Promise异步回调。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.MANAGE_SHORTCUTS or (ohos.permission.MANAGE_SHORTCUTS and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-shortcutManager-function updateDesktopShortcutInfo(shortcutInfo: ShortcutInfo, userId: int): Promise<void>--><!--Device-shortcutManager-function updateDesktopShortcutInfo(shortcutInfo: ShortcutInfo, userId: int): Promise<void>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shortcutInfo | [ShortcutInfo](arkts-ability-shortcutmanager-shortcutinfo-t.md) | 是 | 快捷方式信息。 |
| userId | number | 是 | 用户ID。可以通过[getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)接口获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name is not found. |
| [17700004](../errorcode-bundle.md#17700004-指定的用户不存在) | The specified user ID is not found. |
| [17700026](../errorcode-bundle.md#17700026-指定应用被禁用) | The specified bundle is disabled. |
| [17700061](../errorcode-bundle.md#17700061-指定的应用分身索引无效) | The specified app index is invalid. |
| 18100002 | The specified shortcut to be updated is not found. |

<!--Del-->
**示例**

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// 请开发者替换为实际的快捷方式信息、用户ID。
let shortcutInfo: shortcutManager.ShortcutInfo = {
  id: 'test1',
  bundleName: 'com.example.myapplication',
  moduleName: '',
  hostAbility: '',
  icon: '',
  iconId: 1,
  label: 'hello',
  labelId: 1,
  wants: [],
  appIndex: 0,
  sourceType: 0,
};

try {
  shortcutManager.updateDesktopShortcutInfo(shortcutInfo, 100)
    .then(() => {
      hilog.info(0x0000, 'testTag', 'updateDesktopShortcutInfo successfully');
    }).catch((err: Error) => {
      hilog.error(0x0000, 'testTag', 'updateDesktopShortcutInfo failed. Cause: %{public}s', err.message);
    });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'updateDesktopShortcutInfo failed. Cause: %{public}s', message);
}
```

<!--DelEnd-->
