# getInputMethodEngine

## getInputMethodEngine

```TypeScript
function getInputMethodEngine(): InputMethodEngine
```

获取输入法应用客户端实例[InputMethodEngine]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_（输入法引擎）。 输入法应用获取该实例后，可订阅软键盘显示/隐藏请求事件等。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [inputMethodEngine.getInputMethodAbility](arkts-ime-inputmethodengine-getinputmethodability-f.md#getinputmethodability)()

<!--Device-inputMethodEngine-function getInputMethodEngine(): InputMethodEngine--><!--Device-inputMethodEngine-function getInputMethodEngine(): InputMethodEngine-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 输入法应用客户端。 |

**示例：**

```TypeScript
// 获取输入法应用客户端实例（已废弃）
let InputMethodEngine: inputMethodEngine.InputMethodEngine = inputMethodEngine.getInputMethodEngine();
```

