# @ohos.graphics.displaySync

可变帧率支持让开发者以指定帧率来运行UI业务，一般用于开发者自绘制UI，并且对于帧率有特定需求的场景，系统会根据设置的期望帧率、最小帧率和最大帧率来调整绘制频率，以满足不同场景的需求。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace displaySync--><!--Device-unnamed-declare namespace displaySync-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [create](arkts-arkgraphics2d-displaysync-create-f.md#create) | 创建DisplaySync对象，通过此对象设置UI自绘制内容帧率。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DisplaySync](arkts-arkgraphics2d-displaysync-displaysync-i.md) | 期望帧率和回调函数设置实例。用于设置期望帧率范围、注册帧回调函数，以及启动和停止帧回调。 下列API示例中都需先使用displaySync.create()方法获取到DisplaySync实例，再通过此实例调用对应方法。 |
| [IntervalInfo](arkts-arkgraphics2d-displaysync-intervalinfo-i.md) | 开发者可以从回调函数中获取帧绘制的时间戳信息，包含当前帧到达的时间timestamp和下一帧预期到达的时间targetTimestamp。 |

