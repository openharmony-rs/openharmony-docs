# getAttachedMechDevices

## getAttachedMechDevices

```TypeScript
function getAttachedMechDevices(): MechInfo[]
```

获取已连接的机械设备列表

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-mechanicManager-function getAttachedMechDevices(): MechInfo[]--><!--Device-mechanicManager-function getAttachedMechDevices(): MechInfo[]-End-->

**系统能力：** SystemCapability.Mechanic.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_[] | 返回已连接的机械设备列表 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |

**示例：**

```TypeScript
console.info('Query device list');
// 调用getAttachedMechDevices方法获取已连接的机械体设备列表
let mechanicInfos = mechanicManager.getAttachedMechDevices();
console.info(`'device list:' ${mechanicInfos}`);
```

