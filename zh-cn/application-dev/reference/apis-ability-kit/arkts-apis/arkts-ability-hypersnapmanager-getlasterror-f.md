# getLastError

## 导入模块

```TypeScript
import { hyperSnapManager } from '@kit.AbilityKit';
```

## getLastError

```TypeScript
function getLastError(errType: HyperSnapErrorType): Promise<HyperSnapErrorInfo>
```

获取指定场景下当前应用的最后一次Hyper Snap错误信息。每个场景的错误信息独立存储，并在请求成功后清除。设备重启后，所有错误信息都会被清除。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| errType | [HyperSnapErrorType](arkts-ability-hypersnapmanager-hypersnaperrortype-e.md) | 是 | Hyper Snap错误类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[HyperSnapErrorInfo](arkts-ability-hypersnapmanager-hypersnaperrorinfo-i.md)&gt; | Promise用于返回错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Connect to system service failed. |
