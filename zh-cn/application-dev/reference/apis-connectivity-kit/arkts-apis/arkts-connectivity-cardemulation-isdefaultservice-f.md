# isDefaultService

## 导入模块

```TypeScript
import { cardEmulation } from '@kit.ConnectivityKit';
```

## isDefaultService

```TypeScript
function isDefaultService(elementName: ElementName, type: CardType): boolean
```

判断指定的应用是否为指定业务类型的默认应用。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_CARD_EMULATION

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.CardEmulation

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| elementName | [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-elementname-i.md) | 是 | 所属应用声明NFC卡模拟能力的页面信息（至少包含bundleName、abilityName这两项的赋值），不可以为空。 |
| type | CardType | 是 | 卡模拟业务类型。目前只支持默认支付应用查询。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true: 是默认支付应用， false: 不是默认支付应用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
// 适用于除轻量级智能穿戴产品之外其他设备
import { cardEmulation } from '@kit.ConnectivityKit';
import { bundleManager, Want } from '@kit.AbilityKit';

// 需要初始化 elementName、bundleName、abilityName，根据实际应用信息更改为正确的值
let elementName: bundleManager.ElementName = {
  bundleName: "com.example.myapplication",
  moduleName: "entry",
  abilityName: "EntryAbility"
};

let isDefaultService: boolean = cardEmulation.isDefaultService(elementName, cardEmulation.CardType.PAYMENT);
```

```TypeScript
// 适用于轻量级智能穿戴设备
import cardEmulation from '@ohos.nfc.cardEmulation';

let appName = "com.example.testquestionlite";
let isDefaultService = cardEmulation.isDefaultService(appName, cardEmulation.CardType.PAYMENT);
```
