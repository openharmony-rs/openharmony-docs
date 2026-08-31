# @ohos.nfc.tag(标准NFC-Tag)

本模块主要用于操作及管理NFC Tag，提供后台读卡和前台应用优先分发两种读卡模式。 后台读卡是指不需要打开应用程序，电子设备通过NFC读取标签卡片后，根据标签卡片的类型匹配到一个或多个应用程序。如果仅匹配到一个，则直接拉起应用程序的读卡页面；如果是多个则弹出应用选择器，让用户选择指定的读卡应用。后台读卡不涉及tag相 关接口，示例参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md#后台读取标签)。 前台读卡是指提前打开应用程序，并进入对应的NFC读卡页面后读卡，只会把读到的标签卡片信息分发给前台应用程序。

> **说明：**
> 
> 2. 从API版本26.0.0开始请使用canIUse("SystemCapability.Communication.NFC.Tag")
> && [nfcController.isNfcSupported](arkts-connectivity-nfccontroller-isnfcsupported-f.md)共同判断设备是否支持NFC能力更加准确，否则可能导
> 致应用运行稳定性问题，参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。
> 
> 3. 导入tag模块编辑器报错，在某个具体设备型号上能力可能超出工程默认设备定义的能力集范围，如需要使用此部分能力需额外配置自定义syscap，参考
> [syscap开发指南](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/syscap)。

## 导入模块

```TypeScript
import { tag } from '@kit.ConnectivityKit';
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [tag(标准NFC-Tag)](arkts-connectivity-tag-n.md) | 本模块主要用于操作及管理NFC Tag，提供后台读卡和前台应用优先分发两种读卡模式。 后台读卡是指不需要打开应用程序，电子设备通过NFC读取标签卡片后，根据标签卡片的类型匹配到一个或多个应用程序。如果仅匹配到一个，则直接拉起应用程序的读卡页面；如果是多个则弹出应用选择器，让用户选择指定的读卡应用。后台读卡不涉及tag相 关接口，示例参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md#后台读取标签)。 前台读卡是指提前打开应用程序，并进入对应的NFC读卡页面后读卡，只会把读到的标签卡片信息分发给前台应用程序。 |
