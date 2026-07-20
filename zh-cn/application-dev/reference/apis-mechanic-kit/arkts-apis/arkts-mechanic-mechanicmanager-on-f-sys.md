# on（系统接口）

## 导入模块

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

<a id="on"></a>
## on('rotationAxesStatusChange')

```TypeScript
function on(type: 'rotationAxesStatusChange', callback: Callback<RotationAxesStateChangeInfo>): void
```

Register a listener for axis state changes.The status of the rotation axis changes dynamically, which needs to be monitored.

**起始版本：** 20

<!--Device-mechanicManager-function on(type: 'rotationAxesStatusChange', callback: Callback<RotationAxesStateChangeInfo>): void--><!--Device-mechanicManager-function on(type: 'rotationAxesStatusChange', callback: Callback<RotationAxesStateChangeInfo>): void-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'rotationAxesStatusChange' | 是 | Event type. |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;RotationAxesStateChangeInfo&gt; | 是 | Rotate axis state changes callback. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |

**示例：**

```TypeScript
console.info('Register Axis Status listener');
mechanicManager.on("rotationAxesStatusChange", (result: mechanicManager.RotationAxesStateChangeInfo) => {
  console.info(`'result:' ${result}`);
});
console.info('Successful registration');

```

