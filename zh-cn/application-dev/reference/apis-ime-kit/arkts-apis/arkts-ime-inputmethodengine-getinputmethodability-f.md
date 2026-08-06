# getInputMethodAbility

## getInputMethodAbility

```TypeScript
function getInputMethodAbility(): InputMethodAbility
```

获取输入法应用客户端实例[InputMethodAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_（输入法能力对象），仅支持输入法应用调用。 输入法应用获取该实例后，可订阅软键盘显示/隐藏请求事件、创建/销毁输入法面板等。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

<!--Device-inputMethodEngine-function getInputMethodAbility(): InputMethodAbility--><!--Device-inputMethodEngine-function getInputMethodAbility(): InputMethodAbility-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 输入法应用客户端。 |

**示例：**

```TypeScript
// 获取输入法应用客户端实例
let InputMethodAbility: inputMethodEngine.InputMethodAbility = inputMethodEngine.getInputMethodAbility();
```


## getInputMethodAbility

```TypeScript
function getInputMethodAbility(): InputMethodAbility | null
```

获取输入法应用客户端实例[InputMethodAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_（输入法能力对象），仅支持输入法应用调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-inputMethodEngine-function getInputMethodAbility(): InputMethodAbility | null--><!--Device-inputMethodEngine-function getInputMethodAbility(): InputMethodAbility | null-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 输入法应用客户端。 |

