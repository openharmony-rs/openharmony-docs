# @ohos.graphics.displaySync

可变帧率支持让开发者以指定帧率来运行UI业务，一般用于开发者自绘制UI，并且对于帧率有特定诉求的场景。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [create](arkts-arkgraphics2d-create-f.md#create-1) | 创建DisplaySync对象，通过此对象设置UI自绘制内容帧率。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DisplaySync](arkts-arkgraphics2d-displaysync-i.md) | 帧率和回调函数设置实例。用于帧率设置和回调函数的注册，以及启动和停止回调函数的调用。下列API示例中都需先使用displaySync.create()方法获取到DisplaySync实例，再通过此实例调用对应方法。 |
| [IntervalInfo](arkts-arkgraphics2d-intervalinfo-i.md) | 开发者可以从订阅函数中获取帧绘制的时间戳信息，包含当前帧到达的时间timestamp和下一帧预期到达的时间targetTimestamp。 |

