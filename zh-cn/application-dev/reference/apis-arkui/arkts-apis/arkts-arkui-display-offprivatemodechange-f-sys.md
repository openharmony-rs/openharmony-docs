# offPrivateModeChange（系统接口）

## offPrivateModeChange

```TypeScript
function offPrivateModeChange(callback?: Callback<boolean>): void
```

Unregister the callback for private mode changes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-display-function offPrivateModeChange(callback?: Callback<boolean>): void--><!--Device-display-function offPrivateModeChange(callback?: Callback<boolean>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt; | 否 | Unregister the callback function. If not provided, all callbacks for the given event type will be removed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

## 示例

```TypeScript
try {
  display.offPrivateModeChange(callback);
} catch (exception) {
  let error = exception as BusinessError;
  console.error(`Failed to unregister callback. Code: ${error.code} , message: ${error.message}`);
}
```

