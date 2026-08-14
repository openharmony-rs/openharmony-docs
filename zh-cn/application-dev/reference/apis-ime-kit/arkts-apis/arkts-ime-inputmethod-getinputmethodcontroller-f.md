# getInputMethodController

## getInputMethodController

```TypeScript
function getInputMethodController(): InputMethodController
```

获取客户端实例[InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i.md#InputMethodController)。

**起始版本：** 6

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为6。

**废弃版本：** 9

**替代接口：** [getController](arkts-ime-inputmethod-getcontroller-f.md#getController)

<!--Device-inputMethod-function getInputMethodController(): InputMethodController--><!--Device-inputMethod-function getInputMethodController(): InputMethodController-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [InputMethodController](arkts-ime-inputmethod-inputmethodcontroller-i.md) | 回调返回当前客户端实例。 |

## 示例

```TypeScript
let inputMethodController: inputMethod.InputMethodController = inputMethod.getInputMethodController();
```

