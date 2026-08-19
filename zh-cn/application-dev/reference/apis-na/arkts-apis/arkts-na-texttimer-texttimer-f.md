# TextTimer

## TextTimer

```TypeScript
@ComponentBuilder
export declare function TextTimer(
    options?: TextTimerOptions
): TextTimerAttribute
```

创建文本计时器组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function TextTimer(    options?: TextTimerOptions): TextTimerAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function TextTimer(    options?: TextTimerOptions): TextTimerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TextTimerOptions](arkts-na-texttimer-texttimeroptions-i.md) | 否 | 通过文本显示计时信息并控制其计时器状态的组件参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TextTimerAttribute |  |


## TextTimer

```TypeScript
@Builder
export declare function TextTimer(
    style: CustomBuilderT<TextTimerAttribute>,
): TextTimerAttribute
```

定义TextTimer组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function TextTimer(    style: CustomBuilderT<TextTimerAttribute>,): TextTimerAttribute--><!--Device-unnamed-@Builderexport declare function TextTimer(    style: CustomBuilderT<TextTimerAttribute>,): TextTimerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;TextTimerAttribute&gt; | 是 | TextTimer属性的实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TextTimerAttribute |  |

