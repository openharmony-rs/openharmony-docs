# SheetKeyboardAvoidMode

半模态激活输入法时对软键盘的避让方式。
> **说明：**  
>  
> 设置POPUP_SHEET避让方式时，半模态只避让由面板内的文本框组件拉起的软键盘场景，其他场景半模态无需避让。

**起始版本：** 13

<!--Device-unnamed-declare enum SheetKeyboardAvoidMode--><!--Device-unnamed-declare enum SheetKeyboardAvoidMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

设置半模态不避让软键盘。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-SheetKeyboardAvoidMode-NONE = 0--><!--Device-SheetKeyboardAvoidMode-NONE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TRANSLATE_AND_RESIZE

```TypeScript
TRANSLATE_AND_RESIZE = 1
```

设置半模态先上抬面板避让软键盘；

当上抬至最大高度仍不足以避让软键盘时，则通过压缩整体内容完成避让。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-SheetKeyboardAvoidMode-TRANSLATE_AND_RESIZE = 1--><!--Device-SheetKeyboardAvoidMode-TRANSLATE_AND_RESIZE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## RESIZE_ONLY

```TypeScript
RESIZE_ONLY = 2
```

设置半模态通过压缩整体内容避让软键盘。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-SheetKeyboardAvoidMode-RESIZE_ONLY = 2--><!--Device-SheetKeyboardAvoidMode-RESIZE_ONLY = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TRANSLATE_AND_SCROLL

```TypeScript
TRANSLATE_AND_SCROLL = 3
```

设置半模态先上抬面板避让软键盘；

当上抬至最大高度仍不足以避让软键盘时，则通过滚动内容完成避让。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-SheetKeyboardAvoidMode-TRANSLATE_AND_SCROLL = 3--><!--Device-SheetKeyboardAvoidMode-TRANSLATE_AND_SCROLL = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## POPUP_SHEET

```TypeScript
POPUP_SHEET = 4
```

设置半模态popup样式弹窗避让软键盘。

1. 避让软键盘时，在popup样式弹窗当前显示位置无法容纳弹窗尺寸的前提下，遵循先垂直翻转避让，后尝试90°水平旋转避让的规则调整显示位置，以预设方向为下方为例，调整避让顺序依次为：下、上、右、左。2. 如果设置的对齐方式导致组件布局超出窗口范围，将根据该对齐方式在水平或垂直方向上进行位移，直至组件完全显示在窗口内。3. 避让软键盘时，如果在四个方向上均无法容纳当前的popup样式弹窗，处理方式遵循开发者设置的placementOnTarget属性：

（1）若属性值为true，将依据设定的placement，向其镜像方向平移，直至弹窗能够完全显示。

（2）若属性值为false，则在四个方向中，选择能够完全展示弹窗宽度且剩余高度最大的方向，通过调整半模态高度以适应当前方向，确保弹窗能够放下，同时保持预设placement对应的对齐方式不变。

4. 若此时半模态不是跟手样式，则不具备避让软键盘能力。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-SheetKeyboardAvoidMode-POPUP_SHEET = 4--><!--Device-SheetKeyboardAvoidMode-POPUP_SHEET = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

