# writeNdefTag

## 导入模块

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
```

## writeNdefTag

```TypeScript
function writeNdefTag(data: string): Promise<void>
```

写入内容到有源标签。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [write](arkts-connectivity-connectedtag-write-f.md)

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.ConnectedTag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 | 有源标签内容, 最大长度为1024个字节。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**示例**

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let rawData = "010203"; // change it to be correct.
connectedTag.writeNdefTag(rawData).then(() => {
    console.info("connectedTag.writeNdefTag Promise success.");
}).catch((err: BusinessError)=> {
    console.error("connectedTag.writeNdefTag Promise err: " + err);
});
```


## writeNdefTag

```TypeScript
function writeNdefTag(data: string, callback: AsyncCallback<void>): void
```

写入内容到有源标签，使用AsyncCallback方式作为异步方法。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [write](arkts-connectivity-connectedtag-write-f.md)

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.ConnectedTag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 | 有源标签内容, 最大长度为1024个字节。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当写入标签成功，err为undefined，否则为错误对象。 |

**示例**

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';

let rawData = "010203"; // change it to be correct.
connectedTag.writeNdefTag(rawData, (err)=> {
    if (err) {
        console.error("connectedTag.writeNdefTag AsyncCallback err: " + err);
    } else {
        console.info("connectedTag.writeNdefTag AsyncCallback success.");
    }
});
```
