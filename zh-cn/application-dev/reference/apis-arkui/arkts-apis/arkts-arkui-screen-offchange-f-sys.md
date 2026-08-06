# offChange（系统接口）

## offChange

```TypeScript
function offChange(callback?: Callback<long>): void
```

Unregister the callback for screen changes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-screen-function offChange(callback?: Callback<long>): void--><!--Device-screen-function offChange(callback?: Callback<long>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;long&gt; | 否 | Unregister the callback function.If not provided, all callbacks for the given event type will be removed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例：**

```TypeScript
let callback: Callback<long> = (data: long) => {
  console.info(`Succeeded in unregistering the callback for screen changes. Data: ${data}`)
};
screen.offChange(callback);
screen.offChange();
```

