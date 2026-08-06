# offWaterMarkFlagChange（系统接口）

## offWaterMarkFlagChange

```TypeScript
function offWaterMarkFlagChange(callback?: Callback<boolean>): void
```

移除水印启用状态变化的监听。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-window-function offWaterMarkFlagChange(callback?: Callback<boolean>): void--><!--Device-window-function offWaterMarkFlagChange(callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;boolean&gt; | 否 | 已注册的回调函数。如果传入参数，则关闭该监听。如果未传入参数，则关闭所有水印启用状态变化的监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [1300002](../errorcode-window.md#1300002-窗口状态异常) | This window state is abnormal. |
| [1300003](../errorcode-window.md#1300003-系统服务工作异常) | This window manager service works abnormally. |

**示例：**

```TypeScript
const callback = (bool: boolean) => {
  // ...
}
try {
  window.onWaterMarkFlagChange(callback);
  window.offWaterMarkFlagChange(callback);
  // 如果通过on开启多个callback进行监听，同时关闭所有监听：
  window.offWaterMarkFlagChange();
} catch (exception) {
  let error = exception as BusinessError;
  console.error(`Failed to enable or disable the listener for watermark flag changes. Cause code: ${error.code}, message: ${error.message}`);
}
```

