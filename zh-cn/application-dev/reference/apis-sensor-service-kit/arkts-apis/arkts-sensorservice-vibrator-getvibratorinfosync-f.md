# getVibratorInfoSync

## getVibratorInfoSync

```TypeScript
function getVibratorInfoSync(param?: VibratorInfoParam): Array<VibratorInfo>
```

查询一个或所有设备的马达信息列表。适用于在触发振动前查询设备马达能力和多马达设备的马达ID，以便选择合适的马达触发振动。 不传param时查询所有设备马达信息；传入VibratorInfoParam可查询指定设备或马达。返回VibratorInfo数组，包含deviceId、vibratorId、deviceName、 isHdHapticSupported、isLocalVibrator等属性，可用于startVibration (#vibratorstartvibration9)和stopVibration (# vibratorstopvibration19)中指定马达和设备。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-vibrator-function getVibratorInfoSync(param?: VibratorInfoParam): Array<VibratorInfo>--><!--Device-vibrator-function getVibratorInfoSync(param?: VibratorInfoParam): Array<VibratorInfo>-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [VibratorInfoParam](arkts-sensorservice-vibrator-vibratorinfoparam-i.md) | 否 | 指出需要查询的设备和马达信息。不传param时默认查询所有设备所有马达的信息。deviceId默认值为-1（查询全部设备），vibratorId默认值为0（查询该 设备的全部马达）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[VibratorInfo](arkts-sensorservice-vibrator-vibratorinfo-i.md)&gt; | 马达设备的信息数组。每个元素包含deviceId、vibratorId、deviceName、isHdHapticSupported、isLocalVibrator等属性，可 用于选择合适的马达触发振动或判断设备振动能力。 |

## 示例

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const vibratorInfoList: vibrator.VibratorInfo[] = vibrator.getVibratorInfoSync({ deviceId: 1, vibratorId: 3 });
  console.info(`vibratorInfoList: ${JSON.stringify(vibratorInfoList)}`);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`An unexpected error occurred. Code: ${e.code}, message: ${e.message}`);
}
```

