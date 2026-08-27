# readNdefTag

## 导入模块

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
```

## readNdefTag

```TypeScript
function readNdefTag(): Promise<string>
```

读取有源标签内容。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [read](arkts-connectivity-connectedtag-read-f.md)

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.ConnectedTag

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;string & gt; | Promise对象，返回读取有源标签内容的列表。 |

**示例**

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

connectedTag.readNdefTag().then((data) => {
    console.info("connectedTag readNdefTag Promise data = " + data);
}).catch((err: BusinessError)=> {
    console.error("connectedTag readNdefTag Promise err: " + err);
});
```


## readNdefTag

```TypeScript
function readNdefTag(callback: AsyncCallback<string>): void
```

读取有源标签内容，使用AsyncCallback方式作为异步方法。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [read](arkts-connectivity-connectedtag-read-f.md)

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.ConnectedTag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。当读取成功时data为读取到有源标签的内容；否则为err错误对象。 |

**示例**

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';

connectedTag.readNdefTag((err, data)=> {
    if (err) {
        console.error("connectedTag readNdefTag AsyncCallback err: " + err);
    } else {
        console.info("connectedTag readNdefTag AsyncCallback data: " + data);
    }
});
```
