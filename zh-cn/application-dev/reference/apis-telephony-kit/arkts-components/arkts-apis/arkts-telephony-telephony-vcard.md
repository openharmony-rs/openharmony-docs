# @ohos.telephony.vcard(VCard模块)

VCard是电子名片的文件格式标准，它可包含的信息有：姓名、地址资讯、电话号码、URL、logo、相片等。VCard模块提供了VCard能力，包括将VCard文件导入联系人数据库和将联系人数据导出为VCard文件等。

**起始版本：** 11

**系统能力：** SystemCapability.Telephony.CoreService

## 导入模块

```TypeScript
import { vcard } from '@kit.TelephonyKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [exportVCard](arkts-telephony-vcard-exportvcard-f.md) | 将联系人导出为 VCF(vcard file)文件。使用callback异步回调。 |
| [exportVCard](arkts-telephony-vcard-exportvcard-f.md) | 将联系人导出为 VCF(vcard file)文件。使用Promise异步回调。 |
| [exportVCard](arkts-telephony-vcard-exportvcard-f.md) | 将联系人导出为 VCF(vcard file)文件。使用callback异步回调。 |
| [importVCard](arkts-telephony-vcard-importvcard-f.md) | 将VCard文件导入联系人数据库。使用callback异步回调。 |
| [importVCard](arkts-telephony-vcard-importvcard-f.md) | 将VCard文件导入联系人数据库。使用Promise异步回调。 |
| [importVCard](arkts-telephony-vcard-importvcard-f.md) | 将VCard文件导入联系人数据库。使用callback异步回调。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [VCardBuilderOptions](arkts-telephony-vcard-vcardbuilderoptions-i.md) | VCard版本和编码信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [VCardType](arkts-telephony-vcard-vcardtype-e.md) | VCard版本类型。 |
