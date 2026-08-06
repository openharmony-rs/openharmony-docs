# on（系统接口）

## on('drag')

```TypeScript
function on(type: 'drag', callback: Callback<DragState>): void
```

注册监听拖拽状态。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-dragInteraction-function on(type: 'drag', callback: Callback<DragState>): void--><!--Device-dragInteraction-function on(type: 'drag', callback: Callback<DragState>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Drag

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'drag' | 是 | 监听类型，固定取值为 'drag'。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;DragState&gt; | 是 | 回调函数，异步返回拖拽状态消息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Incorrect parameter types.3.Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

**示例：**

```TypeScript
try {
  dragInteraction.on('drag', (data: dragInteraction.DragState) => {
    console.info(`Drag interaction event: ${data}`);
  });
} catch (error) {
  console.error(`Register failed, code: ${error.code}, message: ${error.message}`);
}
```

