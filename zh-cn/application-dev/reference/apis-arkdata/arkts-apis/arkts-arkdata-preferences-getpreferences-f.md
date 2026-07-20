# getPreferences

## 导入模块

```TypeScript
import { preferences } from '@kit.ArkData';
```

<a id="getpreferences"></a>
## getPreferences

```TypeScript
function getPreferences(context: Context, name: string, callback: AsyncCallback<Preferences>): void
```

获取Preferences实例，通过name进行参数设置，使用callback异步回调。

应用首次调用该接口获取某个Preferences实例后，该实例会被缓存起来，后续再次调用时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-preferences-function getPreferences(context: Context, name: string, callback: AsyncCallback<Preferences>): void--><!--Device-preferences-function getPreferences(context: Context, name: string, callback: AsyncCallback<Preferences>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文。<br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 |
| name | string | 是 | Preferences实例的名称。名称长度需大于零且小于等于255字节，名称中不能包含'/'且不能以'/'结尾。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Preferences&gt; | 是 | 回调函数。当获取Preferences实例成功，err为undefined，返回Preferences实例；否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error.<br>**适用版本：** 11+ |

**示例：**

FA模型示例：

```TypeScript
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();
let dataPreferences: preferences.Preferences | null = null;

preferences.getPreferences(context, 'myStore', (err: BusinessError, val: preferences.Preferences) => {
  if (err) {
    console.error("Failed to get preferences. Code = " + err.code + ", message = " + err.message);
    return;
  }
  dataPreferences = val;
  console.info("Succeeded in getting preferences.");
})

```

Stage模型示例：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let dataPreferences: preferences.Preferences | null = null;

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    preferences.getPreferences(this.context, 'myStore', (err: BusinessError, val: preferences.Preferences) => {
      if (err) {
        console.error("Failed to get preferences. Code = " + err.code + ", message = " + err.message);
        return;
      }
      dataPreferences = val;
      console.info("Succeeded in getting preferences.");
    })
  }
}

```


<a id="getpreferences-1"></a>
## getPreferences

```TypeScript
function getPreferences(context: Context, options: Options, callback: AsyncCallback<Preferences>): void
```

获取Preferences实例，通过Options进行参数设置，使用callback异步回调。

应用首次调用该接口获取某个Preferences实例后，该实例会被缓存起来，后续再次调用时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-preferences-function getPreferences(context: Context, options: Options, callback: AsyncCallback<Preferences>): void--><!--Device-preferences-function getPreferences(context: Context, options: Options, callback: AsyncCallback<Preferences>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文。<br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 |
| options | [Options](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-zlib-options-i.md) | 是 | 与Preferences实例相关的配置选项。name字段为必填字段，名称长度需大于零且小于等于255字节，名称中不能包含'/'且不能以'/'结尾。dataGroupId和storageType为可选字段。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Preferences&gt; | 是 | 回调函数。当获取Preferences实例成功，err为undefined，返回Preferences实例；否则err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
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
let dataPreferences: preferences.Preferences | null = null;

let options: preferences.Options = { name: 'myStore' };
preferences.getPreferences(context, options, (err: BusinessError, val: preferences.Preferences) => {
  if (err) {
    console.error("Failed to get preferences. Code = " + err.code + ", message = " + err.message);
    return;
  }
  dataPreferences = val;
  console.info("Succeeded in getting preferences.");
})

```

Stage模型示例：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let dataPreferences: preferences.Preferences | null = null;

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: preferences.Options = { name: 'myStore' };
    preferences.getPreferences(this.context, options, (err: BusinessError, val: preferences.Preferences) => {
      if (err) {
        console.error("Failed to get preferences. Code = " + err.code + ", message = " + err.message);
        return;
      }
      dataPreferences = val;
      console.info("Succeeded in getting preferences.");
    })
  }
}

```


<a id="getpreferences-2"></a>
## getPreferences

```TypeScript
function getPreferences(context: Context, name: string): Promise<Preferences>
```

获取Preferences实例，通过name进行参数设置，使用Promise异步回调。

应用首次调用该接口获取某个Preferences实例后，该实例会被缓存起来，后续再次调用时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-preferences-function getPreferences(context: Context, name: string): Promise<Preferences>--><!--Device-preferences-function getPreferences(context: Context, name: string): Promise<Preferences>-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文。<br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 |
| name | string | 是 | Preferences实例的名称。名称长度需大于零且小于等于255字节，名称中不能包含'/'且不能以'/'结尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Preferences&gt; | Promise对象，返回Preferences实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [15500000](../errorcode-preferences.md#15500000-内部错误) | Inner error.<br>**适用版本：** 11+ |

**示例：**

FA模型示例：

```TypeScript
// 获取context
import { featureAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context = featureAbility.getContext();

let dataPreferences: preferences.Preferences | null = null;
let sp = preferences.getPreferences(context, 'myStore');
sp.then((object: preferences.Preferences) => {
  dataPreferences = object;
  console.info("Succeeded in getting preferences.");
}).catch((err: BusinessError) => {
  console.error("Failed to get preferences. Code = " + err.code + ", message = " + err.message);
})

```

Stage模型示例：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let dataPreferences: preferences.Preferences | null = null;

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let sp = preferences.getPreferences(this.context, 'myStore');
    sp.then((object: preferences.Preferences) => {
      dataPreferences = object;
      console.info("Succeeded in getting preferences.");
    }).catch((err: BusinessError) => {
      console.error("Failed to get preferences. Code = " + err.code + ", message = " + err.message);
    })
  }
}

```


<a id="getpreferences-3"></a>
## getPreferences

```TypeScript
function getPreferences(context: Context, options: Options): Promise<Preferences>
```

获取Preferences实例，通过Options进行参数设置，使用Promise异步回调。

应用首次调用该接口获取某个Preferences实例后，该实例会被缓存起来，后续再次调用时不会再次从持久化文件中读取，直接从缓存中获取Preferences实例。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-preferences-function getPreferences(context: Context, options: Options): Promise<Preferences>--><!--Device-preferences-function getPreferences(context: Context, options: Options): Promise<Preferences>-End-->

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文。<br>FA模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-context-depr-i.md)。<br>Stage模型的应用Context定义见[Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md)。 |
| options | [Options](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-zlib-options-i.md) | 是 | 与Preferences实例相关的配置选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Preferences&gt; | Promise对象，返回Preferences实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br>1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types;<br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
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

let dataPreferences: preferences.Preferences | null = null;
let options: preferences.Options = { name: 'myStore' };
let sp = preferences.getPreferences(context, options);
sp.then((object: preferences.Preferences) => {
  dataPreferences = object;
  console.info("Succeeded in getting preferences.");
}).catch((err: BusinessError) => {
  console.error("Failed to get preferences. Code = " + err.code + ", message = " + err.message);
})

```

Stage模型示例：

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let dataPreferences: preferences.Preferences | null = null;

class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    let options: preferences.Options = { name: 'myStore' };
    let sp = preferences.getPreferences(this.context, options);
    sp.then((object: preferences.Preferences) => {
      dataPreferences = object;
      console.info("Succeeded in getting preferences.");
    }).catch((err: BusinessError) => {
      console.error("Failed to get preferences. Code = " + err.code + ", message = " + err.message);
    })
  }
}

```

