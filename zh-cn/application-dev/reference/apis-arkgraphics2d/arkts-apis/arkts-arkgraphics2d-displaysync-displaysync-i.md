# DisplaySync

帧率和回调函数设置实例。用于帧率设置和回调函数的注册，以及启动和停止回调函数的调用。 下列API示例中都需先使用displaySync.create()方法获取到DisplaySync实例，再通过此实例调用对应方法。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-displaySync-interface DisplaySync--><!--Device-displaySync-interface DisplaySync-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## off('frame')

```TypeScript
off(type: 'frame', callback?: Callback<IntervalInfo>): void
```

取消订阅每一帧的变化。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-DisplaySync-off(type: 'frame', callback?: Callback<IntervalInfo>): void--><!--Device-DisplaySync-off(type: 'frame', callback?: Callback<IntervalInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frame' | 是 | 设置注册回调的类型（只能是'frame'类型）。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;IntervalInfo&gt; | 否 | 订阅函数，参数不填时，默认取消全部订阅函数。 |

**示例：**

```TypeScript
let callback = (frameInfo: displaySync.IntervalInfo) => {
    console.info("DisplaySync", 'TimeStamp:' + frameInfo.timestamp + ' TargetTimeStamp: ' + frameInfo.targetTimestamp);
}

backDisplaySync?.on("frame", callback)

// 取消订阅函数
backDisplaySync?.off("frame", callback)
```

## offFrame

```TypeScript
offFrame(callback?: Callback<IntervalInfo>): void
```

取消订阅每一帧的变化。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-DisplaySync-offFrame(callback?: Callback<IntervalInfo>): void--><!--Device-DisplaySync-offFrame(callback?: Callback<IntervalInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;IntervalInfo&gt; | 否 | 订阅函数，参数不填时，默认取消全部订阅函数。 |

**示例：**

```TypeScript
let callback = (frameInfo: displaySync.IntervalInfo) => {
    console.info("DisplaySync", 'TimeStamp:' + frameInfo.timestamp + ' TargetTimeStamp: ' + frameInfo.targetTimestamp);
}

backDisplaySync?.onFrame(callback)

// 取消订阅函数
backDisplaySync?.offFrame(callback)
```

## on('frame')

```TypeScript
on(type: 'frame', callback: Callback<IntervalInfo>): void
```

订阅每一帧的变化。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

<!--Device-DisplaySync-on(type: 'frame', callback: Callback<IntervalInfo>): void--><!--Device-DisplaySync-on(type: 'frame', callback: Callback<IntervalInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frame' | 是 | 设置注册回调的类型（只能是'frame'类型）。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;IntervalInfo&gt; | 是 | 订阅函数。 |

**示例：**

```TypeScript
let callback = (frameInfo: displaySync.IntervalInfo) => {
    console.info("DisplaySync", 'TimeStamp:' + frameInfo.timestamp + ' TargetTimeStamp: ' + frameInfo.targetTimestamp);
}

// 注册订阅函数
backDisplaySync?.on("frame", callback)
```

## onFrame

```TypeScript
onFrame(callback: Callback<IntervalInfo>): void
```

订阅每一帧的变化。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-DisplaySync-onFrame(callback: Callback<IntervalInfo>): void--><!--Device-DisplaySync-onFrame(callback: Callback<IntervalInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;IntervalInfo&gt; | 是 | 订阅函数。 |

**示例：**

```TypeScript
let callback = (frameInfo: displaySync.IntervalInfo) => {
    console.info("DisplaySync", 'TimeStamp:' + frameInfo.timestamp + ' TargetTimeStamp: ' + frameInfo.targetTimestamp);
}

// 注册订阅函数
backDisplaySync?.onFrame(callback)
```

## setExpectedFrameRateRange

```TypeScript
setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange) : void
```

设置期望的帧率范围。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-DisplaySync-setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange) : void--><!--Device-DisplaySync-setExpectedFrameRateRange(rateRange: ExpectedFrameRateRange) : void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rateRange | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 设置DisplaySync期望的帧率。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 2. Incorrect parameters types.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 3. Parameter verification failed.or check if ExpectedFrameRateRange is valid. |

**示例：**

```TypeScript
let range : ExpectedFrameRateRange = {
  expected: 10,
  min:0,
  max:120
};

// 设置DisplaySync期望的帧率
backDisplaySync?.setExpectedFrameRateRange(range)
```

## start

```TypeScript
start(): void
```

开始每帧回调。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-DisplaySync-start(): void--><!--Device-DisplaySync-start(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```TypeScript
let range : ExpectedFrameRateRange = {
  expected: 10,
  min:0,
  max:120
};

backDisplaySync?.setExpectedFrameRateRange(range)

let callback = (frameInfo: displaySync.IntervalInfo) => {
    console.info("DisplaySync", 'TimeStamp:' + frameInfo.timestamp + ' TargetTimeStamp: ' + frameInfo.targetTimestamp);
}

backDisplaySync?.on("frame", callback)

// 开始每帧回调
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

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-DisplaySync-stop(): void--><!--Device-DisplaySync-stop(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```TypeScript
let range : ExpectedFrameRateRange = {
  expected: 10,
  min:0,
  max:120
};

backDisplaySync?.setExpectedFrameRateRange(range)

let callback = (frameInfo: displaySync.IntervalInfo) => {
    console.info("DisplaySync", 'TimeStamp:' + frameInfo.timestamp + ' TargetTimeStamp: ' + frameInfo.targetTimestamp);
}

backDisplaySync?.on("frame", callback)

backDisplaySync?.start()

// ...

// 停止每帧回调
backDisplaySync?.stop()
```

