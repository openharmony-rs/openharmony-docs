# deletePreferences

## 导入模块

```TypeScript
import { preferences } from '@kit.ArkData';
```

<a id="deletepreferences"></a>
## deletePreferences

```TypeScript
function deletePreferences(context: Context, name: string, callback: AsyncCallback<void>): void
```

从缓存中删除指定的Preferences实例，若Preferences实例有对应的持久化文件，则同时删除其持久化文件。通过name进行参数设置，使用callback异步回调。

调用该接口后，不建议再使用旧的Preferences实例进行数据操作，否则会导致数据一致性问题，应将Preferences实例置为null，系统会统一回收。

不支持该接口与其他preference接口并发调用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-preferences-function deletePreferences(context: Context, name: string, callback: AsyncCallback<void>): void--><!--Device-preferences-function deletePreferences(context: Context, name: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文。<br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 |
| name | string | 是 | Preferences实例的名称。名称长度需大于零且小于等于255字节，名称中不能包含'/'且不能以'/'结尾。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当移除成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500010](../errorcode-preferences.md#15500010-删除用户首选项持久化文件失败) | Failed to delete the user preferences persistence file. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error.<br>**适用版本：** 11+ |

**示例：**

FA模型示例：

```TypeScript
// 获取context
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();

preferences.deletePreferences(context, 'myStore', (err: BusinessError) => {
  if (err) {
    console.error("Failed to delete preferences. Code = " + err.code + ", message = " + err.message);
    return;
  }
  console.info("Succeeded in deleting preferences.");
})

```

Stage模型示例：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    preferences.deletePreferences(this.context, 'myStore', (err: BusinessError) => {
      if (err) {
        console.error("Failed to delete preferences. Code = " + err.code + ", message = " + err.message);
        return;
      }
      console.info("Succeeded in deleting preferences.");
    })
  }
}

```


<a id="deletepreferences-1"></a>
## deletePreferences

```TypeScript
function deletePreferences(context: Context, options: Options, callback: AsyncCallback<void>): void
```

从缓存中删除指定的Preferences实例，若Preferences实例有对应的持久化文件，则同时删除其持久化文件。通过Options进行参数设置，使用callback异步回调。

调用该接口后，不建议再使用旧的Preferences实例进行数据操作，否则会导致数据一致性问题，应将Preferences实例置为null，系统会统一回收。

不支持该接口与其他preference接口并发调用。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-preferences-function deletePreferences(context: Context, options: Options, callback: AsyncCallback<void>): void--><!--Device-preferences-function deletePreferences(context: Context, options: Options, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文。<br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 |
| options | [Options](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-zlib-options-i.md) | 是 | 与Preferences实例相关的配置选项。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当移除成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [15500010](../errorcode-preferences.md#15500010-删除用户首选项持久化文件失败) | Failed to delete the user preferences persistence file. |
| [15501001](../errorcode-preferences.md#15501001-上下文环境非stage模型) | The operations is supported in stage mode only. |
| [15501002](../errorcode-preferences.md#15501002-options中传入的datagroupid参数非法) | Invalid dataGroupId. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error.<br>**适用版本：** 11+ |

**示例：**

FA模型示例：

```TypeScript
// 获取context
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();

let options: preferences.Options = { name: 'myStore' };
preferences.deletePreferences(context, options, (err: BusinessError) => {
  if (err) {
    console.error("Failed to delete preferences. code =" + err.code + ", message = " + err.message);
    return;
  }
  console.info("Succeeded in deleting preferences.");
})

```

Stage模型示例：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: preferences.Options = { name: 'myStore' };
    preferences.deletePreferences(this.context, options, (err: BusinessError) => {
      if (err) {
        console.error("Failed to delete preferences. code =" + err.code + ", message = " + err.message);
        return;
      }
      console.info("Succeeded in deleting preferences.");
    })
  }
}

```


<a id="deletepreferences-2"></a>
## deletePreferences

```TypeScript
function deletePreferences(context: Context, name: string): Promise<void>
```

从缓存中删除指定的Preferences实例，若Preferences实例有对应的持久化文件，则同时删除其持久化文件。通过name进行参数设置，使用Promise异步回调。

调用该接口后，不建议再使用旧的Preferences实例进行数据操作，否则会导致数据一致性问题，应将Preferences实例置为null，系统会统一回收。

不支持该接口与其他preference接口并发调用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-preferences-function deletePreferences(context: Context, name: string): Promise<void>--><!--Device-preferences-function deletePreferences(context: Context, name: string): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文。<br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 |
| name | string | 是 | Preferences实例的名称。名称长度需大于零且小于等于255字节，名称中不能包含'/'且不能以'/'结尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500010](../errorcode-preferences.md#15500010-删除用户首选项持久化文件失败) | Failed to delete the user preferences persistence file. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error.<br>**适用版本：** 11+ |

**示例：**

FA模型示例：

```TypeScript
// 获取context
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();

let sp = preferences.deletePreferences(context, 'myStore');
sp.then(() => {
  console.info("Succeeded in deleting preferences.");
}).catch((err: BusinessError) => {
  console.error("Failed to delete preferences. Code = " + err.code + ", message = " + err.message);
})

```

Stage模型示例：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let sp = preferences.deletePreferences(this.context, 'myStore');
    sp.then(() => {
      console.info("Succeeded in deleting preferences.");
    }).catch((err: BusinessError) => {
      console.error("Failed to delete preferences. code =" + err.code + ", message = " + err.message);
    })
  }
}

```


<a id="deletepreferences-3"></a>
## deletePreferences

```TypeScript
function deletePreferences(context: Context, options: Options): Promise<void>
```

从缓存中删除指定的Preferences实例，若Preferences实例有对应的持久化文件，则同时删除其持久化文件。通过Options进行参数设置，使用Promise异步回调。

调用该接口后，不建议再使用旧的Preferences实例进行数据操作，否则会导致数据一致性问题，应将Preferences实例置为null，系统会统一回收。

不支持该接口与其他preference接口并发调用。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-preferences-function deletePreferences(context: Context, options: Options): Promise<void>--><!--Device-preferences-function deletePreferences(context: Context, options: Options): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文。<br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 |
| options | [Options](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-zlib-options-i.md) | 是 | 与Preferences实例相关的配置选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [15500010](../errorcode-preferences.md#15500010-删除用户首选项持久化文件失败) | Failed to delete the user preferences persistence file. |
| [15501001](../errorcode-preferences.md#15501001-上下文环境非stage模型) | The operations is supported in stage mode only. |
| [15501002](../errorcode-preferences.md#15501002-options中传入的datagroupid参数非法) | Invalid dataGroupId. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error.<br>**适用版本：** 11+ |

**示例：**

FA模型示例：

```TypeScript
// 获取context
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();

let options: preferences.Options = { name: 'myStore' };
let sp = preferences.deletePreferences(context, options);
sp.then(() => {
  console.info("Succeeded in deleting preferences.");
}).catch((err: BusinessError) => {
  console.error("Failed to delete preferences. code =" + err.code + ", message = " + err.message);
})

```

Stage模型示例：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: preferences.Options = { name: 'myStore' };
    let sp = preferences.deletePreferences(this.context, options);
    sp.then(() => {
      console.info("Succeeded in deleting preferences.");
    }).catch((err: BusinessError) => {
      console.error("Failed to delete preferences. code =" + err.code + ", message = " + err.message);
    })
  }
}

```

