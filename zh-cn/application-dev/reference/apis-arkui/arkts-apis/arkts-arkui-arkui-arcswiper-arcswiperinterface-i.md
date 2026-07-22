# ArcSwiperInterface

Provide an interface for ArcSwiper.

**起始版本：** 18

<!--Device-unnamed-interface ArcSwiperInterface--><!--Device-unnamed-interface ArcSwiperInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcSwiperAttribute, ArcSwiper, ArcDirection, ArcSwiperController, ArcDotIndicator } from '@kit.ArkUI';
```

## constructor

```TypeScript
(controller?: ArcSwiperController): ArcSwiperAttribute
```

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperInterface-(controller?: ArcSwiperController): ArcSwiperAttribute--><!--Device-ArcSwiperInterface-(controller?: ArcSwiperController): ArcSwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | [ArcSwiperController](arkts-arkui-arkui-arcswiper-arcswipercontroller-c.md) | 否 | Controller bound to the component to control the page turning. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcSwiperAttribute](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md) | @syscap SystemCapability.ArkUI.ArkUI.Circle@crossplatform@atomicservice |

