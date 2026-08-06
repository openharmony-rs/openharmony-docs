# stopVibrationSync

## stopVibrationSync

```TypeScript
function stopVibrationSync(): void
```

停止任何形式的马达振动。调用成功后马达停止振动。此接口为同步接口，会阻塞主线程直到振动停止操作完成，容易影响UI交互，需谨慎使用。 当开发者需要立即停止所有振动且不关心异步回调结果时使用此接口。适用于对实时性要求极高的场景（如紧急中断振动）。调用成功后，设备上所有正在进行的马达振动立即停止。调用失败时会抛出异常，需使用try catch捕获。与异步版本 [vibrator.stopVibration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_相比，本接口为同步接口，直接返回结果无需回调，但会阻塞主线程。建议在非UI线程中使用，或在UI线程中优先使用异步版本以 避免影响交互响应。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.VIBRATE

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-vibrator-function stopVibrationSync(): void--><!--Device-vibrator-function stopVibrationSync(): void-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [14600101](../errorcode-vibrator.md#14600101-操作设备失败) | Device operation failed. |

**示例：**

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // 停止任何形式的马达振动
  vibrator.stopVibrationSync();
  console.info('Succeed in stopping vibration');
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```

