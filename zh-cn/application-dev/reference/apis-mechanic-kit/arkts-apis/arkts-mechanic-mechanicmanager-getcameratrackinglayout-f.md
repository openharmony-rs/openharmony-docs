# getCameraTrackingLayout

## getCameraTrackingLayout

```TypeScript
function getCameraTrackingLayout(): CameraTrackingLayout
```

获取当前摄像头跟踪布局

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-mechanicManager-function getCameraTrackingLayout(): CameraTrackingLayout--><!--Device-mechanicManager-function getCameraTrackingLayout(): CameraTrackingLayout-End-->

**系统能力：** SystemCapability.Mechanic.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回当前布局 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |

**示例：**

```TypeScript
console.info('Query layout');
// 调用getCameraTrackingLayout方法获取当前摄像头跟踪布局
let layout = mechanicManager.getCameraTrackingLayout();
console.info(`'Succeeded in querying layout, current layout:' ${layout}`);
```

