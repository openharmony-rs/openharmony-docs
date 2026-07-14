# getPreferences

## getPreferences

```TypeScript
function getPreferences(context: Context, options: Options): Promise<Preferences>
```

获取Preferences实例，使用Promise异步回调。

应用首次调用该接口获取某个Preferences实例后，该实例会被缓存起来，后续再次调用时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用上下文。 |
| options | Options | 是 | 与Preferences实例相关的配置选项。name字段为必填字段，名称长度需大于零且小于等于255字节，名称中不能包含'/'且不能以'/'结尾。dataGroupId为可选字段。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Preferences&gt; | Promise对象，返回Preferences实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error. |
| [15501001](../errorcode-preferences.md#15501001-上下文环境非stage模型) | The operations is supported in stage mode only. |
| [15501002](../errorcode-preferences.md#15501002-options中传入的datagroupid参数非法) | Invalid dataGroupId. |

**示例：**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let preferences: sendablePreferences.Preferences;

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: sendablePreferences.Options = { name: 'myStore' };
    let promise = sendablePreferences.getPreferences(this.context, options);
    promise.then((object: sendablePreferences.Preferences) => {
      preferences = object;
      console.info("Succeeded in getting preferences.");
    }).catch((err: BusinessError) => {
      console.error(`Failed to get preferences. code: ${err.code}, message: ${err.message}`);
    });
  }
}

```

