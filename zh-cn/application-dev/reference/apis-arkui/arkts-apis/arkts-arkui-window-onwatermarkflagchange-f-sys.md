# onWaterMarkFlagChange（系统接口）

## onWaterMarkFlagChange

```TypeScript
function onWaterMarkFlagChange(callback: Callback<boolean>): void
```

添加水印启用状态变化的监听。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-window-function onWaterMarkFlagChange(callback: Callback<boolean>): void--><!--Device-window-function onWaterMarkFlagChange(callback: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-window-callback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回当前水印的启用状态。true表示当前已启用水印；false表示当前未启用水印。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

```TypeScript
try {
  window.onWaterMarkFlagChange((data) => {
    console.info(`Succeeded in enabling the listener for watermark flag changes. Data: ${data}`);
  });
} catch (exception) {
  let error = exception as BusinessError;
  console.error(`Failed to enable the listener for watermark flag changes. Cause code: ${error.code}, message: ${error.message}`);
}
```

