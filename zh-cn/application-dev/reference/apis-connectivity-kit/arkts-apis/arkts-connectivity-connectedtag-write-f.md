# write

## 导入模块

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
```

## write

```TypeScript
function write(data: number[]): Promise<void>
```

写入内容到有源标签。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.ConnectedTag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | number[] | 是 | 有源标签内容, 由十六进制数字组成。范围：0x00至0xFF。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3200101](../errorcode-nfc.md#3200101-有源nfc标签状态异常) | Connected NFC tag running state is abnormal in service. |

**示例**

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rawData = [0x01, 0x02, 0x03]; // change it to be correct.
connectedTag.write(rawData).then(() => {
    console.info("connectedTag.write Promise success.");
}).catch((err: BusinessError)=> {
    console.error("connectedTag.write Promise err: " + err);
});
```


## write

```TypeScript
function write(data: number[], callback: AsyncCallback<void>): void
```

写入内容到有源标签，使用AsyncCallback方式作为异步方法。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.ConnectedTag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | number[] | 是 | 有源标签内容, 由十六进制数字组成。范围：0x00至0xFF。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当写入标签成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3200101](../errorcode-nfc.md#3200101-有源nfc标签状态异常) | Connected NFC tag running state is abnormal in service. |

**示例**

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';

let rawData = [0x01, 0x02, 0x03]; // change it to be correct.
connectedTag.write(rawData, (err)=> {
    if (err) {
        console.error("connectedTag.write AsyncCallback err: " + err);
    } else {
        console.info("connectedTag.write AsyncCallback success.");
    }
});
```
