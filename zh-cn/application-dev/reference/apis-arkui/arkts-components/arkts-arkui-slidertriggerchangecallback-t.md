# SliderTriggerChangeCallback

```TypeScript
declare type SliderTriggerChangeCallback = (value: number, mode: SliderChangeMode) => void
```

定义SliderConfiguration中使用的回调类型。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type SliderTriggerChangeCallback = (value: number, mode: SliderChangeMode) => void--><!--Device-unnamed-declare type SliderTriggerChangeCallback = (value: number, mode: SliderChangeMode) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 设置当前进度值。\_\_\_HTML\_TAG\_USD\_2\_\_\_取值范围：[[min]\_\_\_JSDOC\_LINK\_USD\_0\_\_\_-[max]\_\_\_JSDOC\_LINK\_USD\_1\_\_\_]  |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 设置事件触发的相关状态值。  |

