# isBasSupported（系统接口）

## 导入模块

```TypeScript
import { bas } from '@kit.ConnectivityKit';
```

## isBasSupported

```TypeScript
function isBasSupported(): boolean
```

判断本机设备是否可以获取远端设备的电量。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.Bluetooth.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示本机支持获取远端设备的电量；返回false表示本机不支持获取远端设备的电量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications are not allowed to use system APIs. |
| [2900099](../errorcode-bluetoothManager.md#2900099-操作失败) | Operation failed. |
