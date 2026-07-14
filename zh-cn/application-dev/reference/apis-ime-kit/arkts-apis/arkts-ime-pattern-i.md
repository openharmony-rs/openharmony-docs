# Pattern

输入法模式选项的图标资源定义，用于配置键盘模式在弹窗中的视觉表现。仅当前输入法（即系统预置输入法）可使用。

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## icon

```TypeScript
icon: Resource
```

输入法模式选项的默认（未选中）状态图标资源。

**使用场景：** 用于标识每个键盘模式在未选中时的视觉表现形式，用户在弹窗中可据此识别不同的模式选项。

**使用后效果：** 设置后，弹窗中该模式选项在未选中状态时显示此图标。

**说明：** 需使用Resource类型资源引用（如$r('app.media.xxx')），确保工程resource目录中已添加对应的图标资源文件。不支持string和PixelMap类型的图片资源。

**类型：** Resource

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## selectedIcon

```TypeScript
selectedIcon: Resource
```

输入法模式选项的选中状态图标资源。

**使用场景：** 用于标识每个键盘模式在选中时的视觉表现形式，与icon形成选中/未选中的视觉区分，帮助用户识别当前选中的模式。

**使用后效果：** 设置后，弹窗中该模式选项在选中状态时显示此图标。

**相关参数间的配合/制约关系：** selectedIcon应与icon在视觉风格上保持一致，仅在选中状态标识上有所区别（如增加高亮、边框等），以便用户识别当前选中的模式。每个Pattern中的icon和selectedIcon
必须同时设置，缺一不可。

**类型：** Resource

**起始版本：** 11

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

