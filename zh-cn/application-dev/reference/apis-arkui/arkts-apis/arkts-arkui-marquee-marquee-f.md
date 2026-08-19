# Marquee

## Marquee

```TypeScript
@ComponentBuilder
export declare function Marquee(
    options: MarqueeOptions
): MarqueeAttribute
```

创建跑马灯组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Marquee(    options: MarqueeOptions): MarqueeAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Marquee(    options: MarqueeOptions): MarqueeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [MarqueeOptions](arkts-arkui-marquee-marqueeoptions-i.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| MarqueeAttribute |  |


## Marquee

```TypeScript
@Builder
export declare function Marquee(
    style: CustomBuilderT<MarqueeAttribute>,
): MarqueeAttribute
```

定义Marquee组件。

**起始版本：** 26.1.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.1.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Marquee(    style: CustomBuilderT<MarqueeAttribute>,): MarqueeAttribute--><!--Device-unnamed-@Builderexport declare function Marquee(    style: CustomBuilderT<MarqueeAttribute>,): MarqueeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;MarqueeAttribute&gt; | 是 | Marquee属性实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| MarqueeAttribute |  |

