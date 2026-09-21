# off

## 导入模块

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
```

## off("notify")

```TypeScript
function off(type: "notify", callback?:Callback<number>): void
```

取消NFC场强状态事件的注册。

**起始版本：** 8

**需要权限：** ohos.permission.NFC_TAG

**系统能力：** SystemCapability.Communication.ConnectedTag

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | "notify" | 是 | 固定填"notify"字符串。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 否 | 状态改变回调函数。如果callback不填，将“去注册”该事件关联的所有回调函数。 |

**示例**

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';

function nfcStatusCb(rfState: connectedTag.NfcRfType) {
    console.info("connectedTag on Callback rfState: ", rfState);
}

// 有源NFC标签的使用流程
async function nfcTagTestOn(): Promise<void> {
    try {
        console.info("connectedTag initialize");
        connectedTag.initialize();
    } catch (error) {
        console.error("initialize error:" + error);
    }
    // 注册回调以接收nfc进离场状态更改通知
    connectedTag.on("notify", nfcStatusCb);
    try {
        let tag = [3, 1, 0];
        console.info("connectedTag write: tag=" + tag);
        await connectedTag.write(tag);
        let data = await connectedTag.read();
        console.info("connectedTag read: data=" + data);
    } catch (error) {
        console.error("connectedTag error: " + error);
    }
}

// 业务退出时，取消注册回调、取消初始化
async function nfcTagTestOff(): Promise<void> {
    // 取消注册回调
    connectedTag.off("notify", nfcStatusCb);
    try {
        console.info("connectedTag uninitialize");
        connectedTag.uninitialize();
    } catch (error) {
        console.error("connectedTag error: " + error);
    }
}
```
