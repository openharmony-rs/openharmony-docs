# getController

## getController

```TypeScript
function getController(): InputMethodController
```

获取客户端实例[InputMethodController]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 **含义/功能**：获取当前应用的输入法客户端控制器实例，用于后续与输入法进行交互（绑定、显示/隐藏键盘、同步编辑框状态等）。 **使用场景：**当前台应用（如备忘录、聊天应用）需要控制输入法的显示/隐藏、绑定/解绑、同步编辑框信息时，必须先通过此接口获取InputMethodController实例。 **使用后效果**：返回一个InputMethodController实例，后续可通过该实例调用attach、showTextInput、hideTextInput、detach等一系列接口与输入法交互。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-inputMethod-function getController(): InputMethodController--><!--Device-inputMethod-function getController(): InputMethodController-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回当前客户端实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800006](../errorcode-inputmethod-framework.md#12800006-输入法控制器异常) | input method controller error. Possible cause:create InputMethodController object failed. |

**示例：**

```TypeScript
let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
```

