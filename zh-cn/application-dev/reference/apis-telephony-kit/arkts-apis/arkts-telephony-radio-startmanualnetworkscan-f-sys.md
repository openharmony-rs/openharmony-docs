# startManualNetworkScan（系统接口）

## 导入模块

```TypeScript
```

## startManualNetworkScan

```TypeScript
function startManualNetworkScan(slotId: number, callback: Callback<NetworkSearchRealTimeResult>): void
```

启动手动网络扫描，实时报告

**起始版本：** 23

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;NetworkSearchRealTimeResult&gt; | 是 | Indicates the callback for manual network scan |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Nonsystem applications use system APIs. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
radio.startManualNetworkScan(0, (err: BusinessError, data: radio.NetworkSearchRealTimeResult) => {
    if (err) {
        console.error(`startManualNetworkScan failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`startManualNetworkScan success, callback: data->${JSON.stringify(data)}`);
});
```
