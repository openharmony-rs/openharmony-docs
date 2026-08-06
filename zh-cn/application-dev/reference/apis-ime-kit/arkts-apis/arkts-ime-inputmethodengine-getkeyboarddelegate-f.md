# getKeyboardDelegate

## getKeyboardDelegate

```TypeScript
function getKeyboardDelegate(): KeyboardDelegate
```

获取客户端编辑事件监听代理实例[KeyboardDelegate]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_（键盘代理对象）。 输入法应用获取该实例后，可订阅物理键盘按键事件、选中文本变化事件等。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

<!--Device-inputMethodEngine-function getKeyboardDelegate(): KeyboardDelegate--><!--Device-inputMethodEngine-function getKeyboardDelegate(): KeyboardDelegate-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 客户端编辑事件监听代理。 |

**示例：**

```TypeScript
// 获取客户端编辑事件监听代理实例
let KeyboardDelegate: inputMethodEngine.KeyboardDelegate = inputMethodEngine.getKeyboardDelegate();
```


## getKeyboardDelegate

```TypeScript
function getKeyboardDelegate(): KeyboardDelegate | null
```

获取客户端编辑事件监听代理实例[KeyboardDelegate]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_（键盘代理对象）。 输入法应用获取该实例后，可订阅物理键盘按键事件、选中文本变化事件等。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-inputMethodEngine-function getKeyboardDelegate(): KeyboardDelegate | null--><!--Device-inputMethodEngine-function getKeyboardDelegate(): KeyboardDelegate | null-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 客户端编辑事件监听代理。 |

