# off（系统接口）

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## off('rotationAxesStatusChange')

```TypeScript
function off(type: 'rotationAxesStatusChange', callback?: Callback<RotationAxesStateChangeInfo>): void
```

Unregister a listener for axis state changes.

**起始版本：** 20

<!--Device-mechanicManager-function off(type: 'rotationAxesStatusChange', callback?: Callback<RotationAxesStateChangeInfo>): void--><!--Device-mechanicManager-function off(type: 'rotationAxesStatusChange', callback?: Callback<RotationAxesStateChangeInfo>): void-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'rotationAxesStatusChange' | 是 | Event type. |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<RotationAxesStateChangeInfo> | 否 | Rotate axis state changes callback. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |

**示例：**

```TypeScript
console.info('Unregister Axis Status listener');
mechanicManager.off("rotationAxesStatusChange", (result: mechanicManager.RotationAxesStateChangeInfo) => {
  console.info(`'result:' ${result}`);
});
console.info('Unregister successfully');

```

