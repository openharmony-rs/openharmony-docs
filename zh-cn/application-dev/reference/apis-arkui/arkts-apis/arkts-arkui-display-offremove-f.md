# offRemove

## offRemove

```TypeScript
function offRemove(callback?: Callback<long>): void
```

Unregister the callback for display remove events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-display-function offRemove(callback?: Callback<long>): void--><!--Device-display-function offRemove(callback?: Callback<long>): void-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;long&gt; | 否 | Unregister the callback function. If not provided, all callbacks for the given event type will be removed. |

## 示例

```TypeScript
// 如果通过on注册多个callback，同时关闭所有callback监听
display.offRemove();

let callback: Callback<long> = (data: long) => {
  console.info(`Succeeded in unregistering the callback for display remove. Data: ${data}`)
};
// 关闭传入的callback监听
display.offRemove(callback);
```

