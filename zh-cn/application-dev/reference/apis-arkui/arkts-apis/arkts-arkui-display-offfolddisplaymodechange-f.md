# offFoldDisplayModeChange

## offFoldDisplayModeChange

```TypeScript
function offFoldDisplayModeChange(callback?: Callback<FoldDisplayMode>): void
```

Unregister the callback for fold display mode changes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-display-function offFoldDisplayModeChange(callback?: Callback<FoldDisplayMode>): void--><!--Device-display-function offFoldDisplayModeChange(callback?: Callback<FoldDisplayMode>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[FoldDisplayMode](arkts-arkui-display-folddisplaymode-e.md)&gt; | 否 | Unregister the callback function. If not provided, all callbacks for the given event type will be removed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

## 示例

```TypeScript
// 如果通过on注册多个callback，同时关闭所有callback监听
display.offFoldDisplayModeChange();

let callback: Callback<display.FoldDisplayMode> = (data: display.FoldDisplayMode) => {
  console.info(`unregistering FoldDisplayMode changes callback. Data: ${data}`);
};
// 关闭传入的callback监听
display.offFoldDisplayModeChange(callback);
```

