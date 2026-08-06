# ProgressMask

Implements a ProgressMask object to set the progress, maximum value, and color of the mask.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class ProgressMask--><!--Device-unnamed-export declare class ProgressMask-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: double, total: double, color: ResourceColor)
```

constructor.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressMask-constructor(value: double, total: double, color: ResourceColor)--><!--Device-ProgressMask-constructor(value: double, total: double, color: ResourceColor)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double | 是 | Current value of the progress mask. Value range: [0.0, +∞). |
| total | double | 是 | Maximum value of the progress mask. Value range: [0.0, +∞). |
| color | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Color of the progress mask. |

## enableBreathingAnimation

```TypeScript
enableBreathingAnimation(value: boolean): void
```

Enable the breathe animation of mask.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressMask-enableBreathingAnimation(value: boolean): void--><!--Device-ProgressMask-enableBreathingAnimation(value: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 |  |

## updateColor

```TypeScript
updateColor(value: ResourceColor): void
```

Update the color of the mask.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressMask-updateColor(value: ResourceColor): void--><!--Device-ProgressMask-updateColor(value: ResourceColor): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Color of the progress mask. |

## updateProgress

```TypeScript
updateProgress(value: double): void
```

Updates the progress value of the progress mask.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressMask-updateProgress(value: double): void--><!--Device-ProgressMask-updateProgress(value: double): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double | 是 | Current value of the progress mask. |

