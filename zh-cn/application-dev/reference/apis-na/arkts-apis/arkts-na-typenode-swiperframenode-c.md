# SwiperFrameNode

定义Swiper类型的FrameNode。

**继承/实现关系：** SwiperFrameNode extends TypedFrameNode<SwiperAttribute>

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-typeNode-abstract class SwiperFrameNode--><!--Device-typeNode-abstract class SwiperFrameNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## initialize

```TypeScript
abstract initialize(controller?: SwiperController): SwiperAttribute
```

初始化Swiper类型的FrameNode。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperFrameNode-abstract initialize(controller?: SwiperController): SwiperAttribute--><!--Device-SwiperFrameNode-abstract initialize(controller?: SwiperController): SwiperAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | SwiperController | 否 | swiper的控制器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SwiperAttribute |  |

