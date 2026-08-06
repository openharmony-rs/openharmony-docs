# SliderTriggerChangeCallback

```TypeScript
export type SliderTriggerChangeCallback = (value: double, mode: SliderChangeMode) => void
```

定义SliderConfiguration中使用的回调类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type SliderTriggerChangeCallback = (value: double, mode: SliderChangeMode) => void--><!--Device-unnamed-export type SliderTriggerChangeCallback = (value: double, mode: SliderChangeMode) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double | 是 | 设置当前的进度值。\_\_\_HTML\_TAG\_USD\_2\_\_\_取值范围：[[min]\_\_\_JSDOC\_LINK\_USD\_0\_\_\_-[max]\_\_\_JSDOC\_LINK\_USD\_1\_\_\_]  |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 设置事件触发的相关状态值。  |

