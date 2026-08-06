# VideoAttribute

用于播放视频文件并控制其播放状态的组件。

**继承/实现关系：** VideoAttribute extends [CommonMethod](../../../apis-na/arkts-apis/arkts-na-component/common-commonmethod-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface VideoAttribute extends CommonMethod--><!--Device-unnamed-export declare interface VideoAttribute extends CommonMethod-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## surfaceBackgroundColor

```TypeScript
default surfaceBackgroundColor(color: ColorMetrics | undefined): this
```

Set background color of the surface holden by Video(only support Color.Black and Color.Transparent).

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VideoAttribute-default surfaceBackgroundColor(color: ColorMetrics | undefined): this--><!--Device-VideoAttribute-default surfaceBackgroundColor(color: ColorMetrics | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | The surface background color.Default value is Color.Black, \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_INLINE\_\_\_ESCAPED\_UNDERSCORE\_\_\_CODE\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ means setting to the default value. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

