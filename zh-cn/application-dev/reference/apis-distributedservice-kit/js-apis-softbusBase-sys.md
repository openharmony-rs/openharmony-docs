# @ohos.distributed.softbusBase (设备感知)(系统接口)
<!--Kit: Distributed Service Kit-->
<!--Subsystem: Communication-->
<!--Owner: @Lucky-M-->
<!--Designer: @Lucky-M-->
<!--Tester: @openharmony_ci-->
<!--Adviser: @hu-zhiqiong-->

本模块提供设备感知能力，包括感知广播的启停、高频切换、感知扫描的启停以及已发现设备列表查询等。系统应用可通过自定义负载广播唤醒周边协同设备，并通过扫描发现周边感知设备，适用于近场设备间低功耗、高效的协同唤醒与发现场景。

**起始版本：** 26.0.0

> **说明：**
>
> 本模块接口为系统接口，仅可在Stage模型下使用。

## 导入模块

```TypeScript
import softbusBase from '@ohos.distributed.softbusBase';
```

## PerceptionType

感知服务类型枚举。

**起始版本：** 26.0.0

**系统能力**：SystemCapability.Communication.SoftBus.Core

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| PERCEPTION_TYPE_COLLABORATIVE_WAKE | 0 | 协同唤醒。该类型的感知广播或扫描用于跨设备协同唤醒。 |

## PerceptionCycle

感知扫描保活周期档位枚举。档位越高，保活周期越短。

**起始版本：** 26.0.0

**系统能力**：SystemCapability.Communication.SoftBus.Core

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| PERCEPTION_CYCLE_LOW | 0 | 低周期。 |
| PERCEPTION_CYCLE_MEDIUM | 1 | 中周期。 |
| PERCEPTION_CYCLE_HIGH | 2 | 高周期。 |

## PerceptionDeviceInfo

感知扫描发现的设备信息，包括设备类型、设备ID以及广播携带的自定义数据。

**起始版本：** 26.0.0

**系统能力**：SystemCapability.Communication.SoftBus.Core

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | ---- | ---- | -------- |
| deviceType | int | 否 | 否 | 设备类型，具体值以系统定义为准。 |
| deviceId | ArrayBuffer | 否 | 否 | 设备ID，为二进制数据，网络字节序（大端），最大长度6字节。 |
| customData | ArrayBuffer | 否 | 否 | 广播携带的自定义数据，长度与被发现设备广播携带的自定义数据长度一致，最大长度5字节。 |

## softbusBase.startPerceptionAdv

startPerceptionAdv(type:&nbsp;[PerceptionType](#perceptiontype), customData?:&nbsp;ArrayBuffer):&nbsp;Promise&lt;void&gt;

启动感知广播或更新当前所有者的自定义负载。广播启动后，周边扫描设备可发现本设备。使用Promise异步回调。

**起始版本：** 26.0.0

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_SOFTBUS_SYS_HAP 和 ohos.permission.DISTRIBUTED_DATASYNC

**系统能力**：SystemCapability.Communication.SoftBus.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| type | [PerceptionType](#perceptiontype) | 是 | 感知服务类型。 |
| customData | ArrayBuffer | 否 | 广播携带的自定义负载，数据结构由应用层协议定义。最大长度5字节，超出将抛出错误。不填时默认为空ArrayBuffer。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[设备感知错误码](errorcode-softbusBase.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied, need to acquire ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC. |
| 202 | Permission denied, a non-system application calls a system API. |
| 801 | Capability not supported. |
| 2000001 | Internal error. |
| 2000003 | Temporary error. |
| 2006001 | Underlying module error. |

**示例：**

```TypeScript
import softbusBase from '@ohos.distributed.softbusBase';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 自定义负载（≤5字节）
  let customData: ArrayBuffer = new ArrayBuffer(2);
  let view = new Uint8Array(customData);
  view[0] = 0x01;
  view[1] = 0x02;
  softbusBase.startPerceptionAdv(softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE, customData)
    .then(() => {
      console.info('startPerceptionAdv success');
    })
    .catch((err: BusinessError) => {
      console.error(`startPerceptionAdv errCode: ${err.code}, errMessage: ${err.message}`);
    });
} catch (err) {
  const e: BusinessError = err as BusinessError;
  console.error(`startPerceptionAdv errCode: ${e.code}, errMessage: ${e.message}`);
}
```

## softbusBase.setPerceptionAdvHighFreq

setPerceptionAdvHighFreq(type:&nbsp;[PerceptionType](#perceptiontype), customData?:&nbsp;ArrayBuffer):&nbsp;Promise&lt;void&gt;

将活跃感知广播切换为高频，持续10秒，到期后自动恢复原频段。切换时可同时更新自定义负载。使用Promise异步回调。

**起始版本：** 26.0.0

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_SOFTBUS_SYS_HAP 和 ohos.permission.DISTRIBUTED_DATASYNC

**系统能力**：SystemCapability.Communication.SoftBus.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| type | [PerceptionType](#perceptiontype) | 是 | 感知服务类型。 |
| customData | ArrayBuffer | 否 | 广播携带的自定义负载，数据结构由应用层协议定义。最大长度5字节，超出将抛出错误。不填时默认为空ArrayBuffer。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[设备感知错误码](errorcode-softbusBase.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied, need to acquire ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC. |
| 202 | Permission denied, a non-system application calls a system API. |
| 801 | Capability not supported. |
| 2000001 | Internal error. |
| 2000003 | Temporary error. |
| 2006001 | Underlying module error. |

**示例：**

```TypeScript
import softbusBase from '@ohos.distributed.softbusBase';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let customData: ArrayBuffer = new ArrayBuffer(1);
  new Uint8Array(customData)[0] = 0x03;
  softbusBase.setPerceptionAdvHighFreq(softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE, customData)
    .then(() => {
      console.info('setPerceptionAdvHighFreq success');
    })
    .catch((err: BusinessError) => {
      console.error(`setPerceptionAdvHighFreq errCode: ${err.code}, errMessage: ${err.message}`);
    });
} catch (err) {
  const e: BusinessError = err as BusinessError;
  console.error(`setPerceptionAdvHighFreq errCode: ${e.code}, errMessage: ${e.message}`);
}
```

## softbusBase.stopPerceptionAdv

stopPerceptionAdv(type:&nbsp;[PerceptionType](#perceptiontype)):&nbsp;Promise&lt;void&gt;

停止当前所有者的感知广播。广播停止后，周边扫描设备不再发现本设备。使用Promise异步回调。

**起始版本：** 26.0.0

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_SOFTBUS_SYS_HAP 和 ohos.permission.DISTRIBUTED_DATASYNC

**系统能力**：SystemCapability.Communication.SoftBus.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| type | [PerceptionType](#perceptiontype) | 是 | 感知服务类型。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[设备感知错误码](errorcode-softbusBase.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied, need to acquire ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC. |
| 202 | Permission denied, a non-system application calls a system API. |
| 801 | Capability not supported. |
| 2000001 | Internal error. |
| 2000003 | Temporary error. |
| 2006001 | Underlying module error. |

**示例：**

```TypeScript
import softbusBase from '@ohos.distributed.softbusBase';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  softbusBase.stopPerceptionAdv(softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE)
    .then(() => {
      console.info('stopPerceptionAdv success');
    })
    .catch((err: BusinessError) => {
      console.error(`stopPerceptionAdv errCode: ${err.code}, errMessage: ${err.message}`);
    });
} catch (err) {
  const e: BusinessError = err as BusinessError;
  console.error(`stopPerceptionAdv errCode: ${e.code}, errMessage: ${e.message}`);
}
```

## softbusBase.startPerceptionScan

startPerceptionScan(type:&nbsp;[PerceptionType](#perceptiontype), cycle:&nbsp;[PerceptionCycle](#perceptioncycle)):&nbsp;Promise&lt;void&gt;

以指定保活周期启动当前所有者的感知扫描。扫描启动后，可发现周边广播设备，通过 [getPerceptionDeviceList](#softbusbasegetperceptiondevicelist) 获取已发现设备。使用Promise异步回调。

**起始版本：** 26.0.0

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_SOFTBUS_SYS_HAP 和 ohos.permission.DISTRIBUTED_DATASYNC

**系统能力**：SystemCapability.Communication.SoftBus.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| type | [PerceptionType](#perceptiontype) | 是 | 感知服务类型。 |
| cycle | [PerceptionCycle](#perceptioncycle) | 是 | 保活周期档位，档位越高保活周期越短。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[设备感知错误码](errorcode-softbusBase.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied, need to acquire ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC. |
| 202 | Permission denied, a non-system application calls a system API. |
| 801 | Capability not supported. |
| 2000001 | Internal error. |
| 2000003 | Temporary error. |
| 2006001 | Underlying module error. |

**示例：**

```TypeScript
import softbusBase from '@ohos.distributed.softbusBase';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  softbusBase.startPerceptionScan(
    softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE,
    softbusBase.PerceptionCycle.PERCEPTION_CYCLE_MEDIUM)
    .then(() => {
      console.info('startPerceptionScan success');
    })
    .catch((err: BusinessError) => {
      console.error(`startPerceptionScan errCode: ${err.code}, errMessage: ${err.message}`);
    });
} catch (err) {
  const e: BusinessError = err as BusinessError;
  console.error(`startPerceptionScan errCode: ${e.code}, errMessage: ${e.message}`);
}
```

## softbusBase.stopPerceptionScan

stopPerceptionScan(type:&nbsp;[PerceptionType](#perceptiontype)):&nbsp;Promise&lt;void&gt;

停止感知扫描并清空当前所有者的已发现设备列表。扫描停止后，已发现设备列表被清空，不可再通过 [getPerceptionDeviceList](#softbusbasegetperceptiondevicelist) 获取。使用Promise异步回调。

**起始版本：** 26.0.0

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_SOFTBUS_SYS_HAP 和 ohos.permission.DISTRIBUTED_DATASYNC

**系统能力**：SystemCapability.Communication.SoftBus.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| type | [PerceptionType](#perceptiontype) | 是 | 感知服务类型。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[设备感知错误码](errorcode-softbusBase.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied, need to acquire ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC. |
| 202 | Permission denied, a non-system application calls a system API. |
| 801 | Capability not supported. |
| 2000001 | Internal error. |
| 2000003 | Temporary error. |
| 2006001 | Underlying module error. |

**示例：**

```TypeScript
import softbusBase from '@ohos.distributed.softbusBase';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  softbusBase.stopPerceptionScan(softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE)
    .then(() => {
      console.info('stopPerceptionScan success');
    })
    .catch((err: BusinessError) => {
      console.error(`stopPerceptionScan errCode: ${err.code}, errMessage: ${err.message}`);
    });
} catch (err) {
  const e: BusinessError = err as BusinessError;
  console.error(`stopPerceptionScan errCode: ${e.code}, errMessage: ${e.message}`);
}
```

## softbusBase.getPerceptionDeviceList

getPerceptionDeviceList(type:&nbsp;[PerceptionType](#perceptiontype)):&nbsp;Promise&lt;[PerceptionDeviceInfo](#perceptiondeviceinfo)[]&gt;

获取感知扫描发现的设备列表。需先调用 [startPerceptionScan](#softbusbasestartperceptionscan) 启动扫描；调用 [stopPerceptionScan](#softbusbasestopperceptionscan) 停止扫描后，已发现设备列表被清空。使用Promise异步回调。

**起始版本：** 26.0.0

**系统接口**：此接口为系统接口。

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_SOFTBUS_SYS_HAP 和 ohos.permission.DISTRIBUTED_DATASYNC

**系统能力**：SystemCapability.Communication.SoftBus.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | ---- | -------- |
| type | [PerceptionType](#perceptiontype) | 是 | 感知服务类型。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[PerceptionDeviceInfo](#perceptiondeviceinfo)[]&gt; | Promise对象，返回感知扫描发现的设备列表。未发现设备或未启动扫描时返回空数组。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[设备感知错误码](errorcode-softbusBase.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied, need to acquire ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC. |
| 202 | Permission denied, a non-system application calls a system API. |
| 801 | Capability not supported. |
| 2000001 | Internal error. |
| 2000002 | Caller error. |
| 2000003 | Temporary error. |
| 2006001 | Underlying module error. |

**示例：**

```TypeScript
import softbusBase from '@ohos.distributed.softbusBase';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  softbusBase.getPerceptionDeviceList(softbusBase.PerceptionType.PERCEPTION_TYPE_COLLABORATIVE_WAKE)
    .then((devices: Array<softbusBase.PerceptionDeviceInfo>) => {
      console.info(`getPerceptionDeviceList success, count: ${devices.length}`);
      devices.forEach((d, idx) => {
        let idView = new Uint8Array(d.deviceId);
        let dataView = new Uint8Array(d.customData);
        console.info(`device[${idx}]: type=${d.deviceType}, idLen=${idView.length}, customDataLen=${dataView.length}`);
      });
    })
    .catch((err: BusinessError) => {
      console.error(`getPerceptionDeviceList errCode: ${err.code}, errMessage: ${err.message}`);
    });
} catch (err) {
  const e: BusinessError = err as BusinessError;
  console.error(`getPerceptionDeviceList errCode: ${e.code}, errMessage: ${e.message}`);
}
```
