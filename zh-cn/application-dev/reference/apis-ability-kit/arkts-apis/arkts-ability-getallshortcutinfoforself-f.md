# getAllShortcutInfoForSelf

## getAllShortcutInfoForSelf

```TypeScript
function getAllShortcutInfoForSelf(): Promise<Array<ShortcutInfo>>
```

查询当前应用[配置文件](../../../../quick-start/module-configuration-file.md#shortcuts标签)中定义的所有快捷方式信息。使用Promise异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ShortcutInfo&gt;&gt; | Promise对象，返回应用配置文件中定义的所有快捷方式信息。 |

**示例：**

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

