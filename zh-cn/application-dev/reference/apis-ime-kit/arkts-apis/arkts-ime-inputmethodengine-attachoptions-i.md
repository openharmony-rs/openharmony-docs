# AttachOptions

绑定输入法时的附加选项。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-inputMethodEngine-export interface AttachOptions--><!--Device-inputMethodEngine-export interface AttachOptions-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## isSimpleKeyboardEnabled

```TypeScript
isSimpleKeyboardEnabled?: boolean
```

是否使能简单键盘，该属性由编辑框应用设置，true表示使能简单键盘，false表示不使能简单键盘。 如果没有设置或设置非法值，则默认不使能简单键盘。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AttachOptions-isSimpleKeyboardEnabled?: boolean--><!--Device-AttachOptions-isSimpleKeyboardEnabled?: boolean-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## requestKeyboardReason

```TypeScript
requestKeyboardReason?: RequestKeyboardReason
```

该属性由编辑框应用设置，如果没有设置或设置非法值，则默认没有特定的原因触发键盘请求。

**类型：** RequestKeyboardReason

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AttachOptions-requestKeyboardReason?: RequestKeyboardReason--><!--Device-AttachOptions-requestKeyboardReason?: RequestKeyboardReason-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

