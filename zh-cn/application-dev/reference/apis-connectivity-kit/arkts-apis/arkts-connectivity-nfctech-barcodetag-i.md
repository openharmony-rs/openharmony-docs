# BarcodeTag

BarcodeTag提供读取条形码标签的属性和访问I/O操作的能力，继承自TagSession。TagSession是所有NFC Tag 技术类型的基类， 提供建立连接和发送数据等共同接口。具体请参见[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。BarcodeTag获取方式请参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。以下是BarcodeTag的独有接口。

**继承/实现关系：** BarcodeTag extends TagSession

**起始版本：** 18

**系统能力：** SystemCapability.Communication.NFC.Tag

## getBarcode

```TypeScript
getBarcode(): Promise<ArrayBuffer>
```

获取读到的Barcode类型的完整Tag。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;ArrayBuffer & gt; | Promise对象。返回BarCode类型的 tag。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [3100201](../errorcode-nfc.md#3100201-nfc服务读写tag错误) | The tag running state is abnormal in the service. |
| [3100204](../errorcode-nfc.md#3100204-nfc芯片io异常) | The tag I/O operation failed. |
