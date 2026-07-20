# startDeviceManager

## 导入模块

```TypeScript
import { continuationManager } from '@kit.AbilityKit';
```

<a id="startdevicemanager"></a>
## startDeviceManager

```TypeScript
function startDeviceManager(token: number, callback: AsyncCallback<void>): void
```

拉起设备选择模块，可显示组网内可选择设备列表信息，无过滤条件，使用AsyncCallback方式作为异步方法。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [startDiscovering(discoverParam:](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#startdiscovering-1)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-continuationManager-function startDeviceManager(token: number, callback: AsyncCallback<void>): void--><!--Device-continuationManager-function startDeviceManager(token: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| token | number | 是 | 注册后的token。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当模块选择完成，err为undefined，否则返回错误对象。 |

**示例：**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

let token: number = 1;
continuationManager.startDeviceManager(token, (err) => {
  if (err.code != 0) {
    console.error('startDeviceManager failed, cause: ' + JSON.stringify(err));
    return;
  }
  console.info('startDeviceManager finished. ');
});

```


<a id="startdevicemanager-1"></a>
## startDeviceManager

```TypeScript
function startDeviceManager(token: number, options: ContinuationExtraParams, callback: AsyncCallback<void>): void
```

拉起设备选择模块，可显示组网内可选择设备列表信息，使用AsyncCallback方式作为异步方法。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [startDiscovering(discoverParam:](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#startdiscovering-1)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-continuationManager-function startDeviceManager(token: number, options: ContinuationExtraParams, callback: AsyncCallback<void>): void--><!--Device-continuationManager-function startDeviceManager(token: number, options: ContinuationExtraParams, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| token | number | 是 | 注册后的token。 |
| options | [ContinuationExtraParams](arkts-ability-continuationextraparams-continuationextraparams-i.md) | 是 | 过滤可选择设备列表的额外参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当模块选择完成，err为undefined，否则返回错误对象。 |

**示例：**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

let token: number = 1;
continuationManager.startDeviceManager(
  token,
  {
    deviceType: ["00E"]
  },
  (err) => {
    if (err.code != 0) {
      console.error('startDeviceManager failed, cause: ' + JSON.stringify(err));
      return;
    }
    console.info('startDeviceManager finished. ');
});

```


<a id="startdevicemanager-2"></a>
## startDeviceManager

```TypeScript
function startDeviceManager(token: number, options?: ContinuationExtraParams): Promise<void>
```

拉起设备选择模块，可显示组网内可选择设备列表信息，使用Promise方式作为异步方法。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [startDiscovering(discoverParam:](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#startdiscovering-1)

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-continuationManager-function startDeviceManager(token: number, options?: ContinuationExtraParams): Promise<void>--><!--Device-continuationManager-function startDeviceManager(token: number, options?: ContinuationExtraParams): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.DistributedAbilityManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| token | number | 是 | 注册后的token。 |
| options | [ContinuationExtraParams](arkts-ability-continuationextraparams-continuationextraparams-i.md) | 否 | 过滤可选择设备列表的额外参数，该参数可缺省。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise形式返回接口调用结果。 |

**示例：**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let token: number = -1;
continuationManager.startDeviceManager(
  token,
  {
    deviceType: ["00E"]
  }).then(() => {
    console.info('startDeviceManager finished. ');
  }).catch((err: BusinessError) => {
    console.error('startDeviceManager failed, cause: ' + JSON.stringify(err));
});

```

