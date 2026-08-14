# DisplaySync

期望帧率和回调函数设置实例。用于设置期望帧率范围、注册帧回调函数，以及启动和停止帧回调。 下列API示例中都需先使用displaySync.create()方法获取到DisplaySync实例，再通过此实例调用对应方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-displaySync-interface DisplaySync--><!--Device-displaySync-interface DisplaySync-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offFrame

```TypeScript
offFrame(callback?: Callback<IntervalInfo>): void
```

取消订阅每一帧的变化。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DisplaySync-offFrame(callback?: Callback<IntervalInfo>): void--><!--Device-DisplaySync-offFrame(callback?: Callback<IntervalInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[IntervalInfo](arkts-arkgraphics2d-displaysync-intervalinfo-i.md)&gt; | 否 | 订阅函数，参数不填时，默认取消全部订阅函数。 |

## 示例

```TypeScript
let callback = (frameInfo: displaySync.IntervalInfo) => {
    console.info("DisplaySync", 'TimeStamp:' + frameInfo.timestamp + ' TargetTimeStamp: ' + frameInfo.targetTimestamp);
}

backDisplaySync?.onFrame(callback)

// 取消订阅函数
backDisplaySync?.offFrame(callback)
```

## off_frame

```TypeScript
off(type: 'frame', callback?: Callback<IntervalInfo>): void
```

取消订阅每一帧的变化。与on('frame')方法配对使用。取消成功后，将不再触发回调函数。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-DisplaySync-off(type: 'frame', callback?: Callback<IntervalInfo>): void--><!--Device-DisplaySync-off(type: 'frame', callback?: Callback<IntervalInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frame' | 是 | 设置回调的类型（只能是'frame'类型）。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[IntervalInfo](arkts-arkgraphics2d-displaysync-intervalinfo-i.md)&gt; | 否 | 传入调用on('frame')时注册的回调函数，用于取消订阅该回调函数。必须在已通过on('frame')注册回调后使用。 |

## 示例

```TypeScript
// 定义回调函数
let callback = (frameInfo: displaySync.IntervalInfo) => {
    console.info("DisplaySync", 'TimeStamp:' + frameInfo.timestamp + ' TargetTimeStamp: ' + frameInfo.targetTimestamp);
}

// 注册回调函数
backDisplaySync?.on("frame", callback)

// 取消回调函数
backDisplaySync?.off("frame", callback)
```

## onFrame

```TypeScript
onFrame(callback: Callback<IntervalInfo>): void
```

订阅每一帧的变化。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DisplaySync-onFrame(callback: Callback<IntervalInfo>): void--><!--Device-DisplaySync-onFrame(callback: Callback<IntervalInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[IntervalInfo](arkts-arkgraphics2d-displaysync-intervalinfo-i.md)&gt; | 是 | 订阅函数。 |

## 示例

```TypeScript
let callback = (frameInfo: displaySync.IntervalInfo) => {
    console.info("DisplaySync", 'TimeStamp:' + frameInfo.timestamp + ' TargetTimeStamp: ' + frameInfo.targetTimestamp);
}

// 注册订阅函数
backDisplaySync?.onFrame(callback)
```

## on_frame

```TypeScript
on(type: 'frame', callback: Callback<IntervalInfo>): void
```

订阅每一帧的变化。注册回调函数后，还需调用start方法启动DisplaySync，系统才会在每一帧触发该回调。和off('frame')方法配对使用，用于取消注册回调函数。 字段需为非负整数，取值范围为[0, 设备最大帧率]，且满足min <= expected <= max。超出有效范围时参数校验失败。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-DisplaySync-on(type: 'frame', callback: Callback<IntervalInfo>): void--><!--Device-DisplaySync-on(type: 'frame', callback: Callback<IntervalInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frame' | 是 | 设置回调的类型（只能是'frame'类型）。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[IntervalInfo](arkts-arkgraphics2d-displaysync-intervalinfo-i.md)&gt; | 是 | 订阅帧变化的回调函数。IntervalInfo包含timestamp（当前帧到达时间）和targetTimestamp（下一帧预期到达时间）两个属性，单位均为纳秒。 |

## 示例

```TypeScript
// 定义回调函数
let callback = (frameInfo: displaySync.IntervalInfo) => {
    console.info("DisplaySync", 'TimeStamp:' + frameInfo.timestamp + ' TargetTimeStamp: ' + frameInfo.targetTimestamp);
}

// 注册回调函数
backDisplaySync?.on("frame", callback)
```

## setExpectedFrameRateRange

```TypeScript
setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange) : void
```

设置期望的帧率范围。设置的期望帧率范围将作为系统调度的参考，系统会尽量在此范围内调整绘制帧率。 未调用该方法或传入ExpectedFrameRateRange(0, 0, 0)时将跟随应用当前运行的帧率。建议在调用start前设置，以便立即生效；调用start之后设置也可生效但可能存在延迟。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DisplaySync-setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange) : void--><!--Device-DisplaySync-setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange) : void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rateRange | [ExpectedFrameRateRange](../../apis-na/arkts-apis/arkts-na-common-expectedframeraterange-i.md) | 是 | 设置DisplaySync期望的帧率范围，包含expected、min和max三个字段，单位为帧/秒（fps）， 字段需为非负整数，取值范围为[0, 设备最大帧率]，且满足min <= expected <= max。超出有效范围时会抛出401错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. or check if ExpectedFrameRateRange is valid. |

## 示例

```TypeScript
// 定义期望帧率范围
let range: ExpectedFrameRateRange = {
  expected: 10, // 期望帧率
  min: 0, // 最小帧率
  max: 120 // 最大帧率
};

// 设置DisplaySync期望帧率范围
backDisplaySync?.setExpectedFrameRateRange(range)

// 生效期望帧率范围
backDisplaySync?.start()
```

## start

```TypeScript
start(): void
```

使通过setExpectedFrameRateRange设置的期望帧率范围生效；如果通过on('frame')注册了回调函数，则开始请求VSync信号，触发已注册的回调，每帧执行一次。和stop方法配对使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DisplaySync-start(): void--><!--Device-DisplaySync-start(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 示例

```TypeScript
// 定义期望帧率范围
let range: ExpectedFrameRateRange = {
  expected: 10, // 期望帧率
  min: 0, // 最小帧率
  max: 120 // 最大帧率
};
// 设置DisplaySync期望帧率范围
backDisplaySync?.setExpectedFrameRateRange(range)

// 定义回调函数
let callback = (frameInfo: displaySync.IntervalInfo) => {
    console.info("DisplaySync", 'TimeStamp:' + frameInfo.timestamp + ' TargetTimeStamp: ' + frameInfo.targetTimestamp);
}

// 注册回调函数
backDisplaySync?.on("frame", callback)

// 生效期望帧率范围并且开始每帧回调
backDisplaySync?.start()
```

```TypeScript
import { displaySync } from '@kit.ArkGraphics2D';
import { UIContext } from '@kit.ArkUI';

// xxx.ets
@Entry
@Component
struct Index {
  // 创建DisplaySync实例
  backDisplaySync: displaySync.DisplaySync = displaySync.create();

  aboutToAppear() {
    // 获取UIContext实例
    let uiContext: UIContext = this.getUIContext();
    // 在当前UI上下文中执行DisplaySync的start接口
    uiContext?.runScopedTask(() => {
      this.backDisplaySync?.start();
    })
  }

  build() {
    // ...
  }
}
```

## stop

```TypeScript
stop(): void
```

关闭期望帧率范围并且停止每帧回调。需在调用start后使用，停止后DisplaySync的配置（如期望帧率范围、回调函数）仍然保留，可随时通过start重新启动。 stop方法会解除DisplaySync与UI上下文和窗口的关联，通常无需特定的UI上下文。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-DisplaySync-stop(): void--><!--Device-DisplaySync-stop(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 示例

```TypeScript
// 定义期望帧率范围
let range: ExpectedFrameRateRange = {
  expected: 10, // 期望帧率
  min: 0, // 最小帧率
  max: 120 // 最大帧率
};

// 设置DisplaySync期望帧率范围
backDisplaySync?.setExpectedFrameRateRange(range)

// 定义回调函数
let callback = (frameInfo: displaySync.IntervalInfo) => {
    console.info("DisplaySync", 'TimeStamp:' + frameInfo.timestamp + ' TargetTimeStamp: ' + frameInfo.targetTimestamp);
}

// 注册回调函数
backDisplaySync?.on("frame", callback)

// 生效期望帧率范围并且开始每帧回调
backDisplaySync?.start()

// ...

// 停止生效期望帧率范围并且停止每帧回调
backDisplaySync?.stop()
```

