# @ohos.nfc.controller(标准NFC)

本模块主要用于管理NFC状态，包括打开和关闭NFC，读取NFC的状态等。

**起始版本：** 7

**系统能力：** SystemCapability.Communication.NFC.Core

## 导入模块

```TypeScript
import { nfcController } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [closeNfc](arkts-connectivity-nfccontroller-closenfc-f.md) | 关闭NFC开关。 |
| [disableNfc](arkts-connectivity-nfccontroller-disablenfc-f.md) | 关闭NFC开关，该接口只能被系统应用调用。 |
| [enableNfc](arkts-connectivity-nfccontroller-enablenfc-f.md) | 打开NFC开关，该接口只能被系统应用调用。 |
| [getNfcState](arkts-connectivity-nfccontroller-getnfcstate-f.md) | 查询NFC状态。 |
| [isNfcAvailable](arkts-connectivity-nfccontroller-isnfcavailable-f.md) | 查询设备是否有NFC能力。 |
| [isNfcOpen](arkts-connectivity-nfccontroller-isnfcopen-f.md) | 查询NFC是否打开。 |
| [isNfcSupported](arkts-connectivity-nfccontroller-isnfcsupported-f.md) | 查询设备是否有NFC能力。 |
| [off](arkts-connectivity-nfccontroller-off-f.md#offnfcstatechange) | 取消NFC开关状态事件的注册，取消后NFC状态变化时，就不会再收到Callback的通知。使用callback异步回调。 |
| [on](arkts-connectivity-nfccontroller-on-f.md#onnfcstatechange) | 注册NFC开关状态事件，获取NFC状态的变化通知。使用callback异步回调。 |
| [openNfc](arkts-connectivity-nfccontroller-opennfc-f.md) | 打开NFC开关。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NfcState](arkts-connectivity-nfccontroller-nfcstate-e.md) | 定义不同的NFC状态值。 |
