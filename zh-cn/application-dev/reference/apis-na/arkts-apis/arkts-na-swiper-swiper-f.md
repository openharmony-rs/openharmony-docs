# Swiper

## Swiper

```TypeScript
@ComponentBuilder
export declare function Swiper(
  controller?: SwiperController,
  content_?: CustomBuilder
): SwiperAttribute
```

创建滑块视图容器。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Swiper(  controller?: SwiperController,  content_?: CustomBuilder): SwiperAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Swiper(  controller?: SwiperController,  content_?: CustomBuilder): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | [SwiperController](arkts-na-swiper-swipercontroller-c.md) | 否 | 给组件绑定一个控制器，用来控制组件翻页或者预加载指定子节点。 |
| content_ | CustomBuilder | 否 | 子组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SwiperAttribute](arkts-na-swiper-swiperattribute-i.md) |  |


## Swiper

```TypeScript
@Builder
export declare function Swiper(
 style_: CustomBuilderT<SwiperAttribute>,
 content_?: CustomBuilder,
): SwiperAttribute
```

定义Swiper组件

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Swiper( style_: CustomBuilderT<SwiperAttribute>, content_?: CustomBuilder,): SwiperAttribute--><!--Device-unnamed-@Builderexport declare function Swiper( style_: CustomBuilderT<SwiperAttribute>, content_?: CustomBuilder,): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style_ | CustomBuilderT&lt;[SwiperAttribute](arkts-na-swiper-swiperattribute-i.md)&gt; | 是 | swiper属性实例 |
| content_ | CustomBuilder | 否 | 内容区。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SwiperAttribute](arkts-na-swiper-swiperattribute-i.md) |  |

