# @ohos.nfc.cardEmulation(标准NFC-cardEmulation)

本模块主要提供NFC卡模拟业务，包括判断支持哪种卡模拟类型，HCE卡模拟的业务实现等。

HCE(Host Card Emulation)，称为基于主机的卡模拟，表示不依赖安全单元芯片，应用程序模拟NFC卡片，可以通过NFC服务和NFC读卡器通信。

HCE卡模拟和AID列表的声明定义

开发HCE卡模拟相关应用时，需要在应用的属性配置文件中，声明与NFC相关的属性值，比如，在module.json5文件中，声明下面属性值：

> **注意：**
> 
> 1. 声明"actions"字段的内容填写，必须包含"ohos.nfc.cardemulation.action.HOST_APDU_SERVICE"，不能更改。
> 
> 2. 声明aid（参考ISO/IEC 7816-4规范）时，name必须为payment-aid或者other-aid。填写错误会造成解析失败。
> 
> 3. 声明权限时"requestPermissions"中的"name"字段的内容填写，必须是"ohos.permission.NFC_CARD_EMULATION"，不能更改。
> 
> 4. 轻量级智能穿戴产品不同于其他设备，仅支持[FA模型](../../../application-models/ability-terminology.md#fa模型)，属性配置和接口调用方式与其他设备有所区别，详见示例。

**起始版本：** 6

**系统能力：** SystemCapability.Communication.NFC.CardEmulation

## 导入模块

```TypeScript
import { cardEmulation } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [hasHceCapability](arkts-connectivity-cardemulation-hashcecapability-f.md) | 判断设备是否支持HCE卡模拟功能。 |
| [isDefaultService](arkts-connectivity-cardemulation-isdefaultservice-f.md) | 判断指定的应用是否为指定业务类型的默认应用。 |
| [isSupported](arkts-connectivity-cardemulation-issupported-f.md) | 是否支持某种类型的卡模拟。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getPaymentServices](arkts-connectivity-cardemulation-getpaymentservices-f-sys.md) | 获取所有支付类型的服务列表。如果应用程序声明支持HCE功能，并且声明了"payment-aid"，则会包含在列表里面，参考[HCE卡模拟和AID列表的声明定义](../../../reference/apis-connectivity-kit/js-apis-cardEmulation.md#hce卡模拟和aid列表的声明定义)。 |
<!--DelEnd-->

### 类

| 名称 | 说明 |
| --- | --- |
| [HceService](arkts-connectivity-cardemulation-hceservice-c.md) | 提供HCE卡模拟的实现，主要包括接收对端读卡设备的APDU数据，并响应APDU数据到对端读卡设备。使用HCE相关接口前，必须先判断设备是否支持HCE卡模拟能力。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CardType](arkts-connectivity-cardemulation-cardtype-e.md) | 定义卡模拟应用所使用的业务类型，是支付类型，还是其他类型。 |
| [FeatureType](arkts-connectivity-cardemulation-featuretype-e.md) | 定义不同的NFC卡模拟类型。 |
