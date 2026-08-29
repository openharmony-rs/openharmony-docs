# read

## 导入模块

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
```

## read

```TypeScript
function read(): Promise<number[]>
```

读取有源标签内容。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.ConnectedTag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number[]&gt; | Promise对象，返回读取有源标签内容的列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3200101](../errorcode-nfc.md#3200101-有源nfc标签状态异常) | Connected NFC tag running state is abnormal in service. |

**示例**

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

connectedTag.read().then((data) => {
    console.info("connectedTag read Promise data = " + data);
}).catch((err: BusinessError)=> {
    console.error("connectedTag read Promise err: " + err);
});
```


## read

```TypeScript
function read(callback: AsyncCallback<number[]>): void
```

读取有源标签内容，使用AsyncCallback方式作为异步方法。

**起始版本：** 9

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.ConnectedTag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number[]&gt; | 是 | 回调函数。当读取成功时data为读取到有源标签的内容；否则为err错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [3200101](../errorcode-nfc.md#3200101-有源nfc标签状态异常) | Connected NFC tag running state is abnormal in service. |

**示例**

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';

connectedTag.read((err, data)=> {
    if (err) {
        console.error("connectedTag read AsyncCallback err: " + err);
    } else {
        console.info("connectedTag read AsyncCallback data: " + data);
    }
});
```
