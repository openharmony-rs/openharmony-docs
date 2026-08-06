# getSetting

## getSetting

```TypeScript
function getSetting(): InputMethodSetting
```

获取客户端设置实例[InputMethodSetting]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 **含义/功能**：获取输入法设置实例，用于查询输入法列表、订阅输入法变化事件、查询面板可见性等配置管理操作。 **使用场景：**当应用需要查询已安装/已激活输入法列表、订阅输入法切换事件、或显示输入法选择对话框时，必须先通过此接口获取InputMethodSetting实例。 **使用后效果**：返回一个InputMethodSetting实例，后续可通过该实例调用getInputMethods、listInputMethodSubtype、on('imeChange')等接口。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-inputMethod-function getSetting(): InputMethodSetting--><!--Device-inputMethod-function getSetting(): InputMethodSetting-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回当前客户端设置实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800007](../errorcode-inputmethod-framework.md#12800007-输入法设置器异常) | input method setter error. Possible cause:create InputMethodSetting object failed. |

**示例：**

```TypeScript
let inputMethodSetting: inputMethod.InputMethodSetting = inputMethod.getSetting();
```

