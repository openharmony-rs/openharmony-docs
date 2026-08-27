# NdefFormatableTag

NdefFormatableTag为NDEF Formattable的标签提供格式化操作，继承自TagSession。TagSession是所有NFC Tag 技术类型的基类， 提供建立连接和发送数据等共同接口。具体请参见[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。NdefFormatableTag获取方式请参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。以下是NdefFormatableTag的独有接口。

**继承/实现关系：** NdefFormatableTag extends TagSession

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NFC.Tag

## format

```TypeScript
format(message: NdefMessage): Promise<void>
```

将标签格式化为NDEF标签，将NDEF消息写入NDEF标签。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | [NdefMessage](arkts-connectivity-nfctech-ndefmessage-i.md) | 是 | 格式化成功时要写入的NDEF消息。可以为null，为null时仅格式化标签，不写入内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [3100201](../errorcode-nfc.md#3100201-nfc服务读写tag错误) | The tag running state is abnormal in the service. |
| [3100204](../errorcode-nfc.md#3100204-nfc芯片io异常) | The tag I/O operation failed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 ndefFormatable

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!ndefFormatable.isTagConnected()) {
        if (!ndefFormatable.connectTag()) {
            console.error("ndefFormatable connectTag failed.");
            return;
        }
    }

    try {
        // 从原始数据创建的ndefMessage，例如：
        let ndefMessage = tag.ndef.createNdefMessage([0xD1, 0x01, 0x03, 0x54, 0x4E, 0x46, 0x43]);  
        // 必须是可以被解析的NDEF记录
        // 或从 tag.ndef.createNdefMessage(ndefRecords:NdefRecord[]) 创建 ndefMessage

        ndefFormatable.format(ndefMessage).then(() => {
            console.info("ndefFormatable format Promise success.");
        }).catch((err : BusinessError)=> {
            console.error(`ndefFormatable format Promise err Code: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`ndefFormatable format Promise catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 ndefFormatable

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!ndefFormatable.isTagConnected()) {
        if (!ndefFormatable.connectTag()) {
            console.error("ndefFormatable connectTag failed.");
            return;
        }
    }

    try {
        // 从原始数据创建的ndefMessage，例如：
        let ndefMessage = tag.ndef.createNdefMessage([0xD1, 0x01, 0x03, 0x54, 0x4E, 0x46, 0x43]);  // 必须是可以被解析的NDEF记录
        // 或从 tag.ndef.createNdefMessage(ndefRecords:NdefRecord[]) 创建 ndefMessage

        ndefFormatable.format(ndefMessage, (err : BusinessError)=> {
            if (err) {
                console.error(`ndefFormatable format AsyncCallback Code: ${err.code}, message: ${err.message}`);
            } else {
                console.info("ndefFormatable format AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`ndefFormatable format AsyncCallback catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## format

```TypeScript
format(message: NdefMessage, callback: AsyncCallback<void>): void
```

将标签格式化为NDEF标签，然后将NDEF消息写入NDEF标签。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | [NdefMessage](arkts-connectivity-nfctech-ndefmessage-i.md) | 是 | 格式化成功时要写入的Ndef消息。可以为null，为null时仅格式化标签，不写入内容。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当NDEF消息写入标签成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [3100201](../errorcode-nfc.md#3100201-nfc服务读写tag错误) | The tag running state is abnormal in the service. |
| [3100204](../errorcode-nfc.md#3100204-nfc芯片io异常) | The Tag I/O operation failed.<br>**适用版本：** 12+ |

**示例**

参见 [format](#format)

## formatReadOnly

```TypeScript
formatReadOnly(message: NdefMessage): Promise<void>
```

将标签格式化为NDEF标签，将NDEF消息写入NDEF标签，之后将标签设置为只读。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | [NdefMessage](arkts-connectivity-nfctech-ndefmessage-i.md) | 是 | 格式化成功时要写入的NDEF消息。可以为null，为null时仅格式化标签，不写入内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [3100201](../errorcode-nfc.md#3100201-nfc服务读写tag错误) | The tag running state is abnormal in the service. |
| [3100204](../errorcode-nfc.md#3100204-nfc芯片io异常) | The tag I/O operation failed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 ndefFormatable

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!ndefFormatable.isTagConnected()) {
        if (!ndefFormatable.connectTag()) {
            console.error("ndefFormatable connectTag failed.");
            return;
        }
    }

    try {
        // 从原始数据创建的ndefMessage，例如：
        let ndefMessage = tag.ndef.createNdefMessage([0xD1, 0x01, 0x03, 0x54, 0x4E, 0x46, 0x43]);
        // 必须是可以被解析的NDEF记录
        // 或从 tag.ndef.createNdefMessage(ndefRecords:NdefRecord[]) 创建 ndefMessage

        ndefFormatable.formatReadOnly(ndefMessage).then(() => {
            console.info("ndefFormatable formatReadOnly Promise success.");
        }).catch((err : BusinessError)=> {
            console.error(`ndefFormatable formatReadOnly Promise Code: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`ndefFormatable formatReadOnly Promise catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 ndefFormatable

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!ndefFormatable.isTagConnected()) {
        if (!ndefFormatable.connectTag()) {
            console.error("ndefFormatable connectTag failed.");
            return;
        }
    }

    try {
        // 从原始数据创建的ndefMessage，例如：
        let ndefMessage = tag.ndef.createNdefMessage([0xD1, 0x01, 0x03, 0x54, 0x4E, 0x46, 0x43]);
        // 必须是可以被解析的NDEF记录
        // 或从 tag.ndef.createNdefMessage(ndefRecords:NdefRecord[]) 创建 ndefMessage

        ndefFormatable.formatReadOnly(ndefMessage, (err : BusinessError)=> {
            if (err) {
                console.error(`ndefFormatable formatReadOnly AsyncCallback err Code: ${err.code}, message: ${err.message}`);
            } else {
                console.info("ndefFormatable formatReadOnly AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`ndefFormatable formatReadOnly AsyncCallback catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## formatReadOnly

```TypeScript
formatReadOnly(message: NdefMessage, callback: AsyncCallback<void>): void
```

将标签格式化为NDEF标签，然后将NDEF消息写入NDEF标签，之后将标签设置为只读。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| message | [NdefMessage](arkts-connectivity-nfctech-ndefmessage-i.md) | 是 | 格式化成功时要写入的NDEF消息。可以为null，为null时仅格式化标签，不写入内容。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当NDEF消息写入NDEF标签成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [3100201](../errorcode-nfc.md#3100201-nfc服务读写tag错误) | The tag running state is abnormal in the service. |
| [3100204](../errorcode-nfc.md#3100204-nfc芯片io异常) | The Tag I/O operation failed.<br>**适用版本：** 12+ |

**示例**

参见 [formatReadOnly](#formatreadonly)
