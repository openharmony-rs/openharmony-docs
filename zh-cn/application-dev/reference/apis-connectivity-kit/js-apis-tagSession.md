# tagSession (标准NFC-Tag TagSession)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @amunra03-->
<!--Designer: @wenxiaolin-->
<!--Tester: @zs_111-->

本模块是对NFC TagSession的使用说明。

> **说明：**
>
> 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

> **注意：**
>
> 导入tag模块编辑器报错，在某个具体设备型号上能力可能超出工程默认设备定义的能力集范围，如需要使用此部分能力需额外配置自定义syscap，参考[syscap开发指南](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/syscap#syscap开发指导)。

## **导入模块**

```js
import { tag } from '@kit.ConnectivityKit';
```

## TagSession

TagSession是所有[nfcTag技术类型](js-apis-nfctech.md)的基类， 提供建立连接和发送数据等共同接口。

需要通过其子类来访问以下接口。在下面的示例中 统一用 getXXX()表示获取子类实例的方法。

具体使用时,请根据实际采用的nfcTag技术，选择对应的方法，具体请参见[nfcTag](js-apis-nfcTag.md)文档。

### getTagInfo<sup>(deprecated)</sup>

getTagInfo(): tag.TagInfo

获取该Tag被分发时，NFC服务所提供的Tag数据对象。

> **说明：**
> 从 API version 7 开始支持，从 API version 9 开始废弃，建议使用[tag.getTagInfo](js-apis-nfcTag.md#taggettaginfo9)替代。

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| **类型** | **说明**                             |
| ------------------ | --------------------------|
| tag.TagInfo  | NFC服务所提供的Tag数据对象。 |

**示例：**

```js
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

let tagInfo : TagInfo = tag.getIsoDep(tagInfo).getTagInfo();
console.info("tag tagInfo: " + tagInfo);
```

### connectTag<sup>(deprecated)</sup>

connectTag(): boolean;

和标签建立连接。在从标签读取数据或将数据写入标签之前，必须调用此方法。

> **说明：**
> 从 API version 7 开始支持，从 API version 9 开始废弃，建议使用[tagSession.connect](#connect9)替代。

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| **类型** | **说明**                             |
| ------------------ | --------------------------|
| boolean  | 连接建立成功返回true，失败返回false。 |

**示例：**

```js
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

let connectStatus : boolean = tag.getIsoDep(tagInfo).connectTag();
console.info("connectStatus: " + connectStatus);
```

### connect<sup>9+</sup>

connect(): void;

和标签建立连接。在从标签读取数据或将数据写入标签之前，必须调用此方法。

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**错误码：**

以下错误码的详细介绍请参见[NFC错误码](errorcode-nfc.md)。

| 错误码ID | 错误信息|
| ------- | -------|
|201 | Permission denied.                 |
|801 | Capability not supported.          |
| 3100201 | The tag running state is abnormal in the service. |

**示例：**

```js
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

### reset()<sup>(deprecated)</sup>

reset(): void

重置与标签的连接。

> **说明：**
> 从 API version 7 开始支持，从 API version 9 开始废弃，建议使用[tagSession.resetConnection](#resetconnection9)替代。

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**示例：**

```js
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

tag.getIsoDep(tagInfo).reset(); 
```

### resetConnection()<sup>9+</sup>

resetConnection(): void

重置与标签的连接。

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**错误码：**

以下错误码的详细介绍请参见[NFC错误码](errorcode-nfc.md)。

| 错误码ID | 错误信息|
| ------- | -------|
|201 | Permission denied.                 |
|801 | Capability not supported.          |
| 3100201 | The tag running state is abnormal in the service. |

**示例：**

```js
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

### isTagConnected<sup>(deprecated)</sup>

isTagConnected(): boolean

检查是否已与标签建立连接。

> **说明：**
> 从 API version 7 开始支持，从 API version 9 开始废弃，建议使用[tagSession.isConnected](#isconnected9)替代。

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| **类型** | **说明**                             |
| ------------------ | --------------------------|
| boolean  | 已建立连接返回 true，未建立连接返回false。 |

**示例：**

```js
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

let isTagConnected = tag.getIsoDep(tagInfo).isTagConnected(); 
console.info("isTagConnected: " + isTagConnected);
```

### isConnected<sup>9+</sup>

isConnected(): boolean

检查是否已与标签建立连接。如果返回未连接，则需要先调用[tagSession.connect](#connect9)建立连接。

**系统能力：** SystemCapability.Communication.NFC.Tag

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**返回值：**

| **类型** | **说明**                             |
| ------------------ | --------------------------|
| boolean  | 已建立连接返回 true，未建立连接返回false。 |

**错误码：**

以下错误码的详细介绍请参见[NFC错误码](errorcode-nfc.md)。

| 错误码ID | 错误信息|
| ------- | -------|
|801 | Capability not supported.          |


**示例：**

```js
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

### getMaxSendLength<sup>(deprecated)</sup>

getMaxSendLength(): number

查询可以发送到标签的最大数据长度。

> **说明：**
> 从 API version 7 开始支持，从 API version 9 开始废弃，建议使用[tagSession.getMaxTransmitSize](#getmaxtransmitsize9)替代。

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| **类型** | **说明**                             |
| ------------------ | --------------------------|
| number  | 可以发送到标签的最大数据长度，非负数。 |

**示例：**
```js
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

let maxSendLen = tag.getIsoDep(tagInfo).getMaxSendLength(); 
console.info("tag maxSendLen: " + maxSendLen);
```

### getMaxTransmitSize<sup>9+</sup>

getMaxTransmitSize(): number

查询可以发送到标签的最大数据长度。

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**返回值：**

| **类型** | **说明**                             |
| ------------------ | --------------------------|
| number  | 可以发送到标签的最大数据长度，非负数。 |

**错误码：**

以下错误码的详细介绍请参见[NFC错误码](errorcode-nfc.md)。

| 错误码ID | 错误信息|
| ------- | -------|
|201 | Permission denied.                 |
|801 | Capability not supported.          |
| 3100201 | The tag running state is abnormal in the service. |

**示例：**
```js
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

### getSendDataTimeout<sup>(deprecated)</sup>

getSendDataTimeout(): number

查询发送数据到Tag的等待超时时间，单位是毫秒。

> **说明：**
> 从 API version 7 开始支持，从 API version 9 开始废弃，建议使用[tagSession.getTimeout](#gettimeout9)替代。

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**返回值：**

| **类型** | **说明**                             |
| ------------------ | --------------------------|
| number  | 发送数据到Tag的等待超时时间，单位是毫秒，非负数。 |

**示例：**

```js
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

let sendDataTimeout = tag.getIsoDep(tagInfo).getSendDataTimeout(); 
console.info("tag sendDataTimeout: " + sendDataTimeout);
```

### getTimeout<sup>9+</sup>

getTimeout(): number

查询发送数据到Tag的等待超时时间，单位是毫秒。

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**返回值：**

| **类型** | **说明**                             |
| ------------------ | --------------------------|
| number  | 发送数据到Tag的等待超时时间，单位是毫秒，非负数。 |

**错误码：**

以下错误码的详细介绍请参见[NFC错误码](errorcode-nfc.md)。

| 错误码ID | 错误信息|
| ------- | -------|
|201 | Permission denied.                 |
|801 | Capability not supported.          |
| 3100201 | The tag running state is abnormal in the service. |

**示例：**

```js
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

### setSendDataTimeout<sup>(deprecated)</sup>

setSendDataTimeout(timeout: number): boolean

设置发送数据到Tag的等待超时时间，单位是毫秒。

> **说明：**
> 从 API version 7 开始支持，从 API version 9 开始废弃，建议使用[tagSession.setTimeout](#settimeout9)替代。

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                   |
| -------- | ----------------------- | ---- | -------------------------------------- |
| timeout | number | 是 | 超时时间，单位毫秒，非负值。 |

**返回值：**

| **类型** | **说明**                             |
| ------------------ | --------------------------|
| boolean  | 设置超时时间成功返回true，设置失败返回false。 |

**示例：**

```js
import { tag } from '@kit.ConnectivityKit';

// 参考 @ohos.nfc.tag（标准NFC-Tag）中 tag.TagInfo 接口，tagInfo是nfc服务在分派标签时给出的对象
// getXXX，可以是getIsoDep、getNdef、getMifareClassic...

let timeoutMs = 700;  // 修改为预期的超时时间
let setStatus = tag.getIsoDep(tagInfo).setSendDataTimeout(timeoutMs); 
console.info("tag setSendDataTimeout setStatus: " + setStatus);
```

### setTimeout<sup>9+</sup>

setTimeout(timeout: number): void

设置发送数据到Tag的等待超时时间，单位是毫秒。

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                   |
| -------- | ----------------------- | ---- | -------------------------------------- |
| timeout | number | 是 | 超时时间，单位毫秒，非负值。 |

**错误码：**

以下错误码的详细介绍请参见[NFC错误码](errorcode-nfc.md)。

| 错误码ID | 错误信息|
| ------- | -------|
|201 | Permission denied.                 |
|401 | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
|801 | Capability not supported.          |
| 3100201 | The tag running state is abnormal in the service. |

**示例：**

```js
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

### sendData<sup>(deprecated)</sup>

sendData(data: number[]): Promise<number[]>

发送指令到Tag上，使用Promise方式作为异步方法。

> **说明：**
> 从 API version 7 开始支持，从 API version 9 开始废弃，建议使用[tagSession.transmit](#transmit9)替代。

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                   |
| -------- | ----------------------- | ---- | -------------------------------------- |
| data | number[] | 是 | 要发送的指令。每个number十六进制表示，范围是0x00~0xFF。 |

**返回值：**

| **类型** | **说明**                             |
| ------------------ | --------------------------|
| Promise<number[]> | 对端Tag对指令的响应数据。每个number十六进制表示，范围是0x00~0xFF。|

**示例：**

```js
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

### sendData<sup>(deprecated)</sup>

sendData(data: number[], callback: AsyncCallback<number[]>): void

发送指令到Tag上，使用AsyncCallback方式作为异步方法。

> **说明：**
> 从 API version 7 开始支持，从 API version 9 开始废弃，建议使用[tagSession.transmit](#transmit9-1)替代。

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                   |
| -------- | ----------------------- | ---- | -------------------------------------- |
| data | number[] | 是 | 要发送的指令。每个number十六进制表示，范围是0x00~0xFF。 |
| callback | AsyncCallback<number[]> | 是 | 回调函数，返回响应数据。每个number十六进制表示，范围是0x00~0xFF。 |

**示例：**

```js
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

### transmit<sup>9+</sup>

transmit(data: number[]): Promise<number[]>

发送指令到Tag上，使用Promise方式作为异步方法。

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                   |
| -------- | ----------------------- | ---- | -------------------------------------- |
| data | number[] | 是 | 要发送的指令。每个number十六进制表示，范围是0x00~0xFF。 |

**返回值：**

| **类型** | **说明**                             |
| ------------------ | --------------------------|
| Promise<number[]> | 对端Tag对指令的响应数据。每个number十六进制表示，范围是0x00~0xFF。|

**错误码：**

以下错误码的详细介绍请参见[NFC错误码](errorcode-nfc.md)。

| 错误码ID | 错误信息|
| ------- | -------|
|201 | Permission denied.                 |
|401 | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
|801 | Capability not supported.          |
| 3100201 | The tag running state is abnormal in the service. |
| 3100204 | The tag I/O operation failed. |

**示例：**

```js
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

### transmit<sup>9+</sup>

transmit(data: number[], callback: AsyncCallback<number[]>): void

发送指令到Tag上，使用AsyncCallback方式作为异步方法。

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.NFC.Tag

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                   |
| -------- | ----------------------- | ---- | -------------------------------------- |
| data | number[] | 是 | 要发送的指令。每个number十六进制表示，范围是0x00~0xFF。 |
| callback | AsyncCallback<number[]> | 是 | 回调函数，返回响应数据。每个number十六进制表示，范围是0x00~0xFF。 |

**错误码：**

以下错误码的详细介绍请参见[NFC错误码](errorcode-nfc.md)。

| 错误码ID | 错误信息|
| ------- | -------|
|201 | Permission denied.                 |
|401 | The parameter check failed. Possible causes: <br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameters types.<br>3. Parameter verification failed. |
|801 | Capability not supported.          |
| 3100201 | The tag running state is abnormal in the service. |
| 3100204 | The tag I/O operation failed.. |

**示例：**

```js
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
