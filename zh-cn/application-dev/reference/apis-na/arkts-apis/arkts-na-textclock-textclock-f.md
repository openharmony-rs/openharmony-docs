# TextClock

## TextClock

```TypeScript
@ComponentBuilder
export declare function TextClock(
    options?: TextClockOptions
): TextClockAttribute
```

创建文本时钟组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function TextClock(    options?: TextClockOptions): TextClockAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function TextClock(    options?: TextClockOptions): TextClockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TextClockOptions](arkts-na-textclock-textclockoptions-i.md) | 否 | 通过文本显示当前系统时间的组件参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TextClockAttribute |  |


## TextClock

```TypeScript
@Builder
export declare function TextClock(
    style: CustomBuilderT<TextClockAttribute>,
): TextClockAttribute
```

定义TextClock组件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function TextClock(    style: CustomBuilderT<TextClockAttribute>,): TextClockAttribute--><!--Device-unnamed-@Builderexport declare function TextClock(    style: CustomBuilderT<TextClockAttribute>,): TextClockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;TextClockAttribute&gt; | 是 | TextClock属性的实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TextClockAttribute |  |

