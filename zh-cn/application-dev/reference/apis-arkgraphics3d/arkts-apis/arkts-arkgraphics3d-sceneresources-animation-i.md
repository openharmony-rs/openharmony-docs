# Animation

动画资源.

**继承/实现关系：** Animation extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**起始版本：** 12

<!--Device-unnamed-export interface Animation extends SceneResource--><!--Device-unnamed-export interface Animation extends SceneResource-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## finish

```TypeScript
finish(): void
```

结束动画并将位置设置到结尾.

**起始版本：** 12

<!--Device-Animation-finish(): void--><!--Device-Animation-finish(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## onFinished

```TypeScript
onFinished(callback: Callback<void>): void
```

注册动画完成时的回调.

**起始版本：** 12

<!--Device-Animation-onFinished(callback: Callback<void>): void--><!--Device-Animation-onFinished(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 是 | 动画完成时调用的回调 |

## onStarted

```TypeScript
onStarted(callback: Callback<void>): void
```

注册动画开始时的回调.

**起始版本：** 12

<!--Device-Animation-onStarted(callback: Callback<void>): void--><!--Device-Animation-onStarted(callback: Callback<void>): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 是 | 动画开始时调用的回调 |

## pause

```TypeScript
pause(): void
```

暂停动画.

**起始版本：** 12

<!--Device-Animation-pause(): void--><!--Device-Animation-pause(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## restart

```TypeScript
restart(): void
```

重新启动动画.

**起始版本：** 12

<!--Device-Animation-restart(): void--><!--Device-Animation-restart(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## seek

```TypeScript
seek(position: number): void
```

将动画跳转到指定位置.

**起始版本：** 12

<!--Device-Animation-seek(position: double): void--><!--Device-Animation-seek(position: double): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | number | 是 | 跳转到0~1之间的位置 |

## start

```TypeScript
start(): void
```

开始动画.

**起始版本：** 12

<!--Device-Animation-start(): void--><!--Device-Animation-start(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## stop

```TypeScript
stop(): void
```

停止动画并将位置设置到开头.

**起始版本：** 12

<!--Device-Animation-stop(): void--><!--Device-Animation-stop(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## duration

```TypeScript
readonly duration: number
```

动画持续时间, 单位为秒.

**类型：** number

**起始版本：** 12

<!--Device-Animation-readonly duration: double--><!--Device-Animation-readonly duration: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## enabled

```TypeScript
enabled: boolean
```

动画是否启用.

**类型：** boolean

**起始版本：** 12

<!--Device-Animation-enabled: boolean--><!--Device-Animation-enabled: boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## progress

```TypeScript
readonly progress: number
```

动画在0~1之间的进度.

**类型：** number

**起始版本：** 12

<!--Device-Animation-readonly progress: double--><!--Device-Animation-readonly progress: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## running

```TypeScript
readonly running: boolean
```

动画是否正在运行.

**类型：** boolean

**起始版本：** 12

<!--Device-Animation-readonly running: boolean--><!--Device-Animation-readonly running: boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## speed

```TypeScript
speed?: number
```

动画速度因子负值使用给定速度因子反向播放动画

**类型：** number

**起始版本：** 20

<!--Device-Animation-speed?: double--><!--Device-Animation-speed?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

