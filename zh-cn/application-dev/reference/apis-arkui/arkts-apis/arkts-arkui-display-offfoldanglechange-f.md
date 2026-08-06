# offFoldAngleChange

## offFoldAngleChange

```TypeScript
function offFoldAngleChange(callback?: Callback<Array<double>>): void
```

Unregister the callback for fold angle changes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-display-function offFoldAngleChange(callback?: Callback<Array<double>>): void--><!--Device-display-function offFoldAngleChange(callback?: Callback<Array<double>>): void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;double&gt;&gt; | 否 | Unregister the callback function.If not provided, all callbacks for the given event type will be removed. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-系统服务工作异常) | This display manager service works abnormally. |

**示例：**

```TypeScript
// 如果通过on注册多个callback，同时关闭所有callback监听
display.offFoldAngleChange();

let callback: Callback<Array<double>> = (angles: Array<double>) => {
  console.info(`Listening fold angles length: ${angles.length}`);
};
// 关闭传入的callback监听
display.offFoldAngleChange(callback);
```

