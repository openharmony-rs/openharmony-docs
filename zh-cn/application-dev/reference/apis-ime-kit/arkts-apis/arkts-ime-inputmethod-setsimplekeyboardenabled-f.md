# setSimpleKeyboardEnabled

## setSimpleKeyboardEnabled

```TypeScript
function setSimpleKeyboardEnabled(enable: boolean): void
```

编辑框应用设置简单键盘标志。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-inputMethod-function setSimpleKeyboardEnabled(enable: boolean): void--><!--Device-inputMethod-function setSimpleKeyboardEnabled(enable: boolean): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 简单键盘是否使能标志，true标识简单键盘使能，false标识简单键盘去使能。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 原生编辑框组件在下一次点击获焦时生效；自绘控件在下一次调用[attach]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_绑定输入法时生效。 |

**示例：**

```TypeScript
let enable: boolean = false;
  inputMethod.setSimpleKeyboardEnabled(enable);
```

