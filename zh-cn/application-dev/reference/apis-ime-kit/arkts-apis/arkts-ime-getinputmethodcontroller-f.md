# getInputMethodController

## getInputMethodController

```TypeScript
function getInputMethodController(): InputMethodController
```

获取客户端实例[InputMethodController](arkts-ime-inputmethodcontroller-i.md)。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [getController](arkts-ime-getcontroller-f.md#getcontroller-1)

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| InputMethodController | 回调返回当前客户端实例。 |

**示例：**

```TypeScript
let inputMethodController: inputMethod.InputMethodController = inputMethod.getInputMethodController();

```

