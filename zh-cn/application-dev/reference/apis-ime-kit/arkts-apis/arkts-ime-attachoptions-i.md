# AttachOptions

绑定输入法时的附加选项。

**起始版本：** 19

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## isSimpleKeyboardEnabled

```TypeScript
isSimpleKeyboardEnabled?: boolean
```

是否使能简单键盘，该属性由编辑框应用设置，true表示使能简单键盘，false表示不使能简单键盘。

如果没有设置或设置非法值，则默认不使能简单键盘。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## requestKeyboardReason

```TypeScript
requestKeyboardReason?: RequestKeyboardReason
```

该属性由编辑框应用设置，如果没有设置或设置非法值，则默认没有特定的原因触发键盘请求。

**类型：** RequestKeyboardReason

**起始版本：** 19

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

