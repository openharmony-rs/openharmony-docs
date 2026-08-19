# CollectStrategy（系统接口）

页面信息收集策略。

**起始版本：** 23

<!--Device-onScreen-export enum CollectStrategy--><!--Device-onScreen-export enum CollectStrategy-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## ALLOW

```TypeScript
ALLOW = 1 << 0
```

应用支持采集。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CollectStrategy-ALLOW = 1 << 0--><!--Device-CollectStrategy-ALLOW = 1 << 0-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## SPLIT_SCREEN

```TypeScript
SPLIT_SCREEN = 1 << 1
```

应用分屏窗口采集策略。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CollectStrategy-SPLIT_SCREEN = 1 << 1--><!--Device-CollectStrategy-SPLIT_SCREEN = 1 << 1-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## UNSUPPORTED_APP

```TypeScript
UNSUPPORTED_APP = 1 << 2
```

应用不支持自动采集。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CollectStrategy-UNSUPPORTED_APP = 1 << 2--><!--Device-CollectStrategy-UNSUPPORTED_APP = 1 << 2-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## PRIVATE_WINDOW

```TypeScript
PRIVATE_WINDOW = 1 << 3
```

应用隐私窗口。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CollectStrategy-PRIVATE_WINDOW = 1 << 3--><!--Device-CollectStrategy-PRIVATE_WINDOW = 1 << 3-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## ANCO_APP

```TypeScript
ANCO_APP = 1 << 4
```

虚拟机应用，非鸿蒙应用。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CollectStrategy-ANCO_APP = 1 << 4--><!--Device-CollectStrategy-ANCO_APP = 1 << 4-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## ALLOW_USER_CHANGE

```TypeScript
ALLOW_USER_CHANGE = 1 << 5
```

应用的采集策略可配置。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CollectStrategy-ALLOW_USER_CHANGE = 1 << 5--><!--Device-CollectStrategy-ALLOW_USER_CHANGE = 1 << 5-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## BUSINESS_APP

```TypeScript
BUSINESS_APP = 1 << 6
```

应用数据可采集。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CollectStrategy-BUSINESS_APP = 1 << 6--><!--Device-CollectStrategy-BUSINESS_APP = 1 << 6-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## FLOAT_SCREEN

```TypeScript
FLOAT_SCREEN = 1 << 7
```

悬浮窗口。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CollectStrategy-FLOAT_SCREEN = 1 << 7--><!--Device-CollectStrategy-FLOAT_SCREEN = 1 << 7-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## PIP_SCREEN

```TypeScript
PIP_SCREEN = 1 << 8
```

画中画模式。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CollectStrategy-PIP_SCREEN = 1 << 8--><!--Device-CollectStrategy-PIP_SCREEN = 1 << 8-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## LAUNCHER

```TypeScript
LAUNCHER = 1 << 9
```

桌面应用。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CollectStrategy-LAUNCHER = 1 << 9--><!--Device-CollectStrategy-LAUNCHER = 1 << 9-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

