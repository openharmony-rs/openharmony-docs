# getAllShortcutInfoForSelf

## getAllShortcutInfoForSelf

```TypeScript
function getAllShortcutInfoForSelf(): Promise<Array<ShortcutInfo>>
```

查询当前应用\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中定义的所有快捷方式信息。使用Promise异步回调。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-shortcutManager-function getAllShortcutInfoForSelf(): Promise<Array<ShortcutInfo>>--><!--Device-shortcutManager-function getAllShortcutInfoForSelf(): Promise<Array<ShortcutInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ShortcutInfo&gt;&gt; | Promise对象，返回应用配置文件中定义的所有快捷方式信息。 |

**示例：**

ArkTS-Dyn示例:

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

shortcutManager.getAllShortcutInfoForSelf()
  .then((data: shortcutManager.ShortcutInfo[]) => {
    console.info('getAllShortcutInfoForSelf shortcut data is' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`getAllShortcutInfoForSelf errData is errCode:${err.code}  message:${err.message}`);
});
```

ArkTS-Sta示例:

```TypeScript
'use static'

import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

shortcutManager.getAllShortcutInfoForSelf()
  .then((data: shortcutManager.ShortcutInfo[]) => {
    console.info('getAllShortcutInfoForSelf shortcut data is' + JSON.stringify(data));
  }).catch((err: Error) => {
    console.error(`getAllShortcutInfoForSelf errData is errCode:${(err as BusinessError).code}  message:${(err as BusinessError).message}`);
  });
```

