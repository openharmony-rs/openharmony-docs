# DismissReason

关闭原因类型。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PRESS_BACK

```TypeScript
PRESS_BACK = 0
```

点击三键back、侧滑（左滑/右滑）、键盘ESC。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TOUCH_OUTSIDE

```TypeScript
TOUCH_OUTSIDE = 1
```

点击遮障层时。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CLOSE_BUTTON

```TypeScript
CLOSE_BUTTON = 2
```

点击关闭按钮。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SLIDE_DOWN

```TypeScript
SLIDE_DOWN = 3
```

下拉关闭。

**说明：**

该接口仅支持在[半模态转场](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)中使用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SLIDE

```TypeScript
SLIDE = 4
```

滑动交互，不是向下滑动。
默认表示向右滑动，镜像操作后表示向左滑动。
不支持选择向左或向右滑动。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

