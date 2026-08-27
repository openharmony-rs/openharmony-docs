# isSupported

## 导入模块

```TypeScript
import { cardEmulation } from '@kit.ConnectivityKit';
```

## isSupported

```TypeScript
function isSupported(feature: number): boolean
```

是否支持某种类型的卡模拟。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [hasHceCapability](arkts-connectivity-cardemulation-hashcecapability-f.md)

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NFC.CardEmulation

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| feature | number | 是 | 卡模拟类型值，详细请见[FeatureType](arkts-connectivity-cardemulation-featuretype-e.md)枚举值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true: 支持该类型卡模拟， false: 不支持该类型卡模拟。 |

**示例**

```TypeScript
// 适用于除轻量级智能穿戴产品之外其他设备
import { cardEmulation } from '@kit.ConnectivityKit';

let isHceSupported: boolean = cardEmulation.isSupported(cardEmulation.FeatureType.HCE);
if (!isHceSupported) {
    console.info('this device is not supported for HCE, ignore it.');
}
```

```TypeScript
// 适用于轻量级智能穿戴设备
import cardEmulation from '@ohos.nfc.cardEmulation';

let isHceSupported = cardEmulation.isSupported(cardEmulation.FeatureType.HCE);
if (!isHceSupported) {
    console.error('this device is not supported for HCE, ignore it.');
}
```
