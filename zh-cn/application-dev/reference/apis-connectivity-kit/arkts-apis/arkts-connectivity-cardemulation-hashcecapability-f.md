# hasHceCapability

## 导入模块

```TypeScript
import { cardEmulation } from '@kit.ConnectivityKit';
```

## hasHceCapability

```TypeScript
function hasHceCapability(): boolean
```

判断设备是否支持HCE卡模拟功能。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_CARD_EMULATION

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.CardEmulation

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true: 支持HCE， false: 不支持HCE。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
// 适用于除轻量级智能穿戴产品之外其他设备
import { cardEmulation } from '@kit.ConnectivityKit';

let hasHceCap: boolean = cardEmulation.hasHceCapability();
if (!hasHceCap) {
    console.error('this device hasHceCapability false, ignore it.');
}
```

```TypeScript
// 适用于轻量级智能穿戴设备
import cardEmulation from '@ohos.nfc.cardEmulation';

let hasHceCap = cardEmulation.hasHceCapability();
if (!hasHceCap) {
    console.error('this device hasHceCapability false, ignore it.');
}
```
