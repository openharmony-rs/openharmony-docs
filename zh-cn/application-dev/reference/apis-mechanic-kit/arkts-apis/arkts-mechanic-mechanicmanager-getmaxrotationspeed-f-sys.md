# getMaxRotationSpeed（系统接口）

## getMaxRotationSpeed

```TypeScript
function getMaxRotationSpeed(mechId: int): RotationSpeed
```

Obtains the maximum rotation speed of a mechanical device.

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-mechanicManager-function getMaxRotationSpeed(mechId: int): RotationSpeed--><!--Device-mechanicManager-function getMaxRotationSpeed(mechId: int): RotationSpeed-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mechId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 机械设备ID |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回最大速度，只返回速度的绝对值 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |

**示例：**

```TypeScript
console.info('Query rotation speed');
let speedLimit: mechanicManager.RotationSpeed = mechanicManager.getMaxRotationSpeed(0);
console.info(`'Query rotation speed successful, speed limit information:' ${speedLimit}`);
```

