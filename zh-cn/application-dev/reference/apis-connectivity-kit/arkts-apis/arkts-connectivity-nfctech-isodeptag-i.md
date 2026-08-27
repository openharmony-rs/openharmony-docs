# IsoDepTag

IsoDepTag 提供对ISO-DEP(ISO 14443-4)技术的属性和I/O操作的访问，继承自TagSession。TagSession是所有NFC Tag技术类型的基类， 提供建立连接和发送数据等共同接口。具体请参见[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。IsoDepTag获取方式请参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。以下是IsoDepTag的独有接口。

**继承/实现关系：** IsoDepTag extends TagSession

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NFC.Tag

## getHiLayerResponse

```TypeScript
getHiLayerResponse(): number[]
```

获取标签的更高层响应字节，针对基于NfcB通信技术的IsoDep卡片。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | IsoDepTag 标签的更高层响应字节，每个number十六进制表示，范围是0x00~0xFF。如果该IsoDep类型Tag是基于NfcA技术的，则该返回值为空。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 isoDep
let hiLayerResponse : number[] = isoDep.getHiLayerResponse();
console.info("isoDep hiLayerResponse: " + hiLayerResponse);
```

## getHistoricalBytes

```TypeScript
getHistoricalBytes(): number[]
```

获取标签的历史字节，针对基于NfcA通信技术的IsoDep卡片。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number[] | IsoDepTag 标签的历史字节，每个number十六进制表示，范围是0x00~0xFF。如果该IsoDep类型Tag是基于NfcB技术的，则该返回值为空。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 isoDep
let historicalBytes : number[] = isoDep.getHistoricalBytes();
console.info("isoDep historicalBytes: " + historicalBytes);
```

## isExtendedApduSupported

```TypeScript
isExtendedApduSupported(): Promise<boolean>
```

检查是否支持扩展的APDU，使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | Promise对象。返回true表示支持；返回false表示不支持。 |

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

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 isoDep
function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!isoDep.isTagConnected()) {
        if (!isoDep.connectTag()) {
            console.error("isoDep connectTag failed.");
            return;
        }
    }

    try {
        isoDep.isExtendedApduSupported().then((response: boolean) => {
            console.info("isoDep isExtendedApduSupported Promise response: " + response);
        }).catch((err: BusinessError) => {
            console.error(`isoDep isExtendedApduSupported Promise Code: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`isoDep isExtendedApduSupported Promise Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## isExtendedApduSupported

```TypeScript
isExtendedApduSupported(callback: AsyncCallback<boolean>): void
```

检查是否支持扩展的APDU。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数，true: 支持， false: 不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [3100201](../errorcode-nfc.md#3100201-nfc服务读写tag错误) | The tag running state is abnormal in the service. |
| [3100204](../errorcode-nfc.md#3100204-nfc芯片io异常) | The Tag I/O operation failed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 isoDep
function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!isoDep.isTagConnected()) {
        if (!isoDep.connectTag()) {
            console.error("isoDep connectTag failed.");
            return;
        }
    }

    try {
        isoDep.isExtendedApduSupported((err: BusinessError, response: boolean) => {
            if (err) {
                console.error(`isoDep isExtendedApduSupported AsyncCallback Code: ${err.code}, message: ${err. message}`);
            } else {
                console.info("isoDep isExtendedApduSupported AsyncCallback response: " + response);
            }
        });
    } catch (businessError) {
        console.error(`isoDep isExtendedApduSupported AsyncCallback Code: ${(businessError as Business).code}, message: ${(businessError as Business).message}`);
    }
}
```
