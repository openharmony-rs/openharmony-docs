# DragEvent

DragEvent object description

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface DragEvent--><!--Device-unnamed-export declare interface DragEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableInternalDropAnimation

```TypeScript
enableInternalDropAnimation(configuration: string): void
```

Enable the internal drop animation, which is only avaiable for system applications. The animations' configuration need to be provided through the input paramerter, and it is a string in json format. This method can only be called in onDrop, and please do not use custom drop animation after this method, as it will reset the calling result, and use custom drop animation insteadly.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-enableInternalDropAnimation(configuration: string): void--><!--Device-DragEvent-enableInternalDropAnimation(configuration: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configuration | string | 是 | the internal drop animation's configuration. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [190003](../../apis-arkui/errorcode-drag-event.md#190003-当前阶段不允许操作) | Operation not allowed for current phase. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |

## executeFollowHandMorphDropAnimation

```TypeScript
executeFollowHandMorphDropAnimation(onAnimationFinished: VoidCallback, animationOption?: string): void
```

Setup one follow-hand morph drop animation execution callback, which will be triggered by system after the drag framework animation ends. [Note]: 1. This method is effective only when dragAnimationType is FOLLOW_HAND_MORPH. 2. Do not implement animation no-related logic in the callback.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-executeFollowHandMorphDropAnimation(onAnimationFinished: VoidCallback, animationOption?: string): void--><!--Device-DragEvent-executeFollowHandMorphDropAnimation(onAnimationFinished: VoidCallback, animationOption?: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| onAnimationFinished | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) | 是 | the callback triggered after framework animation ends. |
| animationOption | string | 否 | optional animation option payload that will be forwarded by framework. |

## dragAnimationType

```TypeScript
dragAnimationType?: DragAnimationType
```

Sets the drag animation type. This property can only be set during onDragStart, but can be retrieved in any onDragXXX callback.

**类型：** [DragAnimationType](arkts-na-common-draganimationtype-e-sys.md)

**默认值：** DragAnimationType.DEFAULT

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DragEvent-dragAnimationType?: DragAnimationType--><!--Device-DragEvent-dragAnimationType?: DragAnimationType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

