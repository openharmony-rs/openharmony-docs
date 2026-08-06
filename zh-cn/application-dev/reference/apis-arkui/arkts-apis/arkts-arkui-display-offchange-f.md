# offChange

## offChange

```TypeScript
function offChange(callback?: Callback<long>): void
```

Unregister the callback for display changes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-display-function offChange(callback?: Callback<long>): void--><!--Device-display-function offChange(callback?: Callback<long>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;long&gt; | 否 | Unregister the callback function.If not provided, all callbacks for the given event type will be removed. |

**示例：**

```TypeScript
// 如果通过on注册多个callback，同时关闭所有callback监听
display.offChange();

let callback: Callback<long> = (data: long) => {
  console.info(`Succeeded in unregistering the callback for display Change. Data: ${data}`)
};
// 关闭传入的callback监听
display.offChange(callback);
```

