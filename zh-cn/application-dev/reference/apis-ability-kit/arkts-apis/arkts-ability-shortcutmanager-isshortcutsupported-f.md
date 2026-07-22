# isShortcutSupported

## 导入模块

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
```

## isShortcutSupported

```TypeScript
function isShortcutSupported(): boolean
```

查询当前设备是否支持快捷方式。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-shortcutManager-function isShortcutSupported(): boolean--><!--Device-shortcutManager-function isShortcutSupported(): boolean-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示当前设备是否支持快捷方式。<br/>返回值为true表示当前设备支持快捷方式；返回值为false表示当前设备不支持快捷方式。 |

**示例：**

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = shortcutManager.isShortcutSupported();
  console.info('isShortcutSupported data is' + JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  console.error(`isShortcutSupported errData is errCode:${err.code}  message:${err.message}`);
}

```

