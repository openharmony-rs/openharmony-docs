# DisplayOrientation

标识该Ability的显示模式。仅适用于FA模型的[PageAbility](../../../application-models/pageability-overview.md)。

<!--Table: 40%; 10%; 50%-->

**起始版本：** 9

<!--Device-bundleManager-export enum DisplayOrientation--><!--Device-bundleManager-export enum DisplayOrientation-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## UNSPECIFIED

```TypeScript
UNSPECIFIED = 0
```

表示未定义方向模式，由系统判定。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayOrientation-UNSPECIFIED = 0--><!--Device-DisplayOrientation-UNSPECIFIED = 0-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## LANDSCAPE

```TypeScript
LANDSCAPE = 1
```

表示横屏显示模式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayOrientation-LANDSCAPE = 1--><!--Device-DisplayOrientation-LANDSCAPE = 1-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## PORTRAIT

```TypeScript
PORTRAIT = 2
```

表示竖屏显示模式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayOrientation-PORTRAIT = 2--><!--Device-DisplayOrientation-PORTRAIT = 2-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## FOLLOW_RECENT

```TypeScript
FOLLOW_RECENT = 3
```

表示跟随上一个显示模式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayOrientation-FOLLOW_RECENT = 3--><!--Device-DisplayOrientation-FOLLOW_RECENT = 3-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## LANDSCAPE_INVERTED

```TypeScript
LANDSCAPE_INVERTED = 4
```

表示反向横屏显示模式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayOrientation-LANDSCAPE_INVERTED = 4--><!--Device-DisplayOrientation-LANDSCAPE_INVERTED = 4-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## PORTRAIT_INVERTED

```TypeScript
PORTRAIT_INVERTED = 5
```

表示反向竖屏显示模式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayOrientation-PORTRAIT_INVERTED = 5--><!--Device-DisplayOrientation-PORTRAIT_INVERTED = 5-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## AUTO_ROTATION

```TypeScript
AUTO_ROTATION = 6
```

表示传感器在旋转到横向和竖向时，页面会自动旋转。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayOrientation-AUTO_ROTATION = 6--><!--Device-DisplayOrientation-AUTO_ROTATION = 6-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## AUTO_ROTATION_LANDSCAPE

```TypeScript
AUTO_ROTATION_LANDSCAPE = 7
```

表示传感器在旋转到横向时，页面会自动旋转。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayOrientation-AUTO_ROTATION_LANDSCAPE = 7--><!--Device-DisplayOrientation-AUTO_ROTATION_LANDSCAPE = 7-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## AUTO_ROTATION_PORTRAIT

```TypeScript
AUTO_ROTATION_PORTRAIT = 8
```

表示传感器在旋转到竖向时，页面会自动旋转。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayOrientation-AUTO_ROTATION_PORTRAIT = 8--><!--Device-DisplayOrientation-AUTO_ROTATION_PORTRAIT = 8-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## AUTO_ROTATION_RESTRICTED

```TypeScript
AUTO_ROTATION_RESTRICTED = 9
```

表示受开关控制的自动旋转模式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayOrientation-AUTO_ROTATION_RESTRICTED = 9--><!--Device-DisplayOrientation-AUTO_ROTATION_RESTRICTED = 9-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## AUTO_ROTATION_LANDSCAPE_RESTRICTED

```TypeScript
AUTO_ROTATION_LANDSCAPE_RESTRICTED = 10
```

表示受开关控制的自动横向旋转模式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayOrientation-AUTO_ROTATION_LANDSCAPE_RESTRICTED = 10--><!--Device-DisplayOrientation-AUTO_ROTATION_LANDSCAPE_RESTRICTED = 10-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## AUTO_ROTATION_PORTRAIT_RESTRICTED

```TypeScript
AUTO_ROTATION_PORTRAIT_RESTRICTED = 11
```

表示受开关控制的自动竖向旋转模式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayOrientation-AUTO_ROTATION_PORTRAIT_RESTRICTED = 11--><!--Device-DisplayOrientation-AUTO_ROTATION_PORTRAIT_RESTRICTED = 11-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## LOCKED

```TypeScript
LOCKED = 12
```

表示锁定模式。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayOrientation-LOCKED = 12--><!--Device-DisplayOrientation-LOCKED = 12-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## AUTO_ROTATION_UNSPECIFIED

```TypeScript
AUTO_ROTATION_UNSPECIFIED = 13
```

受开关控制和由系统判定的自动旋转模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayOrientation-AUTO_ROTATION_UNSPECIFIED = 13--><!--Device-DisplayOrientation-AUTO_ROTATION_UNSPECIFIED = 13-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## FOLLOW_DESKTOP

```TypeScript
FOLLOW_DESKTOP = 14
```

跟随桌面的旋转模式。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DisplayOrientation-FOLLOW_DESKTOP = 14--><!--Device-DisplayOrientation-FOLLOW_DESKTOP = 14-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

