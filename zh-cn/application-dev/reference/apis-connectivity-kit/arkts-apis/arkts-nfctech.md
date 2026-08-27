# nfctech(标准NFC-Tag Nfc 技术)

本模块主要用于采用不同Nfc技术的Tag的读写操作。
 > **注意：**
 >
 > 导入tag模块编辑器报错，在某个具体设备型号上能力可能超出工程默认设备定义的能力集范围，如需要使用此部分能力需额外配置自定义syscap，参考
 > [syscap开发指南](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/syscap)。


## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [BarcodeTag(标准NFC-Tag Nfc 技术)](arkts-connectivity-nfctech-barcodetag-i.md) | BarcodeTag提供读取条形码标签的属性和访问I/O操作的能力，继承自TagSession。TagSession是所有NFC Tag 技术类型的基类， 提供建立连接和发送数据等共同接口。具体请参见[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。BarcodeTag获取方式请参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。以下是BarcodeTag的独有接口。 |
| [IsoDepTag(标准NFC-Tag Nfc 技术)](arkts-connectivity-nfctech-isodeptag-i.md) | IsoDepTag 提供对ISO-DEP(ISO 14443-4)技术的属性和I/O操作的访问，继承自TagSession。TagSession是所有NFC Tag技术类型的基类， 提供建立连接和发送数据等共同接口。具体请参见[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。IsoDepTag获取方式请参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。以下是IsoDepTag的独有接口。 |
| [MifareClassicTag(标准NFC-Tag Nfc 技术)](arkts-connectivity-nfctech-mifareclassictag-i.md) | MifareClassicTag提供对MIFARE Classic属性和I/O操作的访问，继承自[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。TagSession是所有NFC Tag技术类型的基类， 提供建立连接和发送数据等共同接口。具体请参见[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。MifareClassicTag获取方式请参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。以下是MifareClassicTag的独有接口。 |
| [MifareUltralightTag(标准NFC-Tag Nfc 技术)](arkts-connectivity-nfctech-mifareultralighttag-i.md) | MifareUltralightTag 提供对MIFARE Ultralight属性和I/O操作的访问，继承自TagSession。TagSession是所有NFC Tag技术类型的基类， 提供建立连接和发送数据等共同接口。具体请参见[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。MifareUltralightTag获取方式请参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。以下是MifareUltralightTag的独有接口。 |
| [NdefFormatableTag(标准NFC-Tag Nfc 技术)](arkts-connectivity-nfctech-ndefformatabletag-i.md) | NdefFormatableTag为NDEF Formattable的标签提供格式化操作，继承自TagSession。TagSession是所有NFC Tag 技术类型的基类， 提供建立连接和发送数据等共同接口。具体请参见[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。NdefFormatableTag获取方式请参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。以下是NdefFormatableTag的独有接口。 |
| [NdefMessage(标准NFC-Tag Nfc 技术)](arkts-connectivity-nfctech-ndefmessage-i.md) |  |
| [NdefTag(标准NFC-Tag Nfc 技术)](arkts-connectivity-nfctech-ndeftag-i.md) | 提供对已格式化为NDEF的NFC标签的数据和操作的访问，继承自TagSession。TagSession是所有NFC Tag技术类型的基类，提供建立连接和发送数据等共同接口。具体请参见[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。NdefTag获取方式请参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。以下是NdefTag的独有接口。 |
| [NfcATag(标准NFC-Tag Nfc 技术)](arkts-connectivity-nfctech-nfcatag-i.md) | NfcATag 提供 NFC-A(ISO 14443-3A)技术的属性和I/O操作的访问，继承自[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。TagSession是所有NFC Tag技术类型的基类， 提供建立连接和发送数据等共同接口。具体请参见[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。NfcATag获取方式请参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。以下是NfcATag的独有接口。 |
| [NfcBTag(标准NFC-Tag Nfc 技术)](arkts-connectivity-nfctech-nfcbtag-i.md) | NfcBTag 提供对NFC-B(ISO 14443-3B)技术的属性和I/O操作的访问，继承自TagSession。TagSession是所有NFC Tag技术类型的基类，提供建立连接和发送数据等共同接口。具体请参见[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。NfcBTag获取方式请参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。以下是NfcBTag的独有接口。 |
| [NfcFTag(标准NFC-Tag Nfc 技术)](arkts-connectivity-nfctech-nfcftag-i.md) | NfcFTag 提供对NFC-F(JIS 6319-4)技术的属性和I/O操作的访问，继承自TagSession。TagSession是所有NFC Tag技术类型的基类， 提供建立连接和发送数据等共同接口。具体请参见[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。NfcFTag获取方式请参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。以下是NfcFTag的独有接口。 |
| [NfcVTag(标准NFC-Tag Nfc 技术)](arkts-connectivity-nfctech-nfcvtag-i.md) | NfcVTag 提供对NFC-V(ISO 15693)技术的属性和I/O操作的访问，继承自TagSession。TagSession是所有NFC Tag技术类型的基类， 提供建立连接和发送数据等共同接口。具体请参见[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。NfcVTag获取方式请参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。以下是NfcVTag的独有接口。 |
