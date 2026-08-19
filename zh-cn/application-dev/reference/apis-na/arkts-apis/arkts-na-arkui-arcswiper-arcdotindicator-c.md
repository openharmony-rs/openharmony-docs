# ArcDotIndicator

提供弧形圆点指示器属性及功能。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare class ArcDotIndicator--><!--Device-unnamed-export declare class ArcDotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
```

## arcDirection

```TypeScript
arcDirection(direction: ArcDirection | undefined): ArcDotIndicator
```

设置弧形指示器的方向。未通过该接口设置时，形指示器的方向默认为6点钟方向。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcDotIndicator-arcDirection(direction: ArcDirection | undefined): ArcDotIndicator--><!--Device-ArcDotIndicator-arcDirection(direction: ArcDirection | undefined): ArcDotIndicator-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| direction | [ArcDirection](../../apis-arkui/arkts-apis/arkts-arkui-arkui-arcswiper-arcdirection-e.md) \| undefined | 是 | 设置弧形指示器的方向。<br/>取值为undefined时，弧形指示器的方向为6点钟方向。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcDotIndicator](arkts-na-arkui-arcswiper-arcdotindicator-c.md) | 提供弧形圆点指示器属性及功能。 |

## backgroundColor

```TypeScript
backgroundColor(color: ResourceColor | undefined): ArcDotIndicator
```

设置弧形指示器被长按时，弧形指示器的颜色。未通过该接口设置时，弧形指示器被长按时，弧形指示器的颜色默认为'#FF404040'。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcDotIndicator-backgroundColor(color: ResourceColor | undefined): ArcDotIndicator--><!--Device-ArcDotIndicator-backgroundColor(color: ResourceColor | undefined): ArcDotIndicator-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | ResourceColor \| undefined | 是 | 设置弧形指示器被长按时，弧形指示器的颜色。<br/>取值为undefined时，弧形指示器被长按时，弧形指示器的颜色为'#FF404040' 。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcDotIndicator](arkts-na-arkui-arcswiper-arcdotindicator-c.md) | 提供弧形圆点指示器属性及功能。 |

## constructor

```TypeScript
constructor()
```

ArcDotIndicator的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcDotIndicator-constructor()--><!--Device-ArcDotIndicator-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## itemColor

```TypeScript
itemColor(color: ResourceColor | undefined): ArcDotIndicator
```

设置弧形指示器中，未选中导航点的颜色。未通过该接口设置时，未选中导航点的颜色默认为'#A9FFFFFF'。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcDotIndicator-itemColor(color: ResourceColor | undefined): ArcDotIndicator--><!--Device-ArcDotIndicator-itemColor(color: ResourceColor | undefined): ArcDotIndicator-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | ResourceColor \| undefined | 是 | 设置弧形指示器中，未选中导航点的颜色。<br/>取值为undefined时，未选中导航点的颜色为'#A9FFFFFF'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcDotIndicator](arkts-na-arkui-arcswiper-arcdotindicator-c.md) | 提供弧形圆点指示器属性及功能。 |

## maskColor

```TypeScript
maskColor(color: LinearGradient | undefined): ArcDotIndicator
```

设置弧形指示器的遮罩渐变色。未通过该接口设置时，弧形指示器的遮罩渐变色起始颜色默认为'#00000000'，结束颜色默认为'#FF000000'。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcDotIndicator-maskColor(color: LinearGradient | undefined): ArcDotIndicator--><!--Device-ArcDotIndicator-maskColor(color: LinearGradient | undefined): ArcDotIndicator-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | LinearGradient \| undefined | 是 | 设置弧形指示器的遮罩渐变色。<br/>取值为undefined时，弧形指示器的遮罩渐变色起始颜色为'#00000000'，结束颜色为'# FF000000'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcDotIndicator](arkts-na-arkui-arcswiper-arcdotindicator-c.md) | 提供弧形圆点指示器属性及功能。 |

## selectedItemColor

```TypeScript
selectedItemColor(color: ResourceColor | undefined): ArcDotIndicator
```

设置弧形指示器中，选中导航点的颜色。未通过该接口设置时，选中导航点的颜色默认为'#FF5EA1FF'。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcDotIndicator-selectedItemColor(color: ResourceColor | undefined): ArcDotIndicator--><!--Device-ArcDotIndicator-selectedItemColor(color: ResourceColor | undefined): ArcDotIndicator-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | ResourceColor \| undefined | 是 | 设置弧形指示器中，选中导航点的颜色。<br/>取值为undefined时，选中导航点的颜色为'#FF5EA1FF'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ArcDotIndicator](arkts-na-arkui-arcswiper-arcdotindicator-c.md) | 提供弧形圆点指示器属性及功能。 |

