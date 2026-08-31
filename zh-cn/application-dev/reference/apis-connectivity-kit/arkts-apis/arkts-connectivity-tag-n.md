# tag(标准NFC-Tag)

本模块主要用于操作及管理NFC Tag，提供后台读卡和前台应用优先分发两种读卡模式。 后台读卡是指不需要打开应用程序，电子设备通过NFC读取标签卡片后，根据标签卡片的类型匹配到一个或多个应用程序。如果仅匹配到一个，则直接拉起应用程序的读卡页面；如果是多个则弹出应用选择器，让用户选择指定的读卡应用。后台读卡不涉及tag相 关接口，示例参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md#后台读取标签)。 前台读卡是指提前打开应用程序，并进入对应的NFC读卡页面后读卡，只会把读到的标签卡片信息分发给前台应用程序。

> **说明：**
> 
> 2. 从API版本26.0.0开始请使用canIUse("SystemCapability.Communication.NFC.Tag")
> && [nfcController.isNfcSupported](arkts-connectivity-nfccontroller-isnfcsupported-f.md)共同判断设备是否支持NFC能力更加准确，否则可能导
> 致应用运行稳定性问题，参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。
> 
> 3. 导入tag模块编辑器报错，在某个具体设备型号上能力可能超出工程默认设备定义的能力集范围，如需要使用此部分能力需额外配置自定义syscap，参考
> [syscap开发指南](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/syscap)。

**起始版本：** 7

**系统能力：** SystemCapability.Communication.NFC.Tag

## 导入模块

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [ndef(标准NFC-Tag)](arkts-connectivity-tag-ndef-n.md) | Provides methods for accessing NDEF tag. |

### 函数

| 名称 | 说明 |
| --- | --- |
| [getNfcATag(标准NFC-Tag)](arkts-connectivity-tag-getnfcatag-f.md) | 获取NFC A类型Tag对象，通过该对象可访问NfcA技术类型的Tag。 |
| [getNfcA(标准NFC-Tag)](arkts-connectivity-tag-getnfca-f.md) | 获取NFC A类型Tag对象，通过该对象可访问NfcA技术类型的Tag。 |
| [getNfcBTag(标准NFC-Tag)](arkts-connectivity-tag-getnfcbtag-f.md) | 获取NFC B类型Tag对象，通过该对象可访问NfcB技术类型的Tag。 |
| [getNfcB(标准NFC-Tag)](arkts-connectivity-tag-getnfcb-f.md) | 获取NFC B类型Tag对象，通过该对象可访问NfcB技术类型的Tag。 |
| [getNfcFTag(标准NFC-Tag)](arkts-connectivity-tag-getnfcftag-f.md) | 获取NFC F类型Tag对象，通过该对象可访问NfcF技术类型的Tag。 |
| [getNfcF(标准NFC-Tag)](arkts-connectivity-tag-getnfcf-f.md) | 获取NFC F类型Tag对象，通过该对象可访问NfcF技术类型的Tag。 |
| [getNfcVTag(标准NFC-Tag)](arkts-connectivity-tag-getnfcvtag-f.md) | 获取NFC V类型Tag对象，通过该对象可访问NfcV技术类型的Tag。 |
| [getNfcV(标准NFC-Tag)](arkts-connectivity-tag-getnfcv-f.md) | 获取NFC V类型Tag对象，通过该对象可访问NfcV技术类型的Tag。 |
| [getIsoDep(标准NFC-Tag)](arkts-connectivity-tag-getisodep-f.md) | 获取IsoDep类型Tag对象，通过该对象可访问支持IsoDep技术类型的Tag。 |
| [getNdef(标准NFC-Tag)](arkts-connectivity-tag-getndef-f.md) | 获取NDEF类型Tag对象，通过该对象可访问支持NDEF技术类型的Tag。 |
| [getMifareClassic(标准NFC-Tag)](arkts-connectivity-tag-getmifareclassic-f.md) | 获取MIFARE Classic类型Tag对象，通过该对象访问支持MIFARE Classic技术类型的Tag。 |
| [getMifareUltralight(标准NFC-Tag)](arkts-connectivity-tag-getmifareultralight-f.md) | 获取MIFARE Ultralight类型Tag对象，通过该对象可访问支持MIFARE Ultralight技术类型的Tag。 |
| [getNdefFormatable(标准NFC-Tag)](arkts-connectivity-tag-getndefformatable-f.md) | 获取NDEF Formatable类型Tag对象，通过该对象可访问支持NDEF Formatable技术类型的Tag。 |
| [getTagInfo(标准NFC-Tag)](arkts-connectivity-tag-gettaginfo-f.md) | 从Want中获取TagInfo，Want是被NFC服务初始化，包含了TagInfo所需的属性值。 |
| [registerForegroundDispatch(标准NFC-Tag)](arkts-connectivity-tag-registerforegrounddispatch-f.md) | 注册对NFC Tag读卡事件的监听，实现前台应用优先分发的目的。通过discTech设置支持的读卡技术类型，通过callback方式获取读取到Tag的[TagInfo](arkts-connectivity-tag-taginfo-i.md)信息。应用必须在前台才能 调用。需要与取消监听接口[tag.unregisterForegroundDispatch](arkts-connectivity-tag-unregisterforegrounddispatch-f.md)成对使用。如果已注册事件监听，需要在页面退出前台或页面销毁 前调用取消注册。使用callback异步回调。 |
| [unregisterForegroundDispatch(标准NFC-Tag)](arkts-connectivity-tag-unregisterforegrounddispatch-f.md) | 取消注册对NFC Tag读卡事件的监听，退出前台应用优先分发。如果已注册事件监听，需要在页面退出前台或页面销毁前调用取消注册。 |
| [on(标准NFC-Tag)](arkts-connectivity-tag-on-f.md#onreadermode) | 订阅NFC Tag读卡事件，实现前台应用优先分发。设备会进入读卡器模式，同时关闭卡模拟。通过discTech设置支持的读卡技术类型，通过callback方式获取到Tag的[TagInfo](arkts-connectivity-tag-taginfo-i.md)信 息。需要与取消读卡器模式的 tag.off成对使用，如果已通过 on进行设置，需要在页面退出前台或页面销毁时调用 tag.off。使用 callback异步回调。与注册读卡器模式的 tag.on 互斥使用。 |
| [off(标准NFC-Tag)](arkts-connectivity-tag-off-f.md#offreadermode) | 取消订阅NFC Tag读卡事件。设备退出读卡模式，并恢复卡模拟。如果已通过 tag.on 设置NFC的读卡器模式，需要在页面退出前台或页面销毁时调用off进行取消。 |
| [on(标准NFC-Tag)](arkts-connectivity-tag-on-f.md#onreadermodewithinterval) | 订阅NFC Tag读卡事件，实现前台应用优先分发，并支持卡在位检测间隔设置。使用callback异步回调。  - 设备会进入读卡器模式，同时关闭卡模拟。  - 通过discTech设置支持的读卡技术类型，通过callback方式获取到Tag的[TagInfo](arkts-connectivity-tag-taginfo-i.md)信息，通过interval设置卡在位检测间隔。  - 需要与取消读卡器模式的  tag.off成对使 用，如果已通过on进行设置，需要在页面退出前台或页面销毁时调用 tag.off。  - 与注册读卡器模式的  tag.on 互斥使用。 |
| [off(标准NFC-Tag)](arkts-connectivity-tag-off-f.md#offreadermodewithinterval) | 取消订阅NFC Tag读卡事件。设备退出读卡模式，并恢复卡模拟。如果已通过 tag.on 设置NFC的读卡器模式，需要在页面退出前台或页面销毁时调用 tag.off进行取 消。使用callback异步回调。 |
| [getBarcodeTag(标准NFC-Tag)](arkts-connectivity-tag-getbarcodetag-f.md) | 获取BarcodeTag类型Tag对象，通过该对象可访问BarcodeTag技术类型的Tag。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [TagInfo(标准NFC-Tag)](arkts-connectivity-tag-taginfo-i.md) | 在对相关Tag类型卡片进行读写之前，必须先获取[TagInfo](arkts-connectivity-tag-taginfo-i.md)相关属性值，以确认设备读取到的Tag卡片支持哪些技术类型。这样Tag应用程序才能调用正确的接口和所读取到的Tag卡片进行通信。 |
| [NdefRecord(标准NFC-Tag)](arkts-connectivity-tag-ndefrecord-i.md) | NDEF标签Record属性的定义，参考NDEF标签技术规范《NFCForum-TS-NDEF_1.0》的定义细节。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [TagInfo(标准NFC-Tag)](arkts-connectivity-tag-taginfo-i-sys.md) | 在对相关Tag类型卡片进行读写之前，必须先获取[TagInfo](arkts-connectivity-tag-taginfo-i.md)相关属性值，以确认设备读取到的Tag卡片支持哪些技术类型。这样Tag应用程序才能调用正确的接口和所读取到的Tag卡片进行通信。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [TnfType(标准NFC-Tag)](arkts-connectivity-tag-tnftype-e.md) | NDEF Record的TNF(Type Name Field)类型值，参考NDEF标签技术规范《NFCForum-TS-NDEF_1.0》的定义细节。 |
| [NfcForumType(标准NFC-Tag)](arkts-connectivity-tag-nfcforumtype-e.md) | NFC Forum标准里面Tag类型的定义。 |
| [MifareClassicType(标准NFC-Tag)](arkts-connectivity-tag-mifareclassictype-e.md) | MIFARE Classic标签类型的定义。 |
| [MifareClassicSize(标准NFC-Tag)](arkts-connectivity-tag-mifareclassicsize-e.md) | MIFARE Classic标签存储大小的定义。 |
| [MifareUltralightType(标准NFC-Tag)](arkts-connectivity-tag-mifareultralighttype-e.md) | MIFARE Ultralight标签类型的定义。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [NfcATag(标准NFC-Tag)](arkts-connectivity-tag-nfcatag-t.md) | 获取NfcATag。 |
| [NfcBTag(标准NFC-Tag)](arkts-connectivity-tag-nfcbtag-t.md) | 获取NfcBTag。 |
| [NfcFTag(标准NFC-Tag)](arkts-connectivity-tag-nfcftag-t.md) | 获取NfcFTag。 |
| [NfcVTag(标准NFC-Tag)](arkts-connectivity-tag-nfcvtag-t.md) | 获取NfcVTag。 |
| [IsoDepTag(标准NFC-Tag)](arkts-connectivity-tag-isodeptag-t.md) | 获取IsoDepTag。 |
| [NdefTag(标准NFC-Tag)](arkts-connectivity-tag-ndeftag-t.md) | 获取NdefTag。 |
| [MifareClassicTag(标准NFC-Tag)](arkts-connectivity-tag-mifareclassictag-t.md) | 获取MifareClassicTag。 |
| [MifareUltralightTag(标准NFC-Tag)](arkts-connectivity-tag-mifareultralighttag-t.md) | 获取MifareUltralightTag。 |
| [NdefFormatableTag(标准NFC-Tag)](arkts-connectivity-tag-ndefformatabletag-t.md) | 获取NdefFormatableTag。 |
| [NdefMessage(标准NFC-Tag)](arkts-connectivity-tag-ndefmessage-t.md) | 获取NdefMessage。 |
| [TagSession(标准NFC-Tag)](arkts-connectivity-tag-tagsession-t.md) | 获取TagSession。<!--no_check--> |
| [BarcodeTag(标准NFC-Tag)](arkts-connectivity-tag-barcodetag-t.md) | 获取BarcodeTag。 |

### 常量

| 名称 | 说明 |
| --- | --- |
| [NFC_A(标准NFC-Tag)](arkts-connectivity-tag-con.md#nfc_a) | NFC-A (ISO 14443-3A)技术。 |
| [NFC_B(标准NFC-Tag)](arkts-connectivity-tag-con.md#nfc_b) | NFC-B (ISO 14443-3B)技术。 |
| [ISO_DEP(标准NFC-Tag)](arkts-connectivity-tag-con.md#iso_dep) | ISO-DEP (ISO 14443-4)技术。 |
| [NFC_F(标准NFC-Tag)](arkts-connectivity-tag-con.md#nfc_f) | NFC-F (JIS 6319-4)技术。 |
| [NFC_V(标准NFC-Tag)](arkts-connectivity-tag-con.md#nfc_v) | NFC-V (ISO 15693)技术。 |
| [NDEF(标准NFC-Tag)](arkts-connectivity-tag-con.md#ndef) | NDEF技术。 |
| [NDEF_FORMATABLE(标准NFC-Tag)](arkts-connectivity-tag-con.md#ndef_formatable) | 可以格式化的NDEF技术。 |
| [MIFARE_CLASSIC(标准NFC-Tag)](arkts-connectivity-tag-con.md#mifare_classic) | MIFARE Classic技术。 |
| [MIFARE_ULTRALIGHT(标准NFC-Tag)](arkts-connectivity-tag-con.md#mifare_ultralight) | MIFARE Ultralight技术。 |
| [RTD_TEXT(标准NFC-Tag)](arkts-connectivity-tag-con.md#rtd_text) | 文本类型的NDEF Record，参考NDEF标签技术规范《NFCForum-TS-NDEF_1.0》的定义细节。 |
| [RTD_URI(标准NFC-Tag)](arkts-connectivity-tag-con.md#rtd_uri) | URI类型的NDEF Record，参考NDEF标签技术规范《NFCForum-TS-NDEF_1.0》的定义细节。 |
| [NFC_BARCODE(标准NFC-Tag)](arkts-connectivity-tag-con.md#nfc_barcode) | BARCODE技术。 |
| [SKIP_NDEF(标准NFC-Tag)](arkts-connectivity-tag-con.md#skip_ndef) | 跳过NDEF检查的技术。 |
