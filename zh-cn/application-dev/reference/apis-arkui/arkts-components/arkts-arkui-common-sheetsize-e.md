# SheetSize

指定半模态的高度。

**起始版本：** 10

<!--Device-unnamed-declare enum SheetSize--><!--Device-unnamed-declare enum SheetSize-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MEDIUM

```TypeScript
MEDIUM = 0
```

指定半模态高度为半模态所在窗口的60%。

在TV设备上半模态高度为半模态所在窗口的50%。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SheetSize-MEDIUM = 0--><!--Device-SheetSize-MEDIUM = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LARGE

```TypeScript
LARGE = 1
```

指定半模态高度几乎为半模态所在窗口的高度。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SheetSize-LARGE = 1--><!--Device-SheetSize-LARGE = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FIT_CONTENT

```TypeScript
FIT_CONTENT = 2
```

指定半模态高度为适应内容的高度。

**说明：**

1. FIT_CONTENT是半模态容器高度去适应孩子builder根节点的布局。此场景下builder根节点的高度不能使用百分比，两者不能相互依赖彼此的布局。2. 如果半模态使用SheetSize.FIT_CONTENT自适应模式，且类型设置为居中弹窗或跟手弹窗，API version 22及之前版本，高度大于最大高度，则显示最大高度，高度小于最小高度，则显示最小高度。

API version 23开始，高度大于最大高度，则显示最大高度，高度小于最小高度，按照实际自适应高度生效。

其中居中弹窗和跟手弹窗最小高度为320vp，最大高度为窗口短边的90%。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SheetSize-FIT_CONTENT = 2--><!--Device-SheetSize-FIT_CONTENT = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

