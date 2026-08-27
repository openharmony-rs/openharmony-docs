# TagSession

本模块是对NFC TagSession的使用说明。

> **注意：**
> 
> 导入tag模块编辑器报错，在某个具体设备型号上能力可能超出工程默认设备定义的能力集范围，如需要使用此部分能力需额外配置自定义syscap，参考
> [syscap开发指南](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/syscap)。

**起始版本：** 7

**系统能力：** SystemCapability.Communication.NFC.Tag

## connect

```TypeScript
connect(): void
```

和标签建立连接。在从标签读取数据或将数据写入标签之前，必须调用此方法。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3100201](../errorcode-nfc.md#3100201-nfc服务读写tag错误) | The tag running state is abnormal in the service. |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

try {
    tag.getIsoDep(tagInfo).connect(); 
    console.info("tag connect success");
} catch (businessError) {
    console.error("tag connect businessError: " + businessError);
}
```

## connectTag

```TypeScript
connectTag(): boolean
```

和标签建立连接。在从标签读取数据或将数据写入标签之前，必须调用此方法。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** connect

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 连接建立成功返回true，失败返回false。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

let connectStatus : boolean = tag.getIsoDep(tagInfo).connectTag();
console.info("connectStatus: " + connectStatus);
```

## getMaxSendLength

```TypeScript
getMaxSendLength(): number
```

查询可以发送到标签的最大数据长度。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getMaxTransmitSize](#getmaxtransmitsize)

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 可以发送到标签的最大数据长度，非负数。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

let maxSendLen = tag.getIsoDep(tagInfo).getMaxSendLength(); 
console.info("tag maxSendLen: " + maxSendLen);
```

## getMaxTransmitSize

```TypeScript
getMaxTransmitSize(): number
```

查询可以发送到标签的最大数据长度。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 可以发送到标签的最大数据长度，非负数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3100201](../errorcode-nfc.md#3100201-nfc服务读写tag错误) | The tag running state is abnormal in the service. |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

try {
    let maxTransmitSize = tag.getIsoDep(tagInfo).getMaxTransmitSize(); 
    console.info("tag maxTransmitSize = " + maxTransmitSize);
} catch (businessError) {
    console.error("tag getMaxTransmitSize businessError: " + businessError);
}
```

## getSendDataTimeout

```TypeScript
getSendDataTimeout(): number
```

查询发送数据到Tag的等待超时时间，单位是毫秒。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getTimeout](#gettimeout)

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 发送数据到Tag的等待超时时间，单位是毫秒，非负数。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

let sendDataTimeout = tag.getIsoDep(tagInfo).getSendDataTimeout(); 
console.info("tag sendDataTimeout: " + sendDataTimeout);
```

## getTagInfo

```TypeScript
getTagInfo(): tag.TagInfo
```

获取该Tag被分发时，NFC服务所提供的Tag数据对象。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getTagInfo](arkts-connectivity-tag-gettaginfo-f.md)

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| tag.TagInfo | NFC服务所提供的Tag数据对象。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

let tagInfo : TagInfo = tag.getIsoDep(tagInfo).getTagInfo();
console.info("tag tagInfo: " + tagInfo);
```

## getTimeout

```TypeScript
getTimeout(): number
```

查询发送数据到Tag的等待超时时间，单位是毫秒。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 发送数据到Tag的等待超时时间，单位是毫秒，非负数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3100201](../errorcode-nfc.md#3100201-nfc服务读写tag错误) | The tag running state is abnormal in the service. |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

try {
    let timeout = tag.getIsoDep(tagInfo).getTimeout(); 
    console.info("tag timeout = " + timeout);
} catch (businessError) {
    console.error("tag getTimeout businessError: " + businessError);
}
```

## isConnected

```TypeScript
isConnected(): boolean
```

检查是否已与标签建立连接。如果返回未连接，则需要先调用[tagSession.connect](#connect)建立连接。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 已建立连接返回 true，未建立连接返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

try {
    let isConnected = tag.getIsoDep(tagInfo).isConnected(); 
    console.info("tag isConnected = " + isConnected);
} catch (businessError) {
    console.error("tag isConnected businessError: " + businessError);
}
```

## isTagConnected

```TypeScript
isTagConnected(): boolean
```

检查是否已与标签建立连接。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isConnected

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 已建立连接返回 true，未建立连接返回false。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

let isTagConnected = tag.getIsoDep(tagInfo).isTagConnected(); 
console.info("isTagConnected: " + isTagConnected);
```

## reset

```TypeScript
reset(): void
```

重置与标签的连接。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [resetConnection](#resetconnection)

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

tag.getIsoDep(tagInfo).reset();
```

## resetConnection

```TypeScript
resetConnection(): void
```

重置与标签的连接。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3100201](../errorcode-nfc.md#3100201-nfc服务读写tag错误) | The tag running state is abnormal in the service. |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

try {
    tag.getIsoDep(tagInfo).resetConnection(); 
    console.info("tag resetConnection success");
} catch (businessError) {
    console.error("tag resetConnection businessError: " + businessError);
}
```

## sendData

```TypeScript
sendData(data: number[]): Promise<number[]>
```

发送指令到Tag上。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** transmit

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | number[] | 是 | 要发送的指令。每个number十六进制表示，范围是0x00~0xFF。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number[] & gt; | Promise对象，返回对端Tag对指令的响应数据，每个number十六进制表示，范围是0x00~0xFF。 |

**示例**

```TypeScript
import tag from '@kit.ConnectivityKit';
import { BusinessError } from '@ohos.base';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

function tagSessionDemo() {
    // 如果没有连接，请先连接tag
    if (!tag.getIsoDep(tagInfo).isTagConnected()) {
        if (!tag.getIsoDep(tagInfo).connectTag()) {
            console.error("tagSession connectTag failed.");
            return;
        }
    }  

    let cmdData = [0x01, 0x02, 0x03, 0x04]; // 更改为正确的 data
    tag.getIsoDep(tagInfo).sendData(cmdData).then((response) => {
    console.info("tagSession sendData Promise response: " + response);
    }).catch((err : BusinessError)=> {
    console.error("tagSession sendData Promise err: " + err);
    });
}
```

## sendData

```TypeScript
sendData(data: number[], callback: AsyncCallback<number[]>): void
```

发送指令到Tag上。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** transmit

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | number[] | 是 | 要发送的指令。每个number十六进制表示，范围是0x00~0xFF。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number[]&gt; | 是 | 回调函数，返回响应数据。每个number十六进制表示，范围是0x00~0xFF。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

function tagSessionDemo() {
    // 如果没有连接，请先连接tag
    if (!tag.getIsoDep(tagInfo).isTagConnected()) {
        if (!tag.getIsoDep(tagInfo).connectTag()) {
            console.error("tagSession connectTag failed.");
            return;
        }
    }

    let cmdData = [0x01, 0x02, 0x03, 0x04]; // 更改为正确的 data
    tag.getIsoDep(tagInfo).sendData(cmdData, (err, response)=> {
        if (err) {
            console.error("tagSession sendData AsyncCallback err: " + err);
        } else {
            console.info("tagSession sendData AsyncCallback response: " + response);
        }
    });
}
```

## setSendDataTimeout

```TypeScript
setSendDataTimeout(timeout: number): boolean
```

设置发送数据到Tag的等待超时时间，单位是毫秒。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** setTimeout

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | 超时时间，单位毫秒，非负值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 设置超时时间成功返回true，设置失败返回false。 |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

let timeoutMs = 700;  // 修改为预期的超时时间
let setStatus = tag.getIsoDep(tagInfo).setSendDataTimeout(timeoutMs); 
console.info("tag setSendDataTimeout setStatus: " + setStatus);
```

## setTimeout

```TypeScript
setTimeout(timeout: number): void
```

设置发送数据到Tag的等待超时时间，单位是毫秒。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| timeout | number | 是 | 超时时间，单位毫秒，非负值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3100201](../errorcode-nfc.md#3100201-nfc服务读写tag错误) | The tag running state is abnormal in the service. |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

let timeoutMs = 700;  // 修改为预期的超时时间
try {
    tag.getIsoDep(tagInfo).setTimeout(timeoutMs); 
    console.info("tag setTimeout success");
} catch (businessError) {
    console.error("tag setTimeout businessError: " + businessError);
}
```

## transmit

```TypeScript
transmit(data: number[]): Promise<number[]>
```

发送指令到Tag上。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | number[] | 是 | 要发送的指令。每个number十六进制表示，范围是0x00~0xFF。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number[] & gt; | Promise对象，返回对端Tag对指令的响应数据，每个number十六进制表示，范围是0x00~0xFF。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3100201](../errorcode-nfc.md#3100201-nfc服务读写tag错误) | The tag running state is abnormal in the service. |
| [3100204](../errorcode-nfc.md#3100204-nfc芯片io异常) | The tag I/O operation failed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

function tagSessionDemo() {
// 如果没有连接，请先连接tag
    try {
        if (!tag.getIsoDep(tagInfo).isConnected()) {
            tag.getIsoDep(tagInfo).connect();
        }
    } catch (businessError) {
        console.error("tag connect businessError: " + businessError);
        return;
    }

    let cmdData = [0x01, 0x02, 0x03, 0x04]; // 更改为正确的 data
    try {
    tag.getIsoDep(tagInfo).transmit(cmdData).then((response) => {
        console.info("tagSession transmit Promise response: " + response);
    }).catch((err : BusinessError)=> {
        console.error("tagSession transmit Promise err: " + err);
    });
    } catch (businessError) {
        console.error("tag transmit businessError: " + businessError);
        return;
    }
}
```

## transmit

```TypeScript
transmit(data: number[], callback: AsyncCallback<number[]>): void
```

发送指令到Tag上。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | number[] | 是 | 要发送的指令。每个number十六进制表示，范围是0x00~0xFF。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number[]&gt; | 是 | 回调函数，返回响应数据。每个number十六进制表示，范围是0x00~0xFF。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. Possible causes:   1. Mandatory parameters are left unspecified.   2. Incorrect parameters types.   3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3100201](../errorcode-nfc.md#3100201-nfc服务读写tag错误) | The tag running state is abnormal in the service. |
| [3100204](../errorcode-nfc.md#3100204-nfc芯片io异常) | The tag I/O operation failed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

function tagSessionDemo() {
    // 如果没有连接，请先连接tag
    try {
        if (!tag.getIsoDep(tagInfo).isConnected()) {
            tag.getIsoDep(tagInfo).connect();
        }
    } catch (businessError) {
        console.error("tag connect businessError: " + businessError);
        return;
    }

    let cmdData = [0x01, 0x02, 0x03, 0x04]; // 更改为正确的 data
    try {
        tag.getIsoDep(tagInfo).transmit(cmdData, (err, response)=> {
            if (err) {
                console.error("tagSession transmit AsyncCallback err: " + err);
            } else {
                console.info("tagSession transmit AsyncCallback response: " + response);
            }
        });
    } catch (businessError) {
        console.error("tag transmit businessError: " + businessError);
        return;
    }
}
```
