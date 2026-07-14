# DisplaySync

帧率和回调函数设置实例。用于帧率设置和回调函数的注册，以及启动和停止回调函数的调用。
下列API示例中都需先使用displaySync.create()方法获取到DisplaySync实例，再通过此实例调用对应方法。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## off('frame')

```TypeScript
off(type: 'frame', callback?: Callback<IntervalInfo>): void
```

取消订阅每一帧的变化。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frame' | 是 | 设置注册回调的类型（只能是'frame'类型）。 |
| callback | Callback&lt;IntervalInfo&gt; | 否 | 订阅函数，参数不填时，默认取消全部订阅函数。 |

**示例：**

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

## on('frame')

```TypeScript
on(type: 'frame', callback: Callback<IntervalInfo>): void
```

订阅每一帧的变化。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frame' | 是 | 设置注册回调的类型（只能是'frame'类型）。 |
| callback | Callback&lt;IntervalInfo&gt; | 是 | 订阅函数。 |

**示例：**

```TypeScript
// 定义回调函数
let callback = (frameInfo: displaySync.IntervalInfo) => {
    console.info("DisplaySync", 'TimeStamp:' + frameInfo.timestamp + ' TargetTimeStamp: ' + frameInfo.targetTimestamp);
}

// 注册回调函数
backDisplaySync?.on("frame", callback)

// 生效回调函数
backDisplaySync?.start()

```

## setExpectedFrameRateRange

```TypeScript
setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange) : void
```

设置期望的帧率范围。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rateRange | ExpectedFrameRateRange | 是 | 设置DisplaySync期望的帧率。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed.or check if ExpectedFrameRateRange is valid. |

**示例：**

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

开始每帧回调。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

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

停止每帧回调。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

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

