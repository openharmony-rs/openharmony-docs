# Video

## Video

```TypeScript
@ComponentBuilder
export declare function Video(
    value: VideoOptions
): VideoAttribute
```

用于播放视频文件并控制其播放状态的组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Video(    value: VideoOptions): VideoAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Video(    value: VideoOptions): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [VideoOptions](arkts-arkui-video-videooptions-i.md) | 是 | 视频信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [VideoAttribute](arkts-arkui-video-videoattribute-i.md) | The attribute of the Video. |


## Video

```TypeScript
@Builder
export declare function Video(
    style: CustomBuilderT<VideoAttribute>
): VideoAttribute
```

Defines Video Component.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Video(    style: CustomBuilderT<VideoAttribute>): VideoAttribute--><!--Device-unnamed-@Builderexport declare function Video(    style: CustomBuilderT<VideoAttribute>): VideoAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;[VideoAttribute](arkts-arkui-video-videoattribute-i.md)&gt; | 是 | the callback to set up component's attributes. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [VideoAttribute](arkts-arkui-video-videoattribute-i.md) |  |

