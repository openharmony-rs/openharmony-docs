# getPaymentServices（系统接口）

## 导入模块

```TypeScript
import { cardEmulation } from '@kit.ConnectivityKit';
```

## getPaymentServices

```TypeScript
function getPaymentServices(): AbilityInfo[]
```

获取所有支付类型的服务列表。如果应用程序声明支持HCE功能，并且声明了"payment-aid"，则会包含在列表里面，参考 [HCE卡模拟和AID列表的声明定义](../../../reference/apis-connectivity-kit/js-apis-cardEmulation.md#hce卡模拟和aid列表的声明定义)。

**起始版本：** 11

**需要权限：** ohos.permission.NFC_CARD_EMULATION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NFC.CardEmulation

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AbilityInfo](../../apis-ability-kit/arkts-apis/arkts-ability-abilityinfo-i.md)[] | 返回所有支付类型的服务。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
import { cardEmulation } from '@kit.ConnectivityKit';

let paymentServices = cardEmulation.getPaymentServices();
if (paymentServices == undefined || paymentServices.length == 0) {
  console.error('paymentServices is null.');
}
```
