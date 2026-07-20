# ArcDotIndicator

提供弧形圆点指示器属性及功能。

**起始版本：** 18

<!--Device-unnamed-export class ArcDotIndicator--><!--Device-unnamed-export class ArcDotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcSwiperAttribute, ArcSwiper, ArcDirection, ArcSwiperController, ArcDotIndicator } from '@kit.ArkUI';
```

<a id="arcdirection"></a>
## arcDirection

```TypeScript
arcDirection(direction: Optional<ArcDirection>): ArcDotIndicator
```

设置弧形指示器的方向。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcDotIndicator-arcDirection(direction: Optional<ArcDirection>): ArcDotIndicator--><!--Device-ArcDotIndicator-arcDirection(direction: Optional<ArcDirection>): ArcDotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| direction | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;ArcDirection&gt; | 是 | 设置弧形指示器的方向。<br/>默认值：ArcDirection.SIX_CLOCK_DIRECTION，6点钟方向。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcDotIndicator](arkts-arkui-arkui-arcswiper-arcdotindicator-c.md) | 提供弧形圆点指示器属性及功能。 |

<a id="backgroundcolor"></a>
## backgroundColor

```TypeScript
backgroundColor(color: Optional<ResourceColor>): ArcDotIndicator
```

设置弧形指示器被长按时，弧形指示器的颜色。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcDotIndicator-backgroundColor(color: Optional<ResourceColor>): ArcDotIndicator--><!--Device-ArcDotIndicator-backgroundColor(color: Optional<ResourceColor>): ArcDotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;ResourceColor&gt; | 是 | 设置弧形指示器被长按时，弧形指示器的颜色。<br/>默认值：'#FF404040' |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcDotIndicator](arkts-arkui-arkui-arcswiper-arcdotindicator-c.md) | 提供弧形圆点指示器属性及功能。 |

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

ArcDotIndicator的构造函数。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcDotIndicator-constructor()--><!--Device-ArcDotIndicator-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

<a id="itemcolor"></a>
## itemColor

```TypeScript
itemColor(color: Optional<ResourceColor>): ArcDotIndicator
```

设置弧形指示器中，未选中导航点的颜色。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcDotIndicator-itemColor(color: Optional<ResourceColor>): ArcDotIndicator--><!--Device-ArcDotIndicator-itemColor(color: Optional<ResourceColor>): ArcDotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;ResourceColor&gt; | 是 | 设置弧形指示器中，未选中导航点的颜色。<br/>默认值：'#A9FFFFFF' |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcDotIndicator](arkts-arkui-arkui-arcswiper-arcdotindicator-c.md) | 提供弧形圆点指示器属性及功能。 |

<a id="maskcolor"></a>
## maskColor

```TypeScript
maskColor(color: Optional<LinearGradient>): ArcDotIndicator
```

设置弧形指示器的遮罩渐变色。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcDotIndicator-maskColor(color: Optional<LinearGradient>): ArcDotIndicator--><!--Device-ArcDotIndicator-maskColor(color: Optional<LinearGradient>): ArcDotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;LinearGradient&gt; | 是 | 设置弧形指示器的遮罩渐变色。<br/>起始颜色默认值：'#00000000'<br/>结束颜色默认值：'#FF000000' |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcDotIndicator](arkts-arkui-arkui-arcswiper-arcdotindicator-c.md) | 提供弧形圆点指示器属性及功能。 |

<a id="selecteditemcolor"></a>
## selectedItemColor

```TypeScript
selectedItemColor(color: Optional<ResourceColor>): ArcDotIndicator
```

设置弧形指示器中，选中导航点的颜色。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcDotIndicator-selectedItemColor(color: Optional<ResourceColor>): ArcDotIndicator--><!--Device-ArcDotIndicator-selectedItemColor(color: Optional<ResourceColor>): ArcDotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;ResourceColor&gt; | 是 | 设置弧形指示器中，选中导航点的颜色。<br/>默认值：'#FF5EA1FF' |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcDotIndicator](arkts-arkui-arkui-arcswiper-arcdotindicator-c.md) | 提供弧形圆点指示器属性及功能。 |

