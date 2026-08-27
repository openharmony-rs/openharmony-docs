# MifareClassicTag

MifareClassicTag提供对MIFARE Classic属性和I/O操作的访问，继承自[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。TagSession是所有NFC Tag技术类型的基类， 提供建立连接和发送数据等共同接口。具体请参见[TagSession](arkts-connectivity-tagsession-tagsession-i.md)。MifareClassicTag获取方式请参考[nfc-tag开发指南](../../../connectivity/nfc/nfc-tag-access-guide.md)。以下是MifareClassicTag的独有接口。

**继承/实现关系：** MifareClassicTag extends TagSession

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NFC.Tag

## authenticateSector

```TypeScript
authenticateSector(sectorIndex: number, key: number[], isKeyA: boolean): Promise<void>
```

使用密钥对扇区进行身份验证，只有身份验证成功的扇区可以进行操作。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sectorIndex | number | 是 | 待验证的扇区索引，从0开始。 |
| key | number[] | 是 | 用于扇区验证的密钥（6字节）。 |
| isKeyA | boolean | 是 | isKeyA标志。true 表示KeyA，false 表示KeyB。 |

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

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let sectorIndex = 1; // 将其更改为正确的 index
        let key = [0x01, 0x02, 0x03, 0x04, 0x05, 0x06]  // 必须是6个字节，将其更改为正确的key
        mifareClassic.authenticateSector(sectorIndex, key, true).then(() => {
            console.info("mifareClassic authenticateSector Promise success.");
        }).catch((err : BusinessError)=> {
            console.error("mifareClassic authenticateSector Promise errCode: ${err.code}, " + "message: ${err.message}");
        });
    } catch (businessError) {
        console.error(`mifareClassic authenticateSector Promise catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## authenticateSector

```TypeScript
authenticateSector(sectorIndex: number, key: number[], isKeyA: boolean, callback: AsyncCallback<void>): void
```

使用密钥对扇区进行身份验证，只有身份验证成功的扇区可以进行操作。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sectorIndex | number | 是 | 待验证的扇区索引，从0开始。 |
| key | number[] | 是 | 用于扇区验证的密钥（6字节）。 |
| isKeyA | boolean | 是 | isKeyA标志。true 表示KeyA，false 表示KeyB。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当身份验证成功时，err为undefined，否则为错误对象。 |

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

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let sectorIndex = 1; // 将其更改为正确的 index
        let key = [0x01, 0x02, 0x03, 0x04, 0x05, 0x06]  // 必须是6个字节，将其更改为正确的key
        mifareClassic.authenticateSector(sectorIndex, key, true, (err : BusinessError)=> {
            if (err) {
                console.error(`mifareClassic authenticateSector AsyncCallback errCode: ${err.code}, message: ${err.message}`);
            } else {
                console.info("mifareClassic authenticateSector AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`mifareClassic authenticateSector AsyncCallback catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## decrementBlock

```TypeScript
decrementBlock(blockIndex: number, value: number): Promise<void>
```

对指定块的内容，减少指定的数值，并将结果存储在内部传输缓冲器中。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blockIndex | number | 是 | 要被运算的块索引，从0开始。 |
| value | number | 是 | 要减少的数值，非负数。 |

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

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // 将其更改为正确的 index
        let value = 0x20; // 将其更改为正确的数据
        mifareClassic.decrementBlock(blockIndex, value).then(() => {
            console.info("mifareClassic decrementBlock Promise success.");
        }).catch((err : BusinessError)=> {
            console.error("mifareClassic decrementBlock Promise errCode: ${err.code}, message: ${err.message}");
        });
    } catch (businessError) {
        console.error(`mifareClassic decrementBlock Promise catch businessError: Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## decrementBlock

```TypeScript
decrementBlock(blockIndex: number, value: number, callback: AsyncCallback<void>): void
```

对指定块的内容，减少指定的数值。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blockIndex | number | 是 | 要被运算的块索引，从0开始。 |
| value | number | 是 | 要减少的数值，非负数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当对块减少指定数值成功时，err为undefined，否则为错误对象。 |

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

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // 将其更改为正确的 index
        let value = 0x20; // 将其更改为正确的数据
        mifareClassic.decrementBlock(blockIndex, value, (err : BusinessError)=> {
            if (err) {
                console.error("mifareClassic decrementBlock AsyncCallback errCode:" + 
                  "${err.code}, message: ${err.message}");
            } else {
                console.info("mifareClassic decrementBlock AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`mifareClassic decrementBlock AsyncCallback catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## getBlockCountInSector

```TypeScript
getBlockCountInSector(sectorIndex: number): number
```

获取指定扇区中的块数。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sectorIndex | number | 是 | 扇区序号，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 该扇区内的块数量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic

try {
    let sectorIndex = 1; // 将其更改为正确的 index
    let blockCnt : number = mifareClassic.getBlockCountInSector(sectorIndex);
    console.info("mifareClassic blockCnt: " + blockCnt);
} catch (businessError) {
    console.error(`mifareClassic getBlockCountInSector catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
}
```

## getBlockIndex

```TypeScript
getBlockIndex(sectorIndex: number): number
```

获取特定扇区的第一个块的序号。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sectorIndex | number | 是 | 扇区序号，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 该扇区内的第一个块的序号，从0开始。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic

try {
    let sectorIndex = 1; // 将其更改为正确的 index
    let blockIndex : number = mifareClassic.getBlockIndex(sectorIndex);
    console.info("mifareClassic blockIndex: " + blockIndex);
} catch (businessError) {
    console.error(`mifareClassic getBlockIndex catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
}
```

## getSectorCount

```TypeScript
getSectorCount(): number
```

获取MIFARE Classic标签中的扇区数。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 标签中的扇区数量。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic
let sectorCount : number = mifareClassic.getSectorCount();
console.info("mifareClassic sectorCount: " + sectorCount);
```

## getSectorIndex

```TypeScript
getSectorIndex(blockIndex: number): number
```

获取包含指定块号的扇区序号。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blockIndex | number | 是 | 块序号，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 扇区序号，从0开始。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic

try {
    let blockIndex = 1; // 将其更改为正确的 index
    let sectorIndex : number = mifareClassic.getSectorIndex(blockIndex);
    console.info("mifareClassic sectorIndex: " + sectorIndex);
} catch (businessError) {
    console.error(`mifareClassic getSectorIndex catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
}
```

## getTagSize

```TypeScript
getTagSize(): number
```

获取标签的存储空间大小，具体请参见[MifareClassicSize](arkts-connectivity-tag-mifareclassicsize-e.md)。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 标签的大小，单位为字节，请参见[MifareClassicSize]{ |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic
let tagSize : number = mifareClassic.getTagSize();
console.info("mifareClassic tagSize: " + tagSize);
```

## getType

```TypeScript
getType(): tag.MifareClassicType
```

获取MIFARE Classic标签的类型。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| tag.MifareClassicType | MifareClassic标签的类型。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic
let getType : tag.MifareClassicType = mifareClassic.getType();
console.info("mifareClassic getType: " + getType);
```

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareUltralight
let getType : tag.MifareUltralightType = mifareUltralight.getType();
console.info("mifareUltralight getType: " + getType);
```

## incrementBlock

```TypeScript
incrementBlock(blockIndex: number, value: number): Promise<void>
```

对指定块的内容，增加指定的数值，并将结果存储在内部传输缓冲器中。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blockIndex | number | 是 | 要指定增加的块索引，从0开始。 |
| value | number | 是 | 要指定增加的数据，非负数。 |

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

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // 将其更改为正确的 index
        let value = 0x20; // 将其更改为正确的数据
        mifareClassic.incrementBlock(blockIndex, value).then(() => {
            console.info("mifareClassic incrementBlock Promise success.");
        }).catch((err : BusinessError)=> {
            console.error(`mifareClassic incrementBlock Promise err Code: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`mifareClassic incrementBlock Promise catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## incrementBlock

```TypeScript
incrementBlock(blockIndex: number, value: number, callback: AsyncCallback<void>): void
```

对指定块的内容，增加指定的数值，并将结果存储在内部传输缓冲器中。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blockIndex | number | 是 | 要被运算的块索引，从0开始。 |
| value | number | 是 | 要增加的数值，非负数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当对块增加指定数值成功时，err为undefined，否则为错误对象。 |

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

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // 将其更改为正确的 index
        let value = 0x20; // 将其更改为正确的数据
        mifareClassic.incrementBlock(blockIndex, value, (err : BusinessError)=> {
            if (err) {
                console.error(`mifareClassic incrementBlock AsyncCallback err Code: ${err.code}, message: ${err.message}`);
            } else {
                console.info("mifareClassic incrementBlock AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`mifareClassic incrementBlock AsyncCallback catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## isEmulatedTag

```TypeScript
isEmulatedTag(): boolean
```

检查标签是不是被模拟的。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检查结果，true: 是；false：否。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic
let isEmulatedTag : boolean = mifareClassic.isEmulatedTag();
console.info("mifareClassic isEmulatedTag: " + isEmulatedTag);
```

## readSingleBlock

```TypeScript
readSingleBlock(blockIndex: number): Promise<number[]>
```

读取标签中一个块存储的内容，一个块大小为16字节。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blockIndex | number | 是 | 要读取的块索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number[] & gt; | Promise对象。返回读取的块数据。 |

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

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // 将其更改为正确的 index
        mifareClassic.readSingleBlock(blockIndex).then((data : number[]) => {
            console.info("mifareClassic readSingleBlock Promise data: " + data);
        }).catch((err : BusinessError)=> {
            console.error(`mifareClassic readSingleBlock Promise errCode: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`mifareClassic readSingleBlock Promise catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## readSingleBlock

```TypeScript
readSingleBlock(blockIndex: number, callback: AsyncCallback<number[]>): void
```

读取标签中一个块存储的内容，一个块大小为16字节。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blockIndex | number | 是 | 要读取的块索引，从0开始。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number[]&gt; | 是 | 以callback形式异步返回读取到的块数据。 |

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

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1;  // 将其更改为正确的 index
        mifareClassic.readSingleBlock(blockIndex, (err : BusinessError, data : number[])=> {
            if (err) {
                console.error("mifareClassic readSingleBlock AsyncCallback err: " + err);
            } else {
                console.info("mifareClassic readSingleBlock AsyncCallback data: " + data);
            }
        });
    } catch (businessError) {
        console.error(`mifareClassic readSingleBlock AsyncCallback catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## restoreFromBlock

```TypeScript
restoreFromBlock(blockIndex: number): Promise<void>
```

将指定块的值复制到临时寄存器。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blockIndex | number | 是 | 被操作的块的索引，从0开始。 |

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

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }   
    }

    try {
        let blockIndex = 1; // 将其更改为正确的 index
        mifareClassic.restoreFromBlock(blockIndex).then(() => {
            console.info("mifareClassic restoreFromBlock Promise success.");
        }).catch((err : BusinessError)=> {
            console.error(`mifareClassic restoreFromBlock Promise errCode: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`mifareClassic restoreFromBlock Promise catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## restoreFromBlock

```TypeScript
restoreFromBlock(blockIndex: number, callback: AsyncCallback<void>): void
```

将指定块的值复制到临时寄存器。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blockIndex | number | 是 | 被操作的块的索引，从0开始。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当复制指定块内容到临时寄存器成功时，err为undefined，否则为错误对象。 |

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

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // 将其更改为正确的 index
        mifareClassic.restoreFromBlock(blockIndex, (err : BusinessError)=> {
            if (err) {
                console.error(`mifareClassic restoreFromBlock AsyncCallback err Code: ${err.code}, message: ${err.message}`);
            } else {
                console.info("mifareClassic restoreFromBlock AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`mifareClassic restoreFromBlock AsyncCallback catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## transferToBlock

```TypeScript
transferToBlock(blockIndex: number): Promise<void>
```

将临时寄存器的值转移到指定的块。使用Promise异步异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blockIndex | number | 是 | 被操作的块的索引，从0开始。 |

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

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // 将其更改为正确的 index
        mifareClassic.transferToBlock(blockIndex).then(() => {
            console.info("mifareClassic transferToBlock Promise success.");
        }).catch((err : BusinessError)=> {
            console.error(`mifareClassic transferToBlock Promise err Code: ${err.code}, message: ${err.message}`);
        });
    } catch (businessError) {
        console.error(`mifareClassic transferToBlock Promise catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## transferToBlock

```TypeScript
transferToBlock(blockIndex: number, callback: AsyncCallback<void>): void
```

将临时寄存器的值转移到指定的块。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blockIndex | number | 是 | 被操作的块的索引，从0开始。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当临时寄存器的值转移到指定块成功时，err为undefined，否则为错误对象。 |

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

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // 将其更改为正确的 index
        mifareClassic.transferToBlock(blockIndex, (err : BusinessError)=> {
            if (err) {
                console.error(`mifareClassic transferToBlock AsyncCallback errCode: ${err.code}, message: ${err.message}`);
            } else {
                console.info("mifareClassic transferToBlock AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`mifareClassic transferToBlock AsyncCallback catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## writeSingleBlock

```TypeScript
writeSingleBlock(blockIndex: number, data: number[]): Promise<void>
```

向标签中一个块存储写入内容，一个块大小为16字节。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blockIndex | number | 是 | 要写入的块索引，从0开始。 |
| data | number[] | 是 | 要写入的数据，大小必须是16个字节。 |

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

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // 将其更改为正确的 index
        let rawData = [0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x0A,
            0x0B, 0x0C, 0x0D, 0x0E, 0x0F, 0x10]; // 必须是16个字节，将其更改为正确的key
        mifareClassic.writeSingleBlock(blockIndex, rawData).then(() => {
            console.info("mifareClassic writeSingleBlock Promise success.");
        }).catch((err : BusinessError)=> {
            console.error("mifareClassic writeSingleBlock Promise errCode: ${err.code}, message: ${err.message}");
        });
    } catch (businessError) {
        console.error(`mifareClassic writeSingleBlock Promise catch businessError Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```

## writeSingleBlock

```TypeScript
writeSingleBlock(blockIndex: number, data: number[], callback: AsyncCallback<void>): void
```

向标签中一个块存储写入内容，一个块大小为16字节。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blockIndex | number | 是 | 要写入的块索引，从0开始。 |
| data | number[] | 是 | 要写入的数据，大小必须是16个字节。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当向块存储写入内容成功时，err为undefined，否则为错误对象。 |

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

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，获取正确的 mifareClassic

function nfcTechDemo() {
    // 如果没有连接Tag，请先连接
    if (!mifareClassic.isTagConnected()) {
        if (!mifareClassic.connectTag()) {
            console.error("mifareClassic connectTag failed.");
            return;
        }
    }

    try {
        let blockIndex = 1; // 将其更改为正确的 index
        let rawData = [0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x0A,
            0x0B, 0x0C, 0x0D, 0x0E, 0x0F, 0x10]; // 必须是16个字节，将其更改为正确的data
        mifareClassic.writeSingleBlock(blockIndex, rawData, (err : BusinessError)=> {
            if (err) {
                console.error(`mifareClassic writeSingleBlock AsyncCallback err Code: ${err.code}, message: ${err.message}`);
            } else {
                console.info("mifareClassic writeSingleBlock AsyncCallback success.");
            }
        });
    } catch (businessError) {
        console.error(`mifareClassic writeSingleBlock AsyncCallback catch Code: ${(businessError as BusinessError).code}, message: ${(businessError as BusinessError).message}`);
    }
}
```
