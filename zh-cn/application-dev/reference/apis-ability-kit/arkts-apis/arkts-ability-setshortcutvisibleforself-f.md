# setShortcutVisibleForSelf

## setShortcutVisibleForSelf

```TypeScript
function setShortcutVisibleForSelf(id: string, visible: boolean): Promise<void>
```

设置当前应用指定的快捷方式是否显示。使用Promise异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 快捷方式的ID，通过[module.json5配置文件](../../../../quick-start/module-configuration-file.md)中的shortcuts标签下的shortcutId字段获取，取值为长度不超过63字节的字符串。 |
| visible | boolean | 是 | 快捷方式是否显示。true：快捷方式显示；false：快捷方式不显示。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17700070](../errorcode-bundle.md#17700070-指定的快捷方式id不合法) | The specified shortcut id is not exist. |

**示例：**

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 请替换为module.json5配置文件中的shortcuts标签下实际配置的shortcutId字段
shortcutManager.setShortcutVisibleForSelf("shortcut_id", false)
  .then(() => {
    console.info('setShortcutVisibleForSelf success');
  }).catch((err: BusinessError) => {
  console.error(`setShortcutVisibleForSelf errData is errCode:${err.code}  message:${err.message}`);
});

```

