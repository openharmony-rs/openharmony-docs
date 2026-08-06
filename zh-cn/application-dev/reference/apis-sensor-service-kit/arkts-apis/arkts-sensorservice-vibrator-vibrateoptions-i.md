# VibrateOptions

定义触发设备振动的配置参数，包括振动模式及接口调用的回调函数。开发者调用 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_时，通过 VibrateOptions指定振动模式（短振动或长振动）以及监听振动触发成功、失败和完成的回调函数。传入VibrateOptions后，设备将按指定的mode执行相应振动模式，并在振动触发成功时回调success函数，失败时回调 fail函数，接口调用结束时回调complete函数。 > **说明：** > > 从API version 3开始支持，从API version 8开始废弃。建议使用替代类型[VibrateTime]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** ohos.vibrator/vibrator.VibrateTime

**需要权限：** ohos.permission.VIBRATE

<!--Device-unnamed-export interface VibrateOptions--><!--Device-unnamed-export interface VibrateOptions-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice.Lite

## complete

```TypeScript
complete?: () => void
```

振动接口调用结束时的回调函数。使用场景：开发者需要在振动接口调用完成后（无论成功或失败）执行清理或状态更新操作时，使用此回调。不填写此参数时，接口调用结束将不会有回调通知。使用后效果：无论振动触发成功或失败，系统都会调用此回调函数 ，无返回参数。

**类型：** () =&gt; void

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** ohos.vibrator/vibrator#startVibration

**需要权限：** ohos.permission.VIBRATE

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-VibrateOptions-complete?: () => void--><!--Device-VibrateOptions-complete?: () => void-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

振动触发失败时的回调函数。使用场景：开发者需要处理振动触发失败的情况（如权限未授予、设备不支持振动等）时，通过此回调获取错误信息。不填写此参数时，振动触发失败将不会有回调通知。使用后效果：振动触发失败时，系统将调用此回调函数，传入 错误信息data和错误码code。回调函数签名：(data: string, code: number) => void，其中data为错误信息字符串描述，code为错误码数字，标识具体的错误类型。

**类型：** (data: string, code: number) =&gt; void

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** ohos.vibrator/vibrator#startVibration

**需要权限：** ohos.permission.VIBRATE

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-VibrateOptions-fail?: (data: string, code: number) => void--><!--Device-VibrateOptions-fail?: (data: string, code: number) => void-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice.Lite

## mode

```TypeScript
mode?: 'long' | 'short'
```

振动模式，指定设备振动的持续时间类型。取值范围：'long'（长振动）或'short'（短振动）。默认值：'long'。使用场景：开发者可根据实际需求选择振动模式，例如来电提醒使用'long'以持续提醒用户，按键触觉反馈使用' short'以提供即时反馈。不填写此参数时，默认执行长振动。规格限制：仅适用于Lite Wearable设备。

**类型：** 'long' \| 'short'

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** ohos.vibrator/vibrator.VibrateTime

**需要权限：** ohos.permission.VIBRATE

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-VibrateOptions-mode?: 'long' | 'short'--><!--Device-VibrateOptions-mode?: 'long' | 'short'-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice.Lite

## success

```TypeScript
success: () => void
```

振动触发成功时的回调函数。使用场景：开发者需要监听振动触发成功事件时，通过此回调获取成功通知。使用后效果：振动成功触发后，系统将调用此回调函数，无返回参数。

**类型：** () =&gt; void

**起始版本：** 3

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为3。

**废弃版本：** 8

**替代接口：** ohos.vibrator/vibrator#startVibration

**需要权限：** ohos.permission.VIBRATE

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-VibrateOptions-success: () => void--><!--Device-VibrateOptions-success: () => void-End-->

**系统能力：** SystemCapability.Sensors.MiscDevice.Lite

